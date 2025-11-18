---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Beware of intptr"
description: "signed integer type capable of holding a pointer to void"
date: 2025-11-16
author: xiaobin
tags: ["C++"]
---
The default version uses MSVC >=1930, which is Visual Studio 2022.

- [Why use intptr_t?](https://stackoverflow.com/a/53380316)    
On some platforms pointer types have much larger size than any integral type. 
I believe an example of such as platform would be IBM AS/400 with virtual instruction set defining all pointers as 128-bit. 
A more recent example of such platform would be Elbrus. It uses 128-bit pointers which are HW descriptors rather than normal addresses.

### How do I use it?
- [intptr_t](https://stackoverflow.com/a/35072913)
```
I find intptr_t rather less useful, except possibly as a way station when casting, 
to avoid the dread warning about changing signedness and integer size in the same cast. 
(Writing portable code that passes -Wall -Werror on all relevant architectures can be a bit of a struggle.)
```
- [INT_PTR](https://stackoverflow.com/questions/32931058/what-is-actually-an-int-ptr-and-how-can-i-convert-data-to-int-ptr#comment138483746_32931102)
```
Also, intptr_t is the C99/C++11 standard alternative, but INT_PTR predates them.
```

#### INT_PTR
- <ProjectName>.cpp
> MFC App Wizard
>> Generate dialog-based
```
	INT_PTR nResponse = dlg.DoModal();
	if (nResponse == IDOK)
	{
		// TODO: Place code here to handle when the dialog is
		//  dismissed with OK
	}
	else if (nResponse == IDCANCEL)
	{
		// TODO: Place code here to handle when the dialog is
		//  dismissed with Cancel
	}
	else if (nResponse == -1)
	{
		TRACE(traceAppMsg, 0, "Warning: dialog creation failed, so application is terminating unexpectedly.\n");
		TRACE(traceAppMsg, 0, "Warning: if you are using MFC controls on the dialog, you cannot #define _AFX_NO_MFC_CONTROLS_IN_DIALOGS.\n");
	}
```

### Recommend
- This is closely related to the operating system!
> It's not recommended to use definitions from the operating system when you don't need them!

## Ref
- [MSVC Version](https://en.wikipedia.org/wiki/Microsoft_Visual_C%2B%2B)
- [intptr_t(optional)](https://en.cppreference.com/w/cpp/types/integer.html)
