---
layout: ../../layouts/MarkdownPostLayout.astro
title: "CMFCPropertySheet 1 - Controls"
description: "Desktop version of Tabs"
date: 2025-12-26
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Perform the following steps to use the CMFCPropertySheet class in your application:

1. Derive a class from the CMFCPropertySheet class and name the class, for example, CMyPropertySheet.
2. Construct a CMFCPropertyPage object for each property page.
3. Call the CMFCPropertySheet::SetLook method in the CMyPropertySheet constructor. 
A parameter of that method specifies that property pages shall be displayed either as tabs along the top or left of the property sheet; 
tabs in the style of a Microsoft OneNote property sheet; buttons on a Microsoft Outlook toolbar control; 
nodes on a tree control; or as a list of items on the left side of the property sheet.
4. If you create a property sheet in the style of a Microsoft Outlook toolbar, 
call the CMFCPropertySheet::SetIconsList method to associate an image list together with the property pages.
5. Call the CMFCPropertySheet::AddPage method for each property page.
6. Create a CMFCPropertySheet control and call its DoModal method.

#### omitted
Steps that can be omitted: Steps three and four.

If omitted, it becomes the same as CPropertySheet.
### include file
- Property page
```
#include "afxpropertypage.h"
```
- property sheet
```
#include <afxpropertysheet.h>
```
### The difference between CMFCPropertyPage and CPropertyPage
CMFCPropertyPage:
```
	friend class CMFCPopupMenu;
	friend class CContextMenuManager;
	friend class CMFCDropDownListBox;
	friend class CMFCPropertySheet;
```
CPropertyPage:
```
friend class CPropertySheet;
```

## Ref
- [CMFCPropertySheet class](https://learn.microsoft.com/en-us/cpp/mfc/reference/cmfcpropertysheet-class?view=msvc-170)
