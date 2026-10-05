---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC2 - MFC"
description: "Create CRecordset Class"
date: 2026-09-26
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
### [Data Source (ODBC)](https://learn.microsoft.com/en-us/cpp/data/odbc/data-source-odbc?view=msvc-170)
```
public:
	CRec1Set(CDatabase* pDatabase = NULL);
```
In database terms, a data source is a specific set of data, the information required to access that data, and the location of the data source, 
which can be described using a data-source name. To work with class [CDatabase](https://learn.microsoft.com/en-us/cpp/mfc/reference/cdatabase-class?view=msvc-170), 
the data source must be one that you have configured through Open Database Connectivity (ODBC) Administrator. 
Examples of data sources include a remote database running on Microsoft SQL Server across a network or a Microsoft Access file in a local directory. 
From your application, you can access any data source for which you have an ODBC driver.

### Field
- Declare
```
public:
	CStringA	m_stor_id;
	CStringA	m_ord_num;
	CTime		m_ord_date;
	int			m_qty;
	CStringA	m_payterms;
	CStringA	m_title_id;
```
- Initial
```
CRec1Set::CRec1Set1Set(CDatabase* pdb)
	: CRecordset(pdb)
{
	m_stor_id = "";
	m_ord_num = "";
	m_ord_date;
	m_qty = 0;
	m_payterms = "";
	m_title_id = "";
	m_nFields = 6;
	m_nDefaultType = dynaset;
}
```

## handling
invoke overloaded method:
- GetDefaultConnect()
- GetDefaultSQL()
- DoFieldExchange()
### Connection String
```
CString CRec1Set::GetDefaultConnect()
{
	return _T("DSN=sql2000;UID=sa;PWD=pass2word1;DATABASE=pubs");
}
```
### Table
```
CString CRec1Set::GetDefaultSQL()
{
	return _T("[dbo].[sales]");
}
```
### Record Field Exchange
```
void CRec1Set::DoFieldExchange(CFieldExchange* pFX)
{
	pFX->SetFieldType(CFieldExchange::outputColumn);
// Macros such as RFX_Text() and RFX_Int() are dependent on the
// type of the member variable, not the type of the field in the database.
// ODBC will try to automatically convert the column value to the requested type
	RFX_Text(pFX, _T("[stor_id]"), m_stor_id);
	RFX_Text(pFX, _T("[ord_num]"), m_ord_num);
	RFX_Date(pFX, _T("[ord_date]"), m_ord_date);
	RFX_Int(pFX, _T("[qty]"), m_qty);
	RFX_Text(pFX, _T("[payterms]"), m_payterms);
	RFX_Text(pFX, _T("[title_id]"), m_title_id);
}
```

## Ref
- [CRecordset class](https://learn.microsoft.com/en-us/cpp/mfc/reference/crecordset-class?view=msvc-170)
- [Record Field Exchange](https://learn.microsoft.com/en-us/cpp/mfc/reference/record-field-exchange-functions?view=msvc-170)
- [Create a single-document project using the MFC App Wizard in VC++ 5.0/6.0](../sdi_vc56-mfc)
- [Difference between DECLARE_DYNAMIC and DECLARE_DYNCREATE?](https://stackoverflow.com/a/733796)
- [snapshot vs dynaset](https://stackoverflow.com/a/9488266)
