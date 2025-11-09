---
layout: ../../layouts/MarkdownPostLayout.astro
title: "MFC Desktop Applications"
description: "MFC Application Wizard"
date: 2025-11-02
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- [Creating an MFC Application](https://learn.microsoft.com/en-us/cpp/mfc/reference/creating-an-mfc-application)    
name: [SerialComm](https://github.com/tdtc-hrb/SerialComm-mfc)

### IDE
- [VS2013](https://download.microsoft.com/download/A/A/D/AAD1AA11-FF9A-4B3C-8601-054E89260B78/vs2013.5_ce_enu.iso)    
VS 2010 is slower than ever, 2012 is less slow, 2013 is even less slow. 
I would go with the last one just to have more recent C++ features and excellent debugging experience. 
You might want to read about the issues and good sides of recent VS versions in this blog article 
from dark_sylink who is the main contributor for Ogre 2.0 : https://www.yosoygames.com.ar/wp/2013/12/microsoft-we-need-to-talk-about-visual-studio

- [MFC MBCS DLL Add-on](https://learn.microsoft.com/en-us/cpp/mfc/mfc-mbcs-dll-add-on)    
Support for MFC and its multibyte character set (MBCS) libraries requires 
an additional step during Visual Studio installation in Visual Studio 2013 and later.

Download the DLL at [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

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
