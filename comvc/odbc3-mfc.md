---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC3 - MFC"
description: "CRecordView"
date: 2026-09-24
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
![application wizard - step6](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard6c-vc12.png)

(Figure: Step 6 of the MFC Application Wizard in Visual Studio 2013)

**NOTE: The database wizard is no longer provided in VS2017 and later versions.**

### operation data
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

## invoke CRec1Set
- member
```
// Attributes
public:
	CRec1Set m_Rec1Set;
```
at "MFCApplication1Doc.h"
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
- [Create a single-document project using the MFC App Wizard in VC++ 5.0/6.0](../sdi_vc56-mfc)
