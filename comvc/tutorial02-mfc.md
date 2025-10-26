---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Custom resources - MFC"
description: "Add or remove tool buttons and menus; Add dialog boxes;"
date: 2025-10-26
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- Double-click "*.rc2" to enter the resource viewer.

#### menus
Remove "New" from the menu.
- In the menu, right-click the "New" and select "Delete".


### tool button
Remove the print button from the toolbar;

#### icon
- In the toolbar, right-click the Print icon and select "Delete".
- In the toolbar, right-click the New icon and select "Delete".
- In the toolbar, Drag icons to fill the empty buttons.

#### rc
at 
```
IDR_MAINFRAME TOOLBAR 16, 15
```
removed:
- BUTTON      ID_FILE_NEW
- BUTTON      ID_FILE_PRINT

### dialog
In the dialog:
```
Add Resource -> 
```
- IDD_DIALOGBAR
> Port Configuration

Right-click the dialog box， Add MFC Class：
- class name: CConfigDlg
- bass class: CDialog
- .h file: ConfigDlg.h
- .cpp file: ConfigDlg.cpp

## Breaking changes
- [nullptr - c++11](https://en.cppreference.com/w/cpp/language/nullptr.html)
- [Microsoft C/C++ language conformance by Visual Studio version](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-language-conformance)
- [Microsoft C/C++ change history 2003 - 2015](https://learn.microsoft.com/en-us/cpp/porting/visual-cpp-change-history-2003-2015)

### [nullptr](https://ece.uwaterloo.ca/~dwharder/icsrts/C/14)
In VC++ (VS2005~VS2010) that does not support the C++11 standard:
```
CConfigDlg(CWnd* pParent = nullptr);
```

## Ref
- [MFC Dialog Boxes: Dialog Bars](https://www.functionx.com/visualc/dialogboxes/dialogbars.htm)
- [MFC Property Sheets and Property Pages](https://www.functionx.com/visualc/dialogboxes/mfcpspp.htm)
