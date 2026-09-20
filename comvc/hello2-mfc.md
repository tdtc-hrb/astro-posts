---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The Message Map"
description: "add F1 feature"
date: 2025-11-13
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The message map is MFC's way of avoiding the lengthy <i>vtables</i> that would be required 
if every class had a virtual function for every possible message it might receive. 
Any class derived from CCmdTarget can contain a message map.

1. Declare the message map by adding a DECLARE_MESSAGE_MAP statement to the class declaration.    
2. Implement the message map by placing macros identifying the messages that the class will handle 
between calls to BEGIN_MESSAGE_MAP and END_MESSAGE_MAP.    
3. Add member functions to handle the messages.

- declare
```
DECLARE_MESSAGE_MAP()
```
- impl
```
BEGIN_MESSAGE_MAP(CMyApp, CWinApp)
    ON_COMMAND(ID_HELP, &CWinApp::OnHelp)
END_MESSAGE_MAP()
```
#### [begin message map](https://learn.microsoft.com/en-us/cpp/mfc/reference/message-map-macros-mfc?view=msvc-170#begin_message_map)
```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```
Parameters:
- theClass
```
Specifies the name of the class whose message map this is.
```
- baseClass
```
Specifies the name of the base class of theClass.
```

### Modify CMyApp
> MyApp.cpp

- OnHelp()
```
#include "stdafx.h"
```
Copy stdafx.h and targetver.h to the project directory.
#### afxwin
> MyApp.h

Use 
```
#ifndef __AFXWIN_H__
    #error "include 'stdafx.h' before including this file for PCH"
#endif
```
instead of 
```
#include <afxwin.h>
```

## Ref
- [Message Map Macros (MFC)](https://learn.microsoft.com/en-us/cpp/mfc/reference/message-map-macros-mfc)
- [Second MFC - demo](https://mega.nz/file/qMt2lYhT#WWIbuyYjfYr4QWOEDP1AYyU3eabjyj9oP1eMvKdLikA)
