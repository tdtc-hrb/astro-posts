---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The File Dialog - MFC"
description: "Save as a file with a specific extension"
date: 2025-10-31
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Use the [CFileDialog](https://learn.microsoft.com/en-us/cpp/mfc/reference/cfiledialog-class?view=msvc-170#cfiledialog) to customize the file extension, title, and initial directory.
```
explicit CFileDialog(
    BOOL bOpenFileDialog,
    LPCTSTR lpszDefExt = NULL,
    LPCTSTR lpszFileName = NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter = NULL,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0,
    BOOL bVistaStyle = TRUE);
```
- bOpenFileDialog    
> The parameter that specifies what type of dialog box to create.
```
Set it to TRUE to construct a File Open dialog box. 
Set it to FALSE to construct a File Save As dialog box.
```
- lpszDefExt    
The default file name extension.
- lpszFileName    
The initial file name that appears in the Filename box.
- dwFlags
> Use OFN macro combinations.
- lpszFilter    
A series of string pairs that specify filters you can apply to the file. 
- pParentWnd    
A pointer to the parent or owner window of the file dialog box.
- option    
These parameters can be omitted.

### OFN macros
- OFN_HIDEREADONLY
> Hides the Read Only check box.
- OFN_OVERWRITEPROMPT
> Causes the Save As dialog box to generate a message box if the selected file already exists. 
> The user must confirm whether to overwrite the file.

For a description of these flags, 
see the [OPENFILENAME](https://learn.microsoft.com/en-us/windows/win32/api/commdlg/ns-commdlg-openfilenamew) 
structure in the Windows SDK.

## example
```
strFileName.Format("%d%d%d%d%d%d", nYear, nMonth, nDay, nHour, nMinute, nSecond);
strFileName = "D" + strFileName + ".rtf";

    CFileDialog fSaveDialog(FALSE,                  // Set to TRUE to construct a File Open dialog box or 
                                                    // FALSE to construct a File Save As dialog box.
        ".rtf", 
        strFileName, 
        OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT, 
        "Serial Comm Data (*.rtf)|*.rtf|Text (*.txt)|*.txt||", 
        this);
    fSaveDialog.m_pOFN->lpstrTitle = "Serial Comm Data File (Save As...)";
    fSaveDialog.m_pOFN->lpstrInitialDir = "D:";

    if (fSaveDialog.DoModal() == IDOK)
        strPathName = fSaveDialog.GetPathName();
    else
        return;
```
### [m_pOFN](https://learn.microsoft.com/en-us/cpp/mfc/reference/cfiledialog-class?view=msvc-170#m_ofn)
Customize the dialog box title and the initial directory.
```
    fSaveDialog.m_pOFN->lpstrTitle = "Serial Comm Data File (Save As...)";
    fSaveDialog.m_pOFN->lpstrInitialDir = "D:";
```
### [GetPathName](https://learn.microsoft.com/en-us/cpp/mfc/reference/cfiledialog-class?view=msvc-170#getpathname)
The path of the filename includes the file's title plus the entire directory path.


## Ref
- [The File Dialog](https://www.functionx.com/visualc/controls/filedialog.htm)
- [MFC File Processing: The File Dialog Box](https://www.functionx.com/visualc/fileprocessing/dlgfile.htm)
