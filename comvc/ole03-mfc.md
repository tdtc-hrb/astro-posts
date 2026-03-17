---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The OLE clipboard"
description: "Using Alternative Storage Media"
date: 2025-12-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Remember, a data object is a COM object that implements the IDataObject interface.

![Transferring data through the OLE clipboard.](https://github.com/tdtc-hrb/csdn/raw/master/images/figure19.1_mfc2.png)

1. The data provider uses OleSetClipboard to place a data object on the clipboard.
2. The data consumer uses OleGetClipboard to retrieve the IDataObject interface pointer.
3. The data consumer requests data from the data object.
4. The data object providers data to the data consumer.

### provider and consumer
MFC’s OLE clipboard support is concentrated in two classes.
- [COleDataSource](https://tdtc-hrb.github.io/com-vc/posts/ole04-mfc)
- [COleDataObject](https://tdtc-hrb.github.io/com-vc/posts/ole05-mfc)

The first, COleDataSource, models the provider side of clipboard operations.    
The second, COleDataObject, models the consumer side.

#### OLE support
Add the following to the InitInstance() in <ProjName.cpp>:
```
    // Initialize OLE libraries
    if (!AfxOleInit())
    {
        AfxMessageBox(_T("OLE initialization failed.  Make sure that the OLE libraries are the correct version.")); // IDP_OLE_INIT_FAILED
        return FALSE;
    }
```

Resolving the "CoInitialize has not been called".

#### get data and set data
Two structures play key roles in the operation of SetData and GetData:
- FORMATETC
- STGMEDIUM

### example
CFile provider:
- TYMED_HGLOBAL
- TYMED_FILE
- TYMED_MFPICT
- TYMED_ISTREAM

#### provider side
```
    USES_CONVERSION;    // A2W usage

    char szText[] = "Hello, world";

    TCHAR szPath[MAX_PATH], szFileName[MAX_PATH];
    ::GetTempPath(sizeof(szPath) / sizeof(TCHAR), szPath);
    ::GetTempFileName(szPath, _T("tmp"), 0, szFileName);
    CFile file;
    if (file.Open(szFileName, CFile::modeCreate | CFile::modeWrite)) {
        file.Write(szText, ::lstrlen(A2W(szText)) + 1);
        file.Close();
        LPWSTR pwszFileName = (LPWSTR) ::CoTaskMemAlloc(MAX_PATH * sizeof(WCHAR));
#ifdef UNICODE
        ::lstrcpy(pwszFileName, szFileName);
#else
        ::MultiByteToWideChar(CP_ACP, MB_PRECOMPOSED, szFileName, -1, pwszFileName, MAX_PATH);
#endif

        FORMATETC fe = {
            CF_TEXT, NULL, DVASPECT_CONTENT, -1, TYMED_FILE
        };

        STGMEDIUM stgm;
        stgm.tymed = TYMED_FILE;
        stgm.lpszFileName = pwszFileName;
        stgm.pUnkForRelease = NULL;

        COleDataSource* pods = new COleDataSource;
        pods->CacheData(CF_TEXT, &stgm, &fe);
        pods->SetClipboard();
    }
```
#### consumer side
```
    char szText[BUFLEN];
    STGMEDIUM stgm;

    FORMATETC fe = {
        CF_TEXT, NULL, DVASPECT_CONTENT, -1, TYMED_FILE
    };

    COleDataObject odo;
    odo.AttachClipboard();

    if (odo.GetData(CF_TEXT, &stgm, &fe) && stgm.tymed == TYMED_FILE) {
        TCHAR szFileName[MAX_PATH];

#ifdef UNICODE
        ::lstrcpy(szFileName, stgm.lpszFileName);
#else
        ::WideCharToMultiByte(CP_ACP, 0, stgm.lpszFileName,
            -1, szFileName, sizeof(szFileName) / sizeof(TCHAR), NULL, NULL);
#endif

        CFile file;
        if (file.Open(szFileName, CFile::modeRead)) {
            ULONGLONG ulSize = file.GetLength();
            if (ulSize < BUFLEN)
                file.Read(szText, (UINT)ulSize);
            file.Close();
        }
        ::ReleaseStgMedium(&stgm);
    }
```
Macro define:
```
#define BUFLEN 4096
```

## Ref
- [19.2. The OLE Clipboard](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
