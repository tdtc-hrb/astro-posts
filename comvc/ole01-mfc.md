---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ActiveX controls"
description: "MFC support for ActiveX"
date: 2025-12-04
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
For DLLs and ActiveX (formerly OLE) controls, 
CProjNameApp::InitInstance registers the control's object factory with OLE by calling COleObjectFactory::RegisterAll and makes a call to AfxOLEInit. 
In addition, the member function CProjNameApp::ExitInstance is used to unload the control from memory with a call to AfxOleTerm.

### afxole
When I used AppWizard to create the Widget project, I selected none of the OLE options in Step 3. 
When AppWizard is run this way, the generated source code doesn't include a call to the all-important AfxOleInit function, 
which initializes the OLE libraries. 
This function must be called before an MFC application touches COM or OLE in any way. 
Therefore, I added a call to AfxOleInit to the beginning of the application class's InitInstance function. 
This meant that I also had to add the statement
```
#include <afxole.h>
```
to Stdafx.h. Otherwise, the call to AfxOleInit wouldn't have compiled.

I mention this because if you write an application that uses COM or OLE but you don't select one of the OLE options in 
AppWizard, you must add the AfxOleInit call and the statement that <i>#includes Afxole.h</i> manually. 
If you don't, your application will compile just fine, 
but calls to functions such as <i>COleDataSource::DoDragDrop</i> will fail. 
I once lost half a day of work wondering why my clipboard code wasn't working 
when, by all appearances, I had done everything right. 
Then I realized that I had forgotten to include these crucial statements in my source code. 
If you write an application and find that calls to DoDragDrop or other OLE functions mysteriously fail, 
make sure that AfxOleInit is called when the application starts up. You'll save yourself a lot of grief.

### InitInstance
```
    // Initialize OLE libraries
    if (!AfxOleInit())
    {
        AfxMessageBox(IDP_OLE_INIT_FAILED);
        return FALSE;
    }

    AfxEnableControlContainer();
```

#### AfxEnableControlContainer
Call this function in your application object's InitInstance function to enable support for containment of OLE controls.

### ExitInstance
```
    //TODO: handle additional resources you may have added
    AfxOleTerm(FALSE);
```

## Ref
- [OLE Initialization](https://learn.microsoft.com/en-us/cpp/mfc/reference/ole-initialization?view=msvc-170)
- [MFC Program or Control Source and Header Files](https://learn.microsoft.com/en-us/cpp/build/reference/mfc-program-or-control-source-and-header-files?view=msvc-170)
