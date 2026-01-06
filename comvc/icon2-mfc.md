---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Icon - Document/View model"
description: "Minimize the child window to redraw the icon."
date: 2025-11-17
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
If you add a minimize button to your dialog/form, you will need the code below 
 to draw the icon.  For MFC applications using the document/view model, 
 this is automatically done for you by the framework.

### Meet the conditions
- minimize box:
```
Minimize box: True
```
- child window：
```
Style: Child
```

### message map
```
    ON_WM_PAINT()
    ON_WM_QUERYDRAGICON()
```

### query drag icon
- declare
```
afx_msg HCURSOR OnQueryDragIcon();
```
- impl
```
(HCURSOR)m_hIcon;
```

### paint
Draw Icon:
- [IsIconic()](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-isiconic)
- [GetSystemMetrics()](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-getsystemmetrics)
```
    if (IsIconic())
    {
        CPaintDC dc(this); // device context for painting

        int cxIcon = GetSystemMetrics(SM_CXICON);
        int cyIcon = GetSystemMetrics(SM_CYICON);

        CRect rect;
        GetClientRect(&rect);

        int x = (rect.Width() - cxIcon + 1) / 2;
        int y = (rect.Height() - cyIcon + 1) / 2;

        dc.DrawIcon(x, y, m_hIcon);
    }
```

## Ref
- [Icon - Normal Window](https://tdtc-hrb.github.io/com-vc/posts/icon1-mfc)
