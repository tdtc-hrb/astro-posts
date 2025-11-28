---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Scroll Views"
description: "CScrollView adds basic scrolling capabilities to CView."
date: 2025-11-29
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
CScrollView adds basic scrolling capabilities to CView. 
It includes handlers for WM_VSCROLL and WM_HSCROLL messages that allow MFC to do the bulk of the work involved in scrolling a window 
in response to scroll bar messages. 
It also includes member functions that you can call to perform fundamental tasks such as scrolling to a specified position and 
retrieving the current scroll position. 
Because CScrollView handles scrolling entirely on its own, 
you have to do very little to make it work other than implement OnDraw. 
You can usually implement OnDraw in a CScrollView exactly as you do in a CView. 
Unless you want to tweak it to optimize scrolling performance, 
OnDraw requires little or no special logic to support scrolling.

1. Derive your application's view class from CScrollView. 
If you use AppWizard to create the project, you can select CScrollView from the list 
of base classes presented in AppWizard's Step 6 dialog box, as shown in Figure 10-1.

![Using AppWizard to create a CScrollView-based application](https://github.com/tdtc-hrb/csdn/raw/master/images/figure_10.1-spread.png)

2. Override OnInitialUpdate in the view class, and call SetScrollSizes to specify the view's logical dimensions. 
This is your means of telling MFC how large an area the scrollable view should cover. 
If you use AppWizard to create the project and choose CScrollView in the Step 6 dialog box, 
AppWizard overrides OnInitialUpdate for you and inserts a call to SetScrollSizes that sets the view's logical width and height to 100 pixels.

3. Implement OnDraw as if the view were a conventional CView.

### Demo
The demo program is missing a variable type definition—`int`.

Adding `int` will solve the problem:
- row
```
    //
    // Add numbers and button outlines to the row headers.
    //
    for (int i=0; i<19; i++) {
        // some code
    }
```
- column
```
    //
    // Add letters and button outlines to the column headers.
    //
    for (int j=0; j<26; j++) {
        // some code here
    }
```
- cell
```
    //
    // Draw address labels into the individual cells.
    //
    CRect rect;
    pDC->GetClipBox (&rect);
    // other code here
    int nEndRow = min (18, (rect.bottom - 1) / m_nCellHeight);
    // other code here
    
    for (int i=nStartRow; i<=nEndRow; i++)
        for (int j=nStartCol; j<=nEndCol; j++)
            DrawAddress (pDC, i, j);
```

## Ref
- [10.1. Scroll Views(P600)- Programming Windows With MFC](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
- [CD-ROM Jeff Prosise MFC 2nd Edition.zip](https://github.com/definedrisk/prosise-mfc2e)
