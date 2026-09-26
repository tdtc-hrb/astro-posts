---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC4 - MFC"
description: "A simple CRecordView demo."
date: 2025-12-20
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- ODBC: 10.0.17763.1
- SQL Server 2000 is deployed on Windows Server 2003 R2 running in VirtualBox

### Setting ODBC
![open odbc](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc1-sql2k0.png)

![empty - odbc](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc2-sql2k0.png)

![create new data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3a-sql2k0.png)

![DSN name - data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3b-sql2k0.png)

![default DB - data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3c-sql2k0.png)

![other - data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3d-sql2k0.png)

![authenticity - data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3e-sql2k0.png)

![finish - data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3f-sql2k0.png)

![test data source](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc3g-sql2k0.png)

![done - odbc](https://github.com/tdtc-hrb/csdn/raw/master/images/odbc4-sql2k0.png)

**Note: The ODBC driver in Windows 10 21H2 can no longer connect to SQL Server 2000.**
### Create SDI Application
![use CFormView](https://github.com/tdtc-hrb/csdn/raw/master/images/app_wizard-rec_demo.png)

![add CRecordSet Class](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class-rec_demo.png)

![add control variable](https://github.com/tdtc-hrb/csdn/raw/master/images/add_variable-rec_demo.png)

### data move
- First
- Next
- Prev
- Last

### show data
```
void CMFCApplication1View::ShowRow()
{
	int nItem;
	CString tmp;

	tmp.Format(_T("%d"), m_pSet->m_qty);
	m_ListCtrl.DeleteAllItems();

	nItem = m_ListCtrl.InsertItem(0, CString(m_pSet->m_stor_id));
	m_ListCtrl.SetItemText(nItem, 1, CString(m_pSet->m_ord_num));
	m_ListCtrl.SetItemText(nItem, 2, m_pSet->m_ord_date.Format("%Y-%m-%d"));
	m_ListCtrl.SetItemText(nItem, 3, tmp);
	m_ListCtrl.SetItemText(nItem, 4, CString(m_pSet->m_payterms));
	m_ListCtrl.SetItemText(nItem, 5, CString(m_pSet->m_title_id));
}
```

## Ref
- [The List Control - MFC Controls](../serialize-n04-mfc)
- [CRecordSet Class](../odbc2-mfc_db)
- [CRecordView](../odbc3-mfc_db)
- [Create a single-document project using the MFC App Wizard in VC++ 5.0/6.0](../sdi_vc56-mfc)
- [recrodDemo.zip](https://mega.nz/file/vYUz3T6J#OvMrH2INHfRq72tGkZftlNLpHpapU0N_3Vt4h7on9fE)
