---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Windows Controls: The Rich Edit Control"
description: "Use Rich Edit 2.0 Control to store files"
date: 2025-11-01
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
First, set up EDITSTREAM, then StreamOut.

Two Rich Edit 2.0 controls: RICHEDIT2LOG2 and RICHEDIT2LOG1; used to store plain text and hexadecimal text.

### [EDITSTREAM structure (richedit.h)](https://learn.microsoft.com/en-us/windows/win32/api/richedit/ns-richedit-editstream)
```
typedef struct _editstream {
  DWORD_PTR          dwCookie;
  DWORD              dwError;
  EDITSTREAMCALLBACK pfnCallback;
} EDITSTREAM;
```
- dwCookie    
Specifies an application-defined value that the rich edit control passes to the EditStreamCallback callback function specified by the pfnCallback member.
- pfnCallback    
Pointer to an EditStreamCallback function, which is an application-defined function that the control calls to transfer data. 
The control calls the callback function repeatedly, transferring a portion of the data with each call.

#### [callback - es](https://learn.microsoft.com/en-us/windows/win32/api/richedit/nc-richedit-editstreamcallback)
```
EDITSTREAMCALLBACK Editstreamcallback;

DWORD Editstreamcallback(
  [in] DWORD_PTR dwCookie,
  [in] LPBYTE pbBuff,
  [in] LONG cb,
  [in] LONG *pcb
)
{...}
```

### [StreamOut](https://learn.microsoft.com/en-us/cpp/mfc/reference/cricheditctrl-class?view=msvc-170#streamout)
```
long StreamOut(
    int nFormat,
    EDITSTREAM& es);
```
- nFormat    
Flags specifying the output data formats. See the Remarks section for more information.
- es    
EDITSTREAM structure specifying the output stream. See the Remarks section for more information.

#### [example](https://learn.microsoft.com/en-us/cpp/mfc/reference/cricheditctrl-class?view=msvc-170#example-47)
- MyStreamOutCallback
```
// My callback procedure that writes the rich edit control contents
// to a file.
static DWORD CALLBACK 
MyStreamOutCallback(DWORD dwCookie, LPBYTE pbBuff, LONG cb, LONG *pcb)
{
   CFile* pFile = (CFile*) dwCookie;

   pFile->Write(pbBuff, cb);
   *pcb = cb;

   return 0;
}
```
- StreamOut
```
// The example code.

// The file to store the contents of the rich edit control.
CFile cFile(TEXT("My_RichEdit_OutFile.rtf"),
            CFile::modeCreate | CFile::modeWrite);
EDITSTREAM es;

es.dwCookie = (DWORD)&cFile;
es.pfnCallback = MyStreamOutCallback;
m_myRichEditCtrl.StreamOut(SF_RTF, es);
```

### SerialCommView.cpp
- MyStreamOutCallback
```
DWORD CALLBACK CSerialCommView::MyStreamOutCallback(DWORD dwCookie, LPBYTE pbBuff, LONG cb, LONG *pcb)
{
    CFile *pFile = (CFile *)dwCookie;

    pFile->Write(pbBuff, cb);
    *pcb = cb;

    return 0;
}
```
- StreamOut
```
    CFile cFile(TEXT(strPathName), CFile::modeCreate|CFile::modeWrite);
    EDITSTREAM es;

    if (((CButton *)GetDlgItem(IDC_CHECK1HEX))->GetCheck()) { // 日志2
        es.dwCookie = (DWORD) &cFile;
        es.pfnCallback = MyStreamOutCallback;

        ((CRichEditCtrl *)GetDlgItem(IDC_RICHEDIT2LOG2))->StreamOut(SF_RTF, es);
    } else {                                                  // 日志1
        es.dwCookie = (DWORD) &cFile;
        es.pfnCallback = MyStreamOutCallback;

        ((CRichEditCtrl *)GetDlgItem(IDC_RICHEDIT2LOG1))->StreamOut(SF_RTF, es);
    }
```

## Ref
- [Windows Controls: The Rich Edit Control](https://www.functionx.com/visualc/controls/richedit.htm)
