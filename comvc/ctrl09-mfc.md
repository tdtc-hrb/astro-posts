
---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Add Variable - MFC Control"
description: "Let's take ListBox and Edit as examples."
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

Add Variable: 
- First, declare the values ​​for the variables; 
![add member variable wizard](https://github.com/tdtc-hrb/csdn/raw/master/images/add_var1-ctl.png)
![add member variable wizard](https://github.com/tdtc-hrb/csdn/raw/master/images/add_var2-ctl.png)
- then, change the name of the DDX Functions.

#### [DDX Functions](https://learn.microsoft.com/en-us/cpp/mfc/reference/standard-dialog-data-exchange-routines?view=msvc-170#ddx-functions)
|Name |Description|
|-|-|
|DDX_CBIndex | Initializes or retrieves the index of the current selection of a combo box control.|
|DDX_CBString | Initializes or retrieves the current contents of the edit field of a combo box control.|
|DDX_CBStringExact | Initializes or retrieves the current contents of the edit field of a combo box control.|
|DDX_Check | Initializes or retrieves the current state of a check box control.|
|DDX_Control | Subclasses a given control within a dialog box.|
|DDX_DateTimeCtrl | Initializes or retrieves date and/or time data of a date and time picker control.|
|DDX_IPAddress | Initializes or retrieves the current value of an IP address control.|
|DDX_LBIndex | Initializes or retrieves the index of the current selection of a list box control.|
|DDX_LBString | Initializes or retrieves the current selection within a list box control.|
|DDX_LBStringExact | Initializes or retrieves the current selection within a list box control.|
|DDX_ManagedControl | Creates a .NET control matching the control's resource ID.|
|DDX_MonthCalCtrl | Initializes or retrieves the current value of a month calendar control.|
|DDX_Radio | Initializes or retrieves the 0-based index of the radio control that is currently checked within a radio control group.|
|DDX_Scroll | Initializes or retrieves the current position of a scroll control's thumb.|
|DDX_Slider | Initializes or retrieves the current position of a slider control's thumb.|
|DDX_Text | Initializes or retrieves the current value of an edit control.|

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
