---
layout: ../../layouts/MarkdownPostLayout.astro
title: "MFC Desktop Applications"
description: "MFC Application Wizard"
date: 2025-10-25
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- [Creating an MFC Application](https://learn.microsoft.com/en-us/cpp/mfc/reference/creating-an-mfc-application)    
name: [SerialComm](https://github.com/tdtc-hrb/SerialComm-mfc)

## MFC Application Wizard
- [Application Type](https://learn.microsoft.com/en-us/cpp/mfc/reference/application-type-mfc-application-wizard)
- [User Interface Features](https://learn.microsoft.com/en-us/cpp/mfc/reference/user-interface-features-mfc-application-wizard)
> default
- [Advanced Features](https://learn.microsoft.com/en-us/cpp/mfc/reference/advanced-features-mfc-application-wizard)
> Cancel All
- View

### Application Type - Single Document
- Project style:
> MFC standard
- Visual style and colors:
> Windows Native/Default

### [View](https://www.infania.net/misc/kbarchive/kb/098/Q98598/index.html)
In step 5 of the AppWizard, select [Generated Classes](https://learn.microsoft.com/en-us/cpp/mfc/reference/generated-classes-mfc-application-wizard) 
and select CFormView as the base class using the Base class combo box.

## Breaking changes
- [noexcept](https://stackoverflow.com/a/10788461)
- [Microsoft C/C++ language conformance by Visual Studio version](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-language-conformance)
- [Microsoft C/C++ change history 2003 - 2015](https://learn.microsoft.com/en-us/cpp/porting/visual-cpp-change-history-2003-2015)

### [noexcept - C++11](https://learn.microsoft.com/en-us/cpp/cpp/noexcept-cpp)
In VC++ (VS2005~VS2010) that does not support the C++11 standard:
```
CMainFrame() noexcept;
```
