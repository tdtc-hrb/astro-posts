---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The List Control - MFC Controls"
description: "Report View"
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Right-click the list control -> Properties, View: Report.

and Add Variable: 
![m_ListOfDb](https://github.com/tdtc-hrb/csdn/raw/master/images/add_var3-ctl.png)

### col
- impl
```
void CMFCApplication1Dlg::FormatColumns()
{
    m_ListOfDb.InsertColumn(0, _T("Server"), LVCFMT_LEFT, 80);
    m_ListOfDb.InsertColumn(1, _T("Database"), LVCFMT_LEFT, 80);
    m_ListOfDb.InsertColumn(2, _T("User"), LVCFMT_LEFT, 80);
    m_ListOfDb.InsertColumn(3, _T("Password"), LVCFMT_LEFT, 80);
    m_ListOfDb.InsertColumn(4, _T("Type"), LVCFMT_LEFT, 80);
}
```

### row
```
void CMFCApplication1Dlg::SetGridView()
{
    int nItem;

    nItem = m_ListOfDb.InsertItem(0, _T("ser1"));
    m_ListOfDb.SetItemText(nItem, 1, _T("db1"));
    m_ListOfDb.SetItemText(nItem, 2, _T("user1"));
    m_ListOfDb.SetItemText(nItem, 3, _T("pwd1"));
    m_ListOfDb.SetItemText(nItem, 4, _T("0"));

    nItem = m_ListOfDb.InsertItem(1, _T("ser2"));
    m_ListOfDb.SetItemText(nItem, 1, _T("db2"));
    m_ListOfDb.SetItemText(nItem, 2, _T("user2"));
    m_ListOfDb.SetItemText(nItem, 3, _T("pwd2"));
    m_ListOfDb.SetItemText(nItem, 4, _T("0"));
}
```

## Ref
- [How to add items to a List Control in an MFC dialog](https://stackoverflow.com/a/18802485)
- [InsertColumn()](https://learn.microsoft.com/en-us/cpp/mfc/reference/clistctrl-class?view=msvc-170#insertcolumn)
- [InsertItem()](https://learn.microsoft.com/en-us/cpp/mfc/reference/clistctrl-class?view=msvc-170#insertitem)
- [SetItemText()](https://learn.microsoft.com/en-us/cpp/mfc/reference/clistctrl-class?view=msvc-170#setitemtext)
