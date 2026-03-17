---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Sorting in a List Control"
description: "Usage SortItems()"
date: 2025-12-14
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Unless a list view has the style LVS_NOSORTHEADER, 
clicking a header item sends an LVN_COLUMNCLICK notification to the list view's parent. 
An application's usual response to an LVN_COLUMNCLICK notification is to call CListCtrl::SortItems to sort the list view items.

You do have to provide a callback function that the control's built-in sorting routine can 
call to compare a pair of arbitrarily selected items. 
The bad news is that the comparison function receives just three parameters: 
the 32-bit lParam values of the two items being compared 
and an application-defined lParam value that equals the second parameter passed to SortItems. 

And an application that stores its own item data uses memory inefficiently if it assigns text strings to the list view's items and 
subitems because then the data ends up being stored in memory twice. 
You can avoid such wastefulness by specifying LPSTR_TEXTCALLBACK for the item and subitem text and 
providing text to the list view control in response to LVN_GETDISPINFO notifications.

#### LVN event
- LVN_COLUMNCLICK

![col click - list control](https://github.com/tdtc-hrb/csdn/raw/master/images/col_click-event_handler.png)

- LVN_GETDISPINFO

![disp info - list control](https://github.com/tdtc-hrb/csdn/raw/master/images/disp_info-event_handler.png)

### SortItems
package info:
```
typedef struct tagITEMINFO {
	CString     strServer;
	CString     strDatabase;
	CString     strUser;
	CString     strPassword;
	int         nType;
} ITEMINFO;
```
#### LVN_COLUMNCLICK - event
```
void CMFCApplication1Dlg::OnLvnColumnclickList2(NMHDR *pNMHDR, LRESULT *pResult)
{
	LPNMLISTVIEW pNMLV = reinterpret_cast<LPNMLISTVIEW>(pNMHDR);
	// TODO: Add your control notification handler code here
	m_ListOfDb.SortItems(CompareFunc, pNMLV->iSubItem);
	*pResult = 0;
}
```
- CompareFunc
```
int CALLBACK CMFCApplication1Dlg::CompareFunc(LPARAM lParam1, LPARAM lParam2, LPARAM lParamSort)
{
	ITEMINFO* pItem1 = (ITEMINFO*)lParam1;
	ITEMINFO* pItem2 = (ITEMINFO*)lParam2;
	int nResult;

	switch (lParamSort) {
	case 0: // Server
		nResult = pItem1->strServer.CompareNoCase(pItem2->strServer);
		break;
	case 1: // data base
		nResult = pItem1->strDatabase.CompareNoCase(pItem2->strDatabase);
		break;
	case 2: // user
		nResult = pItem1->strUser.CompareNoCase(pItem2->strUser);
		break;
	case 3: // password
		nResult = pItem1->strPassword.CompareNoCase(pItem2->strPassword);
		break;

	case 4: // type
		nResult = pItem1->nType - pItem2->nType;
		break;
	}

	return nResult;
}
```
#### Getdispinfo - envent
```
void CMFCApplication1Dlg::OnLvnGetdispinfoList2(NMHDR *pNMHDR, LRESULT *pResult)
{
	NMLVDISPINFO *pDispInfo = reinterpret_cast<NMLVDISPINFO*>(pNMHDR);
	// TODO: Add your control notification handler code here
	CString string;

	if (pDispInfo->item.mask & LVIF_TEXT) {
		ITEMINFO* pItem = (ITEMINFO*)pDispInfo->item.lParam;

		switch (pDispInfo->item.iSubItem) {

		case 0: // Server
			::lstrcpy(pDispInfo->item.pszText, pItem->strServer);
			break;

		case 1: // Database
			::lstrcpy(pDispInfo->item.pszText, pItem->strDatabase);
			break;

		case 2: // User
			::lstrcpy(pDispInfo->item.pszText, pItem->strUser);
			break;

		case 3: // Password
			::lstrcpy(pDispInfo->item.pszText, pItem->strPassword);
			break;

		case 4: // Type
			string.Format(_T("%u"), pItem->nType);
			::lstrcpy(pDispInfo->item.pszText, string);
			break;
		}
	}

	*pResult = 0;
}
```
### AddItem
```
BOOL CMFCApplication1Dlg::AddItem(int nIndex)
{
	//
	// Allocate a new ITEMINFO structure and initialize it with information
	// about the item.
	//
	ITEMINFO* pItem;
	try {
		pItem = new ITEMINFO;
	}
	catch (CMemoryException* e) {
		e->Delete();
		return FALSE;
	}

	CConnectString *conn = reinterpret_cast<CConnectString *>(this->ListOfConnStrings[nIndex]);

	pItem->strServer = conn->GetServer();
	pItem->strDatabase = conn->GetDb();
	pItem->strUser = conn->GetUser();
	pItem->strPassword = conn->GetPwd();
	pItem->nType = conn->GetType();

	//
	// Add the item to the list view.
	//
	LV_ITEM lvi;
	lvi.mask = LVIF_TEXT | LVIF_PARAM;
	lvi.iItem = nIndex;
	lvi.iSubItem = 0;
	lvi.iImage = 0;
	lvi.pszText = LPSTR_TEXTCALLBACK;
	lvi.lParam = (LPARAM)pItem;

	if (m_ListOfDb.InsertItem(&lvi) == -1)
		return FALSE;

	return TRUE;
}
```

## Ref
- 10.4.3. Sorting in a List View(P649)- Programming Windows With MFC
- [CD-ROM Jeff Prosise MFC 2nd Edition.zip](https://github.com/definedrisk/prosise-mfc2e)
- [ObjArraySerialDemo2.zip](https://mega.nz/file/uYd0GRjY#6nv3hnMd2PdQg4PDaLGI_xR7DHqxow4u2BsbGKJFCoY)
