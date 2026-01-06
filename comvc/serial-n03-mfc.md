---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Fundamentals of Dialog Boxes - MFC"
description: "Customize the dialog and call it."
date: 2025-10-29
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

- Properties
- Win Control
- Invoke

### properties
Select the dialog form, then right-click and select "properties":
- Style: Popup
- System Menu: True
- Title Bar: True
- Border: Dialog Frame
- Caption: Port Configuration

### win Control
Drag the Win Control from the Toolbox to the dialog window:
- Group Box
- Combo Box
- Check Box
- Button

### invoke(SerialCommView.cpp)
In the main form's button event.
- head file
```
#include "ConfigDlg.h"
```
- [call it](https://www.functionx.com/visualc/howto/calldlgfromsdi.htm)
```
CConfigDlg* dlg = new CConfigDlg(this);
dlg->DoModal();
```

## Breaking changes
- Visual Studio 2010+    
The class wizard provides CDiaglogEx.

### [CDialogEx](https://www.functionx.com/visualc/Lesson04.htm)
The primary technique used to create a dialog is to derive a class from CDialog. 
To enhance it, Microsoft created a new class named CDialogEx. 
This class is derived from CDialog and it added only two characteristics: a color background and a picture background.
