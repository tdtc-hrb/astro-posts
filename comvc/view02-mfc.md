---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Tree Views"
description: "Wraps the tree view control"
date: 2025-12-02
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
CTreeCtrl and CTreeView: 
- One uses a variable directly
```
m_myTreeCtl
```
- the other uses <i>GetTreeCtrl()</i>    
[MyExplorer2.1.zip - demo](https://mega.nz/file/fAV2lKKQ#VYrrg0MFeJv9FqjfW1siLi53LmaJMQlpZwDUbhCGPqo)

### Set New Style
- Direct settings
- Indirect setting

default value:
- TVS_HASBUTTONS
- TVS_HASLINES
- TVS_LINESATROOT

#### Direct settings
```
    GetTreeCtrl().ModifyStyle(0, TVS_HASBUTTONS);
    GetTreeCtrl().ModifyStyle(0, TVS_HASLINES);
    GetTreeCtrl().ModifyStyle(0, TVS_LINESATROOT);
```
#### Indirect settings
First obtain the handle, then set the Tree-View Control Window Styles.
```
void CLeftView::SetNewStyle(long lStyleMask, BOOL bSetBits)
{
    long        lStyleOld;

    lStyleOld = GetWindowLongPtr(GetTreeCtrl().GetSafeHwnd(), GWL_STYLE);

    lStyleOld &= ~lStyleMask;
    if (bSetBits)
        lStyleOld |= lStyleMask;

    SetWindowLongPtr(GetTreeCtrl().GetSafeHwnd(), GWL_STYLE, lStyleOld);
    SetWindowPos(NULL, 0, 0, 0, 0, SWP_NOMOVE | SWP_NOSIZE | SWP_NOZORDER);
}
```
The example comes from "[hyun](https://stackoverflow.com/a/21140319)" 
and "[CMyTreeCtrl::SetNewStyle](https://github.com/microsoft/VCSamples/blob/9e1d4475555b76a17a3568369867f1d7b6cc6126/VC2010Samples/MFC/general/CmnCtrl1/mtreectl.cpp#L61)"

### data mgr - insert
```
    for (iItem = 0; iItem < sizeof(strItems) / sizeof(strItems[0]); iItem++)
    {
        curTreeItem.hParent = (iItem % 4 == 0)? NULL : m_rghItem[iItem / 4 * 4];
        curTreeItem.hInsertAfter = TVI_SORT;
        curTreeItem.item.iImage = iItem / 4 * 2;
        curTreeItem.item.iSelectedImage = curTreeItem.item.iImage + 1;
        curTreeItem.item.pszText = strItems[iItem].GetBuffer(strItems[iItem].GetLength());
        curTreeItem.item.mask = TVIF_IMAGE | TVIF_SELECTEDIMAGE | TVIF_TEXT;
        m_rghItem[iItem] = GetTreeCtrl().InsertItem(&curTreeItem);
    }
```
#### data
```
    HTREEITEM   m_rghItem[12];

    CString             strItems[12];
    int                 iItem;
    TV_INSERTSTRUCT     curTreeItem;

    strItems[0] = _T("Dogs");
    strItems[1] = _T("German Shepherd");
    strItems[2] = _T("Dalmatian");
    strItems[3] = _T("Great Dane");
    strItems[4] = _T("Birds");
    strItems[5] = _T("Hummingbird");
    strItems[6] = _T("Pigeon");
    strItems[7] = _T("Eagle");
    strItems[8] = _T("Fish");
    strItems[9] = _T("Snapper");
    strItems[10] = _T("Sole");
    strItems[11] = _T("Salmon");
```

## Ref
- [10.3. Tree Views(P626)- Programming Windows With MFC](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
- [CD-ROM Jeff Prosise MFC 2nd Edition.zip](https://github.com/definedrisk/prosise-mfc2e)
- [CTreeCtrl Class](https://learn.microsoft.com/en-us/cpp/mfc/reference/ctreectrl-class?view=msvc-170)
- [Tree-View Control Window Styles](https://learn.microsoft.com/en-us/windows/win32/Controls/tree-view-control-window-styles)
- [TVINSERTSTRUCTW structure](https://learn.microsoft.com/en-us/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw)
- [TVITEMA structure](https://learn.microsoft.com/en-us/windows/win32/api/commctrl/ns-commctrl-tvitema)
- [MFC Sample CMNCTRL1](https://github.com/microsoft/VCSamples/tree/master/VC2010Samples/MFC/general/CmnCtrl1)
