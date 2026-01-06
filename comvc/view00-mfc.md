---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The Message Map - Mgr"
description: "Tree view message events"
date: 2025-12-09
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Previously, we used manually added message maps; 
now we'll use VC's GUI to manage them.

This is mostly applied to controls that are not draggable. 
For example: MFC View Classes.

#### MFC View Classes
|Class Name |Description |
|-|-|
|CView |Root class for all view classes |
|CCtrlView |Base class for CEditView, CRichEditView, CListView, and CTreeView; can be used to create view classes based on other types of controls |
|CEditView |Wraps the multiline edit control and adds print, search, and search-and-replace capabilities |
|CRichEditView |Wraps the rich edit control |
|CListView |Wraps the list view control |
|CTreeView |Wraps the tree view control |
|CHtmlView |Creates views from HTML files and other media supported by the Microsoft Internet Explorer WebBrowser control |
|CScrollView |Adds scrolling capabilities to CView; base class for |
|CFormView |Implements scrollable "form" views created from dialog templates |
|CRecordView |CFormView derivative designed to display records obtained from an ODBC database |
|CDaoRecordView |DAO version of CRecordView |
|COleDBRecordView |OLE DB version of CRecordView|

### CTreeView
Take OnTvnSelchanged as an example.

![class wizard](https://github.com/tdtc-hrb/csdn/raw/master/images/class_wizard-vc12.png)

Switch to the "Messages" tab; double-click the selected event.

![Before double-clicking;](https://github.com/tdtc-hrb/csdn/raw/master/images/tv_selchanged1a-vc12.png)

![After double-clicking.](https://github.com/tdtc-hrb/csdn/raw/master/images/tv_selchanged1b-vc12.png)

## Ref
- [The Message Map](https://tdtc-hrb.github.io/com-vc/posts/hello2-mfc)
- [Tree Views](https://tdtc-hrb.github.io/com-vc/posts/view02-mfc)
