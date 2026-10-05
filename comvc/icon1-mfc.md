---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Icon - Normal Window"
description: "Simple application of afxApp()"
date: 2025-11-17
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- The handle needs to be obtained in the constructor; 
- the icon is set in the subsequent call.
```
For example, in InitUpdate() or InitDialog().
```

### handle
- Declare
```
protected:
    HICON m_hIcon;
```
- Get handle
```
m_hIcon = AfxGetApp()->LoadIcon(IDI_ICON1);
```

### set icon
```
SetIcon(m_hIcon, TRUE);         // Set big icon
SetIcon(m_hIcon, FALSE);        // Set small icon
```

## Ref
- [AfxGetApp](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwinapp-class?view=msvc-170#remarks)
- [Loads an icon resource](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwinapp-class?view=msvc-170#loadicon)
- [SetIcon](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=msvc-170#public-methods)
