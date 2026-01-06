---
layout: ../../layouts/MarkdownPostLayout.astro
title: "GetDlgItem - Cwnd"
description: "Retrieves a pointer to the specified control or child window in a dialog box or other window."
date: 2025-11-02
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- [CWnd Class](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=msvc-170)    
Provides the base functionality of all window classes in the Microsoft Foundation Class Library.
![mfc v9.0](https://learn.microsoft.com/en-us/cpp/mfc/media/vc369r1.png)

#### [cwnd vs hwnd](https://learn.microsoft.com/en-us/cpp/mfc/tn003-mapping-of-windows-handles-to-objects?view=msvc-170)
Given a handle to any one of these objects, 
you can find the MFC object that wraps the handle by calling the static method FromHandle. 
For example, given an HWND called hWnd, the following line will return a pointer to the CWnd that wraps hWnd:
```
CWnd::FromHandle(hWnd)
```
If hWnd does not have a specific wrapper object, a temporary CWnd is created to wrap hWnd. 
This makes it possible to obtain a valid C++ object from any handle.

After you have a wrapper object, you can retrieve its handle from a public member variable of the wrapper class. 
In the case of a CWnd, m_hWnd contains the HWND for that object.

### [CWnd::GetDlgItem](https://learn.microsoft.com/en-us/cpp/mfc/reference/cwnd-class?view=msvc-170#getdlgitem)
```
CWnd* GetDlgItem(int nID) const;

void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```
#### Parameters
- nID    
Specifies the identifier of the control or child window to be retrieved.
- phWnd    
A pointer to a child window.

#### Return Value
A pointer to the given control or child window. 
If no control with the integer ID given by the nID parameter exists, the value is NULL.

The returned pointer may be temporary and shouldn't be stored for later use.

#### Remarks
The pointer returned is usually cast to the type of control identified by nID.

#### Example
```
// uses GetDlgItem to return a pointer to a user interface control
CEdit *pBoxOne;
pBoxOne = (CEdit*)GetDlgItem(IDC_MYEDIT);
GotoDlgCtrl(pBoxOne);
```

## Ref
- [C++ MFC how to use GetDlgItem()](https://stackoverflow.com/a/30512872)
- [MFC class hierarchy chart - v9.0](https://learn.microsoft.com/en-us/cpp/mfc/hierarchy-chart)
- [Microsoft Foundation Class Library - mfcNUM.dll](https://en.wikipedia.org/wiki/Microsoft_Foundation_Class_Library#Versions)
- [Hierarchy Chart Categories](https://learn.microsoft.com/en-us/cpp/mfc/hierarchy-chart-categories)
