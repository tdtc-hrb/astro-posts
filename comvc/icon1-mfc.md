---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Icon - Normal Window"
description: "Simple application of afxApp()"
date: 2025-11-17
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The handle needs to be obtained in the constructor; the icon is set in the subsequent call.
For example, in InitUpdate() or InitDialog().

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
#### [AfxGetApp](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwinapp-class?view=msvc-170#remarks)
Obtains a pointer to the CWinApp object.

#### LoadIcon
[Loads an icon resource.](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwinapp-class?view=msvc-170#loadicon)
```
HICON LoadIcon(LPCTSTR lpszResourceName) const;
HICON LoadIcon(UINT nIDResource) const;
```

### set icon
- [SetIcon](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=msvc-170#public-methods)
```
SetIcon(m_hIcon, TRUE);         // Set big icon
SetIcon(m_hIcon, FALSE);        // Set small icon
```
