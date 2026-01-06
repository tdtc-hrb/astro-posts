---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Combo-box - Controls"
description: "Provides the functionality of a Windows combo box."
date: 2025-11-04
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Place two combo box controls: 
- m_strPortNum
- IDC_COMBO1Timer

### List Creation
- data propertie    
Right-click the combo box, select Properties, and enter the following in the DATA field:
```
500;1000;2000;
```
- Control initial events    
for example: OnInitialUpdate() or OnInitDialog(). etc.

#### OnInitialUpdate()
```
void CSerialCommView::OnInitialUpdate()
{
    CFormView::OnInitialUpdate();
    GetParentFrame()->RecalcLayout();
    ResizeParentToFit();

    // Add String
    CArray<SSerInfo,SSerInfo&> asi;

    // Populate the list of serial ports.
    EnumSerialPorts(asi,FALSE/*include all*/);

    for (int ii = 0; ii< asi.GetSize(); ii++) {
        m_strPortNum.AddString(asi[ii].strFriendlyName);
    }
}
```

### The Selected String
```
    CString strTemp;
    int nCurSel;

    nCurSel = ((CComboBox *) GetDlgItem(IDC_COMBO1Timer))->GetCurSel();
    ((CComboBox *) GetDlgItem(IDC_COMBO1Timer))->GetLBText(nCurSel, strTemp);
```

## Ref
- [AddString()](https://learn.microsoft.com/en-us/cpp/mfc/reference/ccombobox-class?view=msvc-170#example)
- [GetCurSel()](https://learn.microsoft.com/en-us/cpp/mfc/reference/ccombobox-class?view=msvc-170#getcursel)
- [GetLBText()](https://learn.microsoft.com/en-us/cpp/mfc/reference/ccombobox-class?view=msvc-170#getlbtext)
