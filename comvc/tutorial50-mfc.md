---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC3 - MFC"
description: "CRecordView"
date: 2025-12-21
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
(Figure: Step 6 of the MFC Application Wizard in VS 2013)

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

### Document/View
- document - declare
```
// Attributes
public:
	CRec1Set m_Rec1Set;
```
- view - declare
```
public:
#ifdef AFX_DESIGN_TIME
	enum{ IDD = IDD_MFCAPPLICATION1_FORM };
#endif
	CRec1Set* m_pSet;
```

### init
Initialization is performed in "MFCApplication1View.cpp".
```
	// TODO: add construction code here
	m_pSet = nullptr;
```
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

## Ref
- [CRecordView Class](https://learn.microsoft.com/en-us/cpp/mfc/reference/crecordview-class?view=msvc-170)
