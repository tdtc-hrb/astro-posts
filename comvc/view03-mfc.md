---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Splitter Windows"
description: "The left view is a tree view; the right view is a list view."
date: 2025-11-27
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
MFC supports two types of splitter windows: static and dynamic. 

### splitter window - dynamic
Dynamic splitter windows are created with MFC's CSplitterWnd::Create function. 
Creating and initializing a dynamic splitter window is a simple two-step procedure: 
1. Add a CSplitterWnd data member to the frame window class. 
2. Override the frame window's virtual OnCreateClient function, 
and call CSplitterWnd::Create to create a dynamic splitter window in the frame window's client area.

### splitter window - static
The procedure for adding a static splitter window to a frame window goes like this.
1. Add a CSplitterWnd data member to the frame window class.
2. Override the frame window's OnCreateClient function, and call CSplitterWnd::CreateStatic to create a static splitter window.
3. Use CSplitterWnd::CreateView to create a view in each of the splitter window's panes.

![Using AppWizard to create an Explorer-style application.](https://github.com/tdtc-hrb/csdn/raw/master/images/figure_11.9-wanderer.png)

![(Before changes) Default items](https://github.com/tdtc-hrb/csdn/raw/master/images/default-wanderer.png)

![list view - right](https://github.com/tdtc-hrb/csdn/raw/master/images/rightview-wanderer.png)

![tree view - left](https://github.com/tdtc-hrb/csdn/raw/master/images/leftview-wanderer.png)


## Ref
- [11.2. Splitter Windows(P696) - Programming Windows With MFC](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
