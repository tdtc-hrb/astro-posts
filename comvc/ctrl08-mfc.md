---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Sorting in a List Control - arrows"
description: "Add down arrows and up arrows"
date: 2025-12-15
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Based on the content of article number "[Sorting in a List Control](https://tdtc-hrb.github.io/com-vc/posts/ctrl07-mfc)".
```
void CMFCApplication1Dlg::SetSortArrow(int colIndex, bool ascending)
{
	for (int i = 0; i < m_ListOfDb.GetHeaderCtrl()->GetItemCount(); ++i)
	{
		HDITEM hditem = { 0 };
		hditem.mask = HDI_FORMAT;
		VERIFY(m_ListOfDb.GetHeaderCtrl()->GetItem(i, &hditem));
		hditem.fmt &= ~(HDF_SORTDOWN | HDF_SORTUP);
		if (i == colIndex)
		{
			hditem.fmt |= ascending ? HDF_SORTDOWN : HDF_SORTUP;
		}
		VERIFY(m_ListOfDb.GetHeaderCtrl()->SetItem(i, &hditem));
	}
}
```

- invoke
```
void CMFCApplication1Dlg::OnLvnColumnclickList2(NMHDR *pNMHDR, LRESULT *pResult)
{
	LPNMLISTVIEW pNMLV = reinterpret_cast<LPNMLISTVIEW>(pNMHDR);
	// TODO: Add your control notification handler code here
	int colIndex = pNMLV->iSubItem;

	if (m_SortCol == colIndex)
	{
		m_Ascending = !m_Ascending;
	}
	else
	{
		m_SortCol = colIndex;
		m_Ascending = true;
	}

	BOOL bSort = m_ListOfDb.SortItems(CompareFunc, pNMLV->iSubItem);
	if (bSort)
		//SetSortArrow(m_SortCol, m_Ascending);
		SetSortArrow(m_SortCol, TRUE);			//// Only ASC ICON
	*pResult = 0;
}
```

## Ref
- [CListCtrl and sorting rows](https://www.codeproject.com/articles/CListCtrl-and-sorting-rows)
- [ObjArraySerialDemo2.1.zip](https://mega.nz/file/mYcVzBiB#dHC3dYMfYALxM3qVtyRhHaylpEhjQJQH0h-07qWxNFg)
