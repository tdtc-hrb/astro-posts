---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Using ActiveX Controls"
description: "Copyright belongs to TENUK"
date: 2025-12-05
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Program examples compiled using Visual C++ 9.0 (MFC 9.0) compiler on Windows 2003 machine with Service Pack 2. 

> The minimum available version of Visual Studio is currently(2025.12) VS2008.

### MFC App Wizards
To create a single-document project: Check "ActiveX controls".

![single-document interface](https://github.com/tdtc-hrb/csdn/raw/master/images/sdi-mymfc24.png)

![ActiveX controls](https://github.com/tdtc-hrb/csdn/raw/master/images/image007-mymfc24.png)

![rename classes](https://github.com/tdtc-hrb/csdn/raw/master/images/rename_class-mymfc24.png)

### To install an ActiveX control in a project
Add Class -> MFC Class From ActiveX Control

![Figure 1: Adding ActiveX controls to a project.](https://github.com/tdtc-hrb/csdn/raw/master/images/image001-mymfc24.png)

![Figure 3: A list of all the ActiveX controls currently registered on the system.](https://github.com/tdtc-hrb/csdn/raw/master/images/image003-mymfc24.png)

#### Microsoft Calendar Control
MSCAL.OCX is the Microsoft Calendar Control. It hasn't been included in Access 2010 and later versions.

|office|version|
|-|-|
|2007|12|
|2003|11|
|xp|10|
|2000|9|
|97|8|

from [Can't open MS Access database - error msg "missing or broken reference to "MSCAL.OCX" version 7.0](https://learn.microsoft.com/en-us/answers/questions/5080576/cant-open-ms-access-database-error-msg-missing-or)

## ActiveX
Microsoft Visual Basic (VB) was introduced in 1991 and has proven to be a wildly popular and successful application development system for Microsoft Windows. 
Part of its success is attributable to its open-ended nature. 
The 16-bit versions of VB (versions 1 through 3) supported Visual Basic controls (VBXs), 
ready-to-run software components that VB developers could buy or write themselves. 
VBXs became the center of a whole industry, and pretty soon there were hundreds of them. 
At Microsoft, the Microsoft Foundation Class (MFC) team figured out a way for Microsoft Visual C++ programmers to use VBXs in their programs, too.

Now ActiveX Controls (formerly known as Object Linking and Embedding (OLE) controls or OCXs) are the industrial-strength replacement 
for VBXs based on Microsoft Component Object Model (COM) technology. ActiveX controls can be used by application developers in both VB and Visual C++ 6.0. 
While VBXs were written mostly in plain C, ActiveX controls can be written in C++ with the help of the MFC library or with the help of the ActiveX Template Library (ATL). 
This module is not about writing ActiveX controls; it's about using them in a Visual C++ application. 

### How ActiveX Controls Are Similar to Ordinary Controls
You can consider an ActiveX control to be a child window, just as an ordinary control is. 
If you want to include an ActiveX control in a dialog, you use the dialog editor to place it there, and the identifier for the control turns up in the resource template. 
If you're creating an ActiveX control on the fly, you call a Create() member function for a class that represents the control, 
usually in the WM_CREATE handler for the parent window. When you want to manipulate an ActiveX control, you call a C++ member function, 
just as you do for a Windows control. The window that contains a control is called a container.

### How ActiveX Controls Are Different from Ordinary Controls: Properties and Methods
The most prominent ActiveX Controls features are properties and methods. 
Those C++ member functions that you call to manipulate a control instance all revolve around properties and methods. 
Properties have symbolic names that are matched to integer indexes. For each property, the control designer assigns a property name, 
such as BackColor or GridCellEffect, and a property type, such as string, integer, or double. 
There's even a picture type for bitmaps and icons. The client program can set an individual ActiveX control property by specifying the property's integer index and its value. 
The client can get a property by specifying the index and accepting the appropriate return value. 
In certain cases, ClassWizard lets you define data members in your client window class that are associated with the properties of the controls the client class contains. 
The generated Dialog Data Exchange (DDX) code exchanges data between the control properties and the client class data members.

ActiveX Controls methods are like functions. A method has a symbolic name, a set of parameters, and a return value. 
You call a method by calling a C++ member function of the class that represents the control. 
A control designer can define any needed methods, such as PreviousYear(), LowerControlRods(), and so forth.

An ActiveX control doesn't send WM_ notification messages to its container the way ordinary controls do; instead, 
it "fires events." An event has a symbolic name and can have an arbitrary sequence of parameters; it's really a container function that the control calls. 
Like ordinary control notification messages, events don't return a value to the ActiveX control. Examples of events are Click, KeyDown, and NewMonth. 
Events are mapped in your client class just as control notification messages are. In the MFC world, ActiveX controls act just like child windows, 
but there's a significant layer of code between the container window and the control window. In fact, the control might not even have a window. 
When you call Create(), the control's window isn't created directly; instead, the control code is loaded and given the command for "in-place activation." 
The ActiveX control then creates its own window, which MFC lets you access through a CWnd pointer. 
It's not a good idea for the client to use the control's hWnd directly, however. A DLL is used to store one or more ActiveX controls, 
but the DLL often has an OCX filename extension instead of a DLL extension. Your container program loads the DLLs when it needs them, 
using sophisticated COM techniques that rely on the Windows Registry. 
For the time being, simply accept the fact that once you specify an ActiveX control at design time, it will be loaded for you at runtime. 
Obviously, when you ship a program that requires special ActiveX controls, you'll have to include the OCX files and an appropriate setup program.

## Ref
- [Module 18: Using ActiveX Controls 1](https://www.tenouk.com/visualcplusmfc/visualcplusmfc18.html)
- [Module 18: Using ActiveX Controls 2](https://www.tenouk.com/visualcplusmfc/visualcplusmfc18a.html)
- [Module 18 - demo](https://www.tenouk.com/mfcproject/mymfc24)
