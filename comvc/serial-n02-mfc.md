---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Custom resources - MFC"
description: "Add or remove tool buttons and menus; Add dialog boxes;"
date: 2025-11-20
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- Double-click "*.rc2" to enter the resource viewer.

#### menus
Remove "New" from the menu.
- In the menu, right-click the "New" and select "Delete".


### tool button
Remove the print and new button from the toolbar;

- In the toolbar, right-click the Print icon and select "Delete".
- In the toolbar, right-click the New icon and select "Delete".
- In the toolbar, Drag icons to fill the empty buttons.

![The effect after dragging](https://github.com/tdtc-hrb/csdn/raw/master/images/MFCApplication1.rc-after_drag.png)

Note:    
必须保证图标是一个挨一个的排列。

#### rc(part)
使用Notepad++, 修改*.rc
```
/////////////////////////////////////////////////////////////////////////////
//
// Toolbar
//

IDR_MAINFRAME TOOLBAR 16, 15
BEGIN
    BUTTON      ID_FILE_OPEN
    BUTTON      ID_FILE_SAVE
    BUTTON      ID_EDIT_CUT
    BUTTON      ID_EDIT_COPY
    BUTTON      ID_EDIT_PASTE
    SEPARATOR
    BUTTON      ID_APP_ABOUT
END
```
保存后，Visual Studio 会弹出对话框: 
```
This file has been modified outside of Microsoft Visual Studio. 
Do you want to reload it?
```
点击"yes".

再次打开Toolbar下的IDR_MAINFRAME 会弹出对话框: 
```
The bitmap for this toolbar must be adjusted to use this size.
Adjust the bitmap to fit?
```
点击"OK".

最后, 
```
File -> Save<ProjectName>.rc, 
```
保存图片。

### dialog
In the dialog:
```
Add Resource -> 
```
- IDD_DIALOGBAR
> Port Configuration

Right-click the dialog box， Add MFC Class：
- class name: CConfigDlg
- bass class: CDialog/CDialogEx
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
