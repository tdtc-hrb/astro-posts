---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Combo-box Control - ComboExo example"
description: "Create a new ComboExo using VS2013"
date: 2025-11-04
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- MFC Application Wizard
- design dialog
- event

### [ComboExo example - visualc](https://www.functionx.com/visualc/controls/combobox1.htm)
The original [example](https://www.functionx.com/visualc/samples/comboexo.exe) was written using VC6.0; now we will rewrite it using VS2013. 
After downloading, click "Extract" to extract the source files.

Move files to the "res" directory: 
- res/ComboExo.ico
- res/ComboExo.rc2

#### [Recompile with Visual Studio 2015+](https://stackoverflow.com/a/44462055)
```
D8016 '/ZI' and '/Gy-' command-line options are incompatible
```
C/C++ -> General -> Debug Information Format
```
Program Database(/Zi)
```

## MFC Application Wizard
- [Application Type](https://learn.microsoft.com/en-us/cpp/mfc/reference/application-type-mfc-application-wizard)
- [User Interface Features](https://learn.microsoft.com/en-us/cpp/mfc/reference/user-interface-features-mfc-application-wizard)
> default
- [Advanced Features](https://learn.microsoft.com/en-us/cpp/mfc/reference/advanced-features-mfc-application-wizard)
> Cancel All

### Application Type - Dialog based
- Project style:
> MFC standard
- Dialog based options:
> none

## design dialog
Drag and drop from the toolbox:
- Combo box
- Edit Control

### List height
There are two ways to adjust the list height:

1. [Drag the "down arrow"](https://stackoverflow.com/a/2513306)
![down arrow](https://github.com/tdtc-hrb/csdn/raw/master/images/MFCApplication1-combobox.png)
2. [Configure the rc file](https://stackoverflow.com/a/6095864)    
Original data:
```
COMBOBOX        IDC_COMBO1,58,39,48,30,CBS_DROPDOWN | CBS_SORT | WS_VSCROLL | WS_TABSTOP
```
new data: Height of the 4 items
```
COMBOBOX        IDC_COMBO1,58,39,48,48,CBS_DROPDOWN | CBS_SORT | WS_VSCROLL | WS_TABSTOP
```

## event
- CBN_SELCHANGE
> IDC_COMBO1 -> Properties
- OnInitXXX

### CBN_SELCHANGE
Click the "CBN_SELCHANGE" event property and select "<Add> OnCbnSelchangeCombo1" from the drop-down menu.
![Sent when the user changes the current selection in the list box of a combo box](https://github.com/tdtc-hrb/csdn/raw/master/images/MFCApplication1-combobox1.png)
```
void CComboExoDlg::OnCbnSelchangeCombo1()
{
    // TODO: Add your control notification handler code here
    CString strTemp;
    int nCurSel;

    nCurSel = ((CComboBox*)GetDlgItem(IDC_COMBO1))->GetCurSel();
    ((CComboBox*)GetDlgItem(IDC_COMBO1))->GetLBText(nCurSel, strTemp);

    GetDlgItem(IDC_EDIT1)->SetWindowText(strTemp);
}
```
### OnInitDialog()
```
// Add 20 items to the combo box.
CString str;
for (int i = 0; i < 20; i++)
{
    str.Format(_T("item string %d"), i);
    ((CComboBox*)GetDlgItem(IDC_COMBO1))->AddString(str);
}
```
