---
layout: ../../layouts/MarkdownPostLayout.astro
title: "my first mfc application"
description: "using CFrameWnd and CWinApp."
date: 2025-11-15
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- project wizard
- class wizard
- add window title
- Instantiation
### project wizard
Create an empty Win32 project.

![win32 project](https://github.com/tdtc-hrb/csdn/raw/master/images/new_project1-win32.png)
![empty project](https://github.com/tdtc-hrb/csdn/raw/master/images/new_project2-win32.png)

#### VS2022
> Windows Desktop Wizard

![empty project - VS2022](https://github.com/tdtc-hrb/csdn/raw/master/images/new_project2d14-win32.png)
> d: VS2022 is the fourth version of v14.
> 14(17.14): 14 is the last minor version of VS2022.

### Generate using the class wizard
![Main Window](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class1-win32.png)
![My App](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class2-win32.png)

Note:    
You need to include "afxwin.h" in all header files.

### add window caption - MainWindow
Add constructor

- declare
```
public:
    CMainWindow();
```
- impl
```
CMainWindow::CMainWindow()
{
    Create(NULL, _T("Hello MFC"));
}
```

### add initial instance - MyApp
- declare
```
public:
    virtual BOOL InitInstance();
```
- impl
```
BOOL CMyApp::InitInstance()
{
    m_pMainWnd = new CMainWindow();
    m_pMainWnd->ShowWindow(SW_SHOW);
    m_pMainWnd->UpdateWindow();
    return TRUE;
}
```

#### include head file
```
#include "CMainWindow.h"
```

### done
Add it to MyApp.cpp
```
CMyApp myApp;
```

#### compile
```
error C1189: #error :  Building MFC application with /MD[d] (CRT dll version) requires MFC shared dll version. 
Please #define _AFXDLL or do not use /MD[d]
```
![project property](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_static_lib-win32.png)

- VC6

![project property](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_static_lib1vc6-win32.png)

## Ref
- [CD-ROM Jeff Prosise MFC 2nd Edition.zip](https://github.com/definedrisk/prosise-mfc2e)
- [First MFC - demo](https://mega.nz/file/jdMigRQJ#Rd7ByMLLh8yhwhRh4tGKahOI8MO7watZwrRUsPnwBVc)
