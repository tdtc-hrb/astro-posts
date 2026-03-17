---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Done Hello - MFC"
description: "A complete Hello demo."
date: 2025-11-14
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

### Add Resource
![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res-hellomfc.png)

#### dialog bar
![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res2-hellomfc.png)

property:
- Style: Popup
- System Menu: True
- Title Bar: True

#### Set Icon
- add picture

![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res3-hellomfc.png)
![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res4-hellomfc.png)

- picture control
> type: Icon
> Image: IDI_ICON1

![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res5-hellomfc.png)

### About Dialog
- add class

![add class](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class1-hellomfc.png)
- add resource head file
```
#include "resource.h"
```

## project
![solution explorer](https://github.com/tdtc-hrb/csdn/raw/master/images/solution-hellomfc.png)

- [HelloMfc.zip](https://mega.nz/file/qEl13IDA#teaFKBqYkohy6jNpMO5MmUwwGi7B0EDJE-I065K2J-E)
### Add Button
- Declare
```
private:
    CButton m_btnAbout;
```
- impl
```
    CRect rt;
    rt.top = 10;
    rt.left = 150;
    rt.right = 250;
    rt.bottom = 30;

    m_btnAbout.Create(_T("About"),
        WS_CHILD | WS_VISIBLE,
        rt,
        this,
        ID_ABOUT); // #define ID_ABOUT 1101
```

### Button Event
- Declare
```
public:
    afx_msg void OnBtnClick();
```
- impl
```
afx_msg void CMainWindow::OnBtnClick()
{
    CAboutDlg dlgAbout;  // #include "AboutDlg.h"
    dlgAbout.DoModal();
}
```

### Add Message Map
- Declare
```
DECLARE_MESSAGE_MAP()
```
- impl
```
BEGIN_MESSAGE_MAP(CMainWindow, CFrameWnd)
    ON_COMMAND(ID_ABOUT, OnBtnClick)
END_MESSAGE_MAP()
```

## Ref
- [First Demo](https://tdtc-hrb.github.io/com-vc/posts/hello1-mfc)
- [Second Demo](https://tdtc-hrb.github.io/com-vc/posts/hello2-mfc)
