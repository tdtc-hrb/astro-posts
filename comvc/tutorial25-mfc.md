---
layout: ../../layouts/MarkdownPostLayout.astro
title: "A Brief History of MFC"
description: "MFC Faq V5.6"
date: 2025-11-18
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

## Basic
[MFC 2.0](https://documentation.help/MFC/chapter3_4.htm) was a 16-bit release that shipped with Visual C++ 1.0. 
It added the Document/View framework on top of MFC 1.0 and also added OLE 1.0 classes, 
message maps and common dialog classes. This was a 16-bit release released on 02/93.

### Document Architecture
- CCmdTarget
- CWinApp
> Moved in hierarchy, use to be derived from CObject

- CDocTemplate
- CSingleDocTemplate
- CMultiDocTemplate
- CDocument
- COleDocument
- COleClientDoc
- COleServerDoc

#### Views
- CView
- CScrollView
- CFormView
- CEditView

## Improved
- MFC 3.1
- MFC 9.0

### [MFC 3.1](https://documentation.help/MFC/chapter3_8.htm)
MFC 3.1 shipped with Visual C++ 2.1 in 1/95. 
It introduced MAPI, WinSock and Windows Common Controls. 
The MFC toolbar, status bar, etc.. still live in MFC. 
- Windows Common Controls: Classes All of these are CWnd derived

## Ref
- [MFC 1.0](https://documentation.help/MFC/chapter3_3.htm)
- [MFC 2.5](https://documentation.help/MFC/chapter3_6.htm)
- [MFC 3.0](https://documentation.help/MFC/chapter3_7.htm)
- [MFC 4.0](https://documentation.help/MFC/chapter3_10.htm)
