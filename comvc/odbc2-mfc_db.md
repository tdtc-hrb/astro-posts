---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC2 - MFC"
description: "Create CRecordset Class"
date: 2025-12-20
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- Connection String
- Table
- Field mapping

> Take the sales table in the pubs database as an example.

#### head file
- Include the header file in "framework.h":
```
#include <afxdb.h>          // ODBC
```
- Include the header file in "Rec1Set.cpp:
```
#include "pch.h"
#include "Rec1Set.h"
```

#### Class Information
- [Difference between DECLARE_DYNAMIC and DECLARE_DYNCREATE?](https://stackoverflow.com/a/733796)
```
The first declares that a class has runtime type info and the second that instances can be created dynamically at runtime. 
This is described in detail in the MSDN documentation - see links like Run-Time Object Model Services for more info.
```

### Connection String
Use the overloaded method GetDefaultConnect().
```
CString CRec1Set::GetDefaultConnect()
{
	return _T("DSN=sql2000;UID=sa;PWD=pass2word1;DATABASE=pubs");
}
```
### Table
Use the overloaded method GetDefaultSQL().
```
CString CRec1Set::GetDefaultSQL()
{
	return _T("[dbo].[sales]");
}
```

## Field mapping
- Initial
- Record Field Exchange
### Initial
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
#### [snapshot vs dynaset](https://stackoverflow.com/a/9488266)
Always depends on the datasource, in most cases "snapshot" is faster because 
this gives you a read-only view of the data without the indexes coming it to effect. 
On a "dynaset" Access needs to read the indexes in order to determine how to publish updates if you make any changes to the data. 
If your user is able to add new records in this view then "snapshot" will not be available to you.

#### Database
```
public:
	CRec1Set(CDatabase* pDatabase = NULL);
```
#### Field
Define class member variables.
```
public:
	CStringA	m_stor_id;
	CStringA	m_ord_num;
	CTime		m_ord_date;
	int			m_qty;
	CStringA	m_payterms;
	CStringA	m_title_id;
```

### Record Field Exchange
Use the overloaded method DoFieldExchange().
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
