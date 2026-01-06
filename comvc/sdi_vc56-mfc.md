---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Create a single-document project using the MFC App Wizard in VC++ 5.0/6.0"
description: "Using VC 5.0/6.0"
date: 2025-11-18
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- Visual C++ 5.0/6.0
- Windows 2003 R2
- VirtualBox / VMware workstation

### The Architecture
Supporting the coordination of application data and data renderings is a perfect job 
for a framework. And when Microsoft released MFC 2.0 in early 1993, it included a document/view 
architecture within MFC. MFC's document/view architecture deals with the data management and 
User-Interface issues just described.

As an aside, MFC's document/view is not a new idea. It was first created by the folks at Xerox PARC (by the 
same company that invented graphical user interface) and was a key part of ther Smalltalk environment. 
Smalltalk's version of document/view is called model-view-controller(MVC)(where model=document). The Smalltalk 
MVC architecture has a controller(kind of like CDocTemplate in MFC) that acts like a shield between the document 
and the view so that they do not get too dependent on each other.

### class diagram
![Figure 12-3](https://github.com/tdtc-hrb/csdn/raw/master/images/figure12.3-vc12.png)
Image source: Beginning Visual C++ 2013

## project
```
name: SdiSquares
vc56: Images compatible with both VC 5.0 and VC 6.0
vc5/6: The left side is VC 5.0; the right side is VC 6.0.
```
![new project - vc6.0](https://github.com/tdtc-hrb/csdn/raw/master/images/new_project-vc6.png)

- step 1

![single document - vc5.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard1a-vc5.png)
![single document- vc6.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard1a-vc6.png)
- step 2

![database support](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard2a-vc56.png)
- step 3

![compound - vc5.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard3a-vc5.png)
![compound- vc6.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard3a-vc6.png)
- step 4

![menu - vc5.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard4a-vc5.png)
![menu- vc6.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard4a-vc6.png)

![loc](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard4a1-vc56.png)
- step 5

![comments - vc5.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard5a-vc5.png)
![comments- vc6.0](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard5a-vc6.png)
- step 6:
modify class and file name:
```
CSquaresApp
CSquaresDoc
CSquaresView
SquaresDoc
SquaresView
```
![CSquaresApp](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard6a-vc56.png)

![CSquaresDoc](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard6b-vc56.png)

![CSquaresView](https://github.com/tdtc-hrb/csdn/raw/master/images/mfc_app_wizard6c-vc56.png)

## Ref
- Chapter 7: MFC's Document/View Architecture - MFC Internals
- [Create a single-document project using the MFC App Wizard in VC++ 12.0 (Visual Studio 2013)](https://www.cnblogs.com/xiaobin-hlj80/p/19191031)
