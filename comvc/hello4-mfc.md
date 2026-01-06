---
layout: ../../layouts/MarkdownPostLayout.astro
title: "HelloApp - mfc samples"
description: "Minimal MFC sample that illustrates that few lines of code are required to get a window to appear on the screen."
date: 2025-11-25
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The default is to use CFrameWnd!

### [Create method](https://learn.microsoft.com/en-us/cpp/mfc/reference/cframewnd-class?view=msvc-170#create)
```
Create(NULL, _T("Hello World!"), WS_OVERLAPPEDWINDOW, rectDefault);
```
- [dwStyle](https://learn.microsoft.com/en-us/cpp/mfc/reference/styles-used-by-mfc?view=msvc-170#window-styles)
- rect
Specifies the size and position of the window. 
The <i>rectDefault</i> value allows Windows to specify the size and position of the new window.


## CWnd
[Use CreateEx() to customize special windows.](https://stackoverflow.com/questions/26984816/how-to-create-a-hidden-window-by-extending-cwnd-class-in-visual-c)

### [AfxRegisterWndClass](https://learn.microsoft.com/en-us/cpp/mfc/tn001-window-class-registration?view=msvc-170#the-afxregisterwndclass-function)
```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```
- [hbrBackground](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-getsyscolor#windows-1011-system-colors)
```
COLOR_WINDOW+1 = COLOR_WINDOWFRAME
```

### [LoadCursor](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-loadcursora)
- [lpCursorName](https://learn.microsoft.com/en-us/windows/win32/menurc/about-cursors)

### [CreateEx method](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=msvc-170#createex)
```
        CreateEx(WS_EX_CLIENTEDGE,
            AfxRegisterWndClass(0, ::LoadCursor(NULL, IDC_ARROW), (HBRUSH)(COLOR_WINDOW+1)),
            _T("Hello-World!"), WS_OVERLAPPEDWINDOW,
            CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT, NULL, NULL, 0);
```
- [dwExStyle](https://learn.microsoft.com/en-us/cpp/mfc/reference/styles-used-by-mfc?view=msvc-170#extended-window-styles)
- [x, y, nWidth, nHeight](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-createwindowa#parameters)
```
CW_USEDEFAULT is valid only for overlapped windows; 
if it is specified for a pop-up or child window, the x and y parameters are set to zero.
```

## Ref
- [MFC samples - General](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-samples?view=msvc-170#mfc-samples---general)
- [My first mfc application](https://tdtc-hrb.github.io/com-vc/posts/hello1-mfc)
