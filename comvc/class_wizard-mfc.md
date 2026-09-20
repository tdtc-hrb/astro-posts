---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Tools to Manage Projects: The MFC Class Wizard"
description: "Used to manage window controls."
date: 2025-12-12
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The MFC Class Wizard is a dialog box that can be used to create and manage classes of a project. 
The classes must use, or inherit from, MFC existing classes. There are various ways you can access the MFC Class Wizard:

- At any time on the menu, you can click Project -> Class Wizard...
- In the Solution Explorer,  right-click the name of the project or the name of a folder, and click Class Wizard...
- In the Class View, right-click the name of the project or the name of a class, and click Class Wizard...
- In the Resourve View, right-click the name of the project and click Class Wizard
- If a dialog box (or a form) being designed is displaying in the middle area, right-click it (or any object on it) and click Class Wizard

### A Description of the MFC Class Wizard
- Commands
- Messages
- Virtual Functions

Each tab is equipped with some buttons on the right side. 
The usefulness and behavior of these buttons depend on what is selected on the left list(s) of the same tab.
#### Commands
The Commands tab displays a list of the objects (such as Windows controls) that are positioned on, or are accessible to, the Class Name object:

![Based on dialog box](https://github.com/tdtc-hrb/csdn/raw/master/images/commands-class_wizard.png)

We will come back to this tab when we study the Windows controls.

#### Messages
The Messages tab holds a list of the Windows messages available to the Class Name and inherited from the Base Class:

![Based on dialog box](https://github.com/tdtc-hrb/csdn/raw/master/images/messages-class_wizard.png)

#### Virtual Functions
The Virtual Functions tab displays a list of member functions available to the Class Name. 
The Member Variables section shows a list of the objects positioned on the dialog box. 
We will come back to it. The Methods property page has the methods that have already been created in the Class Name.

## Ref
- [The MFC Class Wizard](https://www.functionx.com/visualc/studio/mcw.htm)
