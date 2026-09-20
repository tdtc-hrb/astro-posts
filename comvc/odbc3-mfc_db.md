---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC3 - MFC"
description: "CRecordView"
date: 2025-12-24
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Use the CFormView template, 
and then manually rewrite it as CRecordView.
- Inheritance Hierarchy
```
CObject
    CCmdTarget
        CWnd
            CView
                CScrollView
                    CFormView
                        CRecordView
```
> NOTE!!! The database wizard is no longer provided in VS2017 and later versions.

![application wizard - step6](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard6c-vc12.png)
(Figure: Step 6 of the MFC Application Wizard in Visual Studio 2013)

### database support
Implement database support in CRecordView.
#### impl
```
// CMFCApplication1View database support
CRecordset* CMFCApplication1View::OnGetRecordset()
{
	return m_pSet;
}
```
#### declare
```
// Overrides
public:
	virtual CRecordset* OnGetRecordset();
```

## Document/View
A document is a collection of data in your application with which the user interacts.

Although the word document seems to imply something of a textual nature, it isn’t limited to text. 
It could be data for a game, a geometric model, a text file, or, indeed, anything you want.

The term document is just a convenient label for the application data in your program, treated as a unit.
### member
```
// Attributes
public:
	CRec1Set m_Rec1Set;
```
you add your own data members to store items that your application requires.
### init
Initialization is performed in "MFCApplication1View.cpp".
```
	// TODO: add construction code here
	m_pSet = nullptr;
```
#### define
```
public:
#ifdef AFX_DESIGN_TIME
	enum{ IDD = IDD_MFCAPPLICATION1_FORM };
#endif
	CRec1Set* m_pSet;
```
at "MFCApplication1View.h"

![Figure 12-2](https://github.com/tdtc-hrb/csdn/raw/master/images/figure12.2-vc12.png)
uses dashed arrows to show how pointers are used to relate objects. These pointers 
enable function members of one object to access the public data or function members in the interface of another object.

#### OnInitialUpdate
- old
```
	CFormView::OnInitialUpdate();
	GetParentFrame()->RecalcLayout();
	ResizeParentToFit();
```
- new
```
	m_pSet = &GetDocument()->m_Rec1Set;
	CRecordView::OnInitialUpdate();
```
member functions(GetDocument()) to support processing of that data.

## Ref
- [CRecordView Class](https://learn.microsoft.com/en-us/cpp/mfc/reference/crecordview-class?view=msvc-170)
- Chapter 12: Windows Programming with the Microsoft Foundation Classes (MFC) - Beginning Visual C++ 2013
