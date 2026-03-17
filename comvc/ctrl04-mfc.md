---
layout: ../../layouts/MarkdownPostLayout.astro
title: "CMFCTabCtrl - Controls"
description: "Provides the functionality of a Windows combo box."
date: 2025-11-06
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Use the wizard to create a dialog-based MFC application. 
> All settings are default values.

### design
![Drag the label to resize](https://github.com/tdtc-hrb/csdn/raw/master/images/MFCApplication1-cmfctab1.png)
![Set the label to be invisible](https://github.com/tdtc-hrb/csdn/raw/master/images/MFCApplication1-cmfctab2.png)

### impl
First, declare the variable in the header file(MFCApplication1Dlg.h); then, add the implementation in the OnInit() event.
- define
```
protected:
    CMFCTabCtrl m_wndTab;

    CEdit       m_wnd1;
    CEdit       m_wnd2;
```
- OnInitDialog()
Add the following between 
<i>// TODO: Add extra initialization here</i> and 
<i>// return TRUE  unless you set the focus to a control</i>:
```
    CRect rectTab;

    GetDlgItem(IDC_STATIC)->GetWindowRect(&rectTab);
    ScreenToClient(&rectTab);

    // CMFCTabCtrl Create
    m_wndTab.Create(CMFCTabCtrl::STYLE_3D, rectTab, this, 1, CMFCTabCtrl::LOCATION_TOP, TRUE);

    // CEdit Create
    // 2 simple text
    m_wnd1.Create(WS_CHILD | WS_VISIBLE, CRect(0, 0, 100, 100), &m_wndTab, 1);
    m_wnd1.SetWindowText(_T("Edit 1"));

    m_wnd2.Create(WS_CHILD | WS_VISIBLE, CRect(0, 0, 0, 0), &m_wndTab, 2);
    m_wnd2.SetWindowText(_T("Edit 2"));

    // add caption
    m_wndTab.AddTab(&m_wnd1, _T("One"), 0, TRUE);
    m_wndTab.AddTab(&m_wnd2, _T("Two"), 0, FALSE);
```

- src: [CMFCTabCtrlDemo.zip - vs2013](https://mega.nz/file/7BN0WD4R#zDxossI9goWoMRFNjaT7LLr_cAOqFufVRLY_5XgkvyM)

## Ref
- [CMFCTabCtrl not visible in CDialog](https://stackoverflow.com/questions/16455701/cmfctabctrl-not-visible-in-cdialog)
- [CMFCTabCtrl - example](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack/TabControl)
