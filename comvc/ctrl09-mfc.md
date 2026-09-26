---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Add Variable - MFC Control"
description: "Let's take ListBox and Edit as examples."
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- First, declare the values ​​for the variables;
- then, change the name of the [DDX Functions](https://learn.microsoft.com/en-us/cpp/mfc/reference/standard-dialog-data-exchange-routines?view=msvc-170#ddx-functions).

#### Add Variable
After dragging a "listbox" from the "Toolbox," right-click and select "Add Variable..."

![add member variable wizard](https://github.com/tdtc-hrb/csdn/raw/master/images/add_var1-ctl.png)

![add member variable wizard](https://github.com/tdtc-hrb/csdn/raw/master/images/add_var2-ctl.png)

### ListBox
- onInitXXX()
```
    m_Types.AddString(_T("MS-Access"));
    m_Types.AddString(_T("MSSQL"));
    m_Types.AddString(_T("MySQL"));
```
for example:
```
    int iCurSel = 0;
    iCurSel = m_Types.GetCurSel();
    CString tmp;
    tmp.Format(_T("%d"), iCurSel);
    AfxMessageBox(tmp);
```

### Edit
- first: change function name
```
void CMFCApplication1Dlg::DoDataExchange(CDataExchange* pDX)
{
    CDialogEx::DoDataExchange(pDX);
    DDX_Control(pDX, IDC_EDIT1, m_Server);
}
```
change:
```
void CMFCApplication1Dlg::DoDataExchange(CDataExchange* pDX)
{
    CDialogEx::DoDataExchange(pDX);
    DDX_Text(pDX, IDC_EDIT1, m_Server);
}
```
Otherwise, the following will occur:
```
error C2664: 'void DDX_Control(CDataExchange *,int,CWnd &)' : cannot convert argument 3 from 'CString' to 'CWnd &'
```

- Last: UpdateData
```
    m_Types.GetText(iCurSel, tmp);
    m_Server = tmp;
    // Update the display
    UpdateData(FALSE);
```

## Ref
- [List Box](https://www.functionx.com/visualc/controls/listbox.htm)
- [addVarDemo.zip](https://mega.nz/file/SZ0SVTiA#013V7bSmIZ9zaOm8MjREH3cqtxF1QCozj2kRJ75xd94)
