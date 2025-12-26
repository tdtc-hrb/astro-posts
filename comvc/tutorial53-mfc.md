---
layout: ../../layouts/MarkdownPostLayout.astro
title: "CMFCPropertySheet 2 - Controls"
description: "Desktop version of Tabs"
date: 2025-12-27
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

In the initial instance of CmnCtrl1.cpp:

- InitInstance()
```
	CAllControlsSheet   allcontrolssheet(_T("Common Controls Sample"));
	m_pMainWnd = &allcontrolssheet;
	allcontrolssheet.DoModal();
	return FALSE;
```

## Project - CmnCtrl1
Use the MFC application wizard to build:
![](https://github.com/tdtc-hrb/csdn/raw/master/images/CmnCtrl1-cmfcpg1.png)

Solution after deleting One1pg:
![](https://github.com/tdtc-hrb/csdn/raw/master/images/CmnCtrl1-cmfcpg2.png)

### Create PropertyPage
Add MFC Class:
```
Add -> Class
MFC -> MFC Class
```
![](https://github.com/tdtc-hrb/csdn/raw/master/images/CmnCtrl1-cmfcpg3.png)

Note!!!
```
Base class selection: CPropertyPage, otherwise you cannot select the Diglog ID!

In "Diglog ID", select an existing one.
```
![](https://github.com/tdtc-hrb/csdn/raw/master/images/CmnCtrl1-cmfcpg4.png)

### Create PropertySheet
![](https://github.com/tdtc-hrb/csdn/raw/master/images/CmnCtrl1-cmfcpg5.png)
- declare
```
// Attributes
public:
	CTreeCtrlPage       m_treectrlpage;
	CAnimateCtrlPage    m_animctrlpage;
```
- add pages
```
protected:
	void AddControlPages(void);
```

#### add pages
```
void CAllControlsSheet::AddControlPages()
{
	m_hIcon = AfxGetApp()->LoadIcon(IDR_MAINFRAME);
	m_psh.dwFlags |= PSP_USEHICON;
	m_psh.hIcon = m_hIcon;
	m_psh.dwFlags |= PSH_NOAPPLYNOW;    // Lose the Apply Now button
	m_psh.dwFlags &= ~PSH_HASHELP;  // Lose the Help button

	AddPage(&m_treectrlpage);
	AddPage(&m_animctrlpage);
}
```
m_hIcon declare:
```
protected:
	HICON m_hIcon;
```
#### constructor
- declare
```
// Construction
public:
	CAllControlsSheet(UINT nIDCaption, CWnd* pParentWnd = NULL, UINT iSelectPage = 0);
	CAllControlsSheet(LPCTSTR pszCaption, CWnd* pParentWnd = NULL, UINT iSelectPage = 0);
```
- impl
```
CAllControlsSheet::CAllControlsSheet(UINT nIDCaption, CWnd* pParentWnd, UINT iSelectPage)
:CMFCPropertySheet(nIDCaption, pParentWnd, iSelectPage)
{
	AddControlPages();

	// TODO :: Add the pages for the rest of the controls here.
}

CAllControlsSheet::CAllControlsSheet(LPCTSTR pszCaption, CWnd* pParentWnd, UINT iSelectPage)
	:CMFCPropertySheet(pszCaption, pParentWnd, iSelectPage)
{
	AddControlPages();
}
```

## Ref
- [example: MFC/general/CmnCtrl1](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/general/CmnCtrl1)
