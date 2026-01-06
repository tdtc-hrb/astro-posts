---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Hello - mfc samples"
description: "Illustrates a single application window with a menu and About box."
date: 2025-11-26
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
This article adds menu events and shortcut key responses in CFrameWnd. 
The modifications are based on the [HelloMFC example](https://tdtc-hrb.github.io/com-vc/posts/hello3-mfc).

### CFrameWnd
- load menu
```
    Create(NULL, _T("Hello MFC"),
        WS_OVERLAPPEDWINDOW,
        rectDefault, 
        NULL, 
        MAKEINTRESOURCE(IDR_MENU1)
    );
```

- [Load Accelerator table](https://stackoverflow.com/a/48791940)
```
LoadAccelTable(MAKEINTRESOURCE(IDR_ACCELERATOR1));
```

### Menu
![add menu](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res6-hellomfc.png)

- event
```
void CMainWindow::OnHelpAboutus()
{
    // TODO: Add your command handler code here
    OnBtnClick();
}
```
![add event](https://github.com/tdtc-hrb/csdn/raw/master/images/add_event1a-hellomfc.png)

![add event](https://github.com/tdtc-hrb/csdn/raw/master/images/add_event2a-hellomfc.png)

### Accelerator
![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res7-hellomfc.png)

![add resource](https://github.com/tdtc-hrb/csdn/raw/master/images/add_res8-hellomfc.png)

#### Key conflict
Remove the message mapping for MyApp.

- MyApp.cpp
```
BEGIN_MESSAGE_MAP(CMyApp, CWinApp)
    ////ON_COMMAND(ID_HELP, &CWinApp::OnHelp)
END_MESSAGE_MAP()
```

## Ref
- [MFC samples - General](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-samples?view=msvc-170#mfc-samples---general)
- [hellomfc2.zip demo](https://mega.nz/file/fEN20B7I#hBoKIkr-MV-WzLLtezv1WvzqbNGPByM67QLo7f1jU6o)
