---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Q&A"
description:  "Code used in the driver"
date: 2026-05-31
author: "tdtc"
---

### [PAGED_CODE](https://learn.microsoft.com/en-us/windows-hardware/drivers/kernel/paged_code)
A call to this macro should be made at the beginning of every driver routine 
that either contains pageable code or accesses pageable code.

### [UNREFERENCED_PARAMETER](https://learn.microsoft.com/en-us/archive/msdn-magazine/2005/may/c-at-work-unreferenced-parameters-adding-task-bar-commands)
At Level 4(W4):
```
int SomeFunction(int arg1, int arg2) { return arg1+5; }
```
With ·/W4·, the compiler complains: <code>"warning C4100: 'arg2' : unreferenced formal parameter."</code> 
To fool the compiler: 
```
int SomeFunction(int arg1, int arg2) { UNREFERENCED_PARAMETER(arg2); return arg1+5; }
```
Now your function references arg2 so the compiler will shut up.

### EXTERN_C_START and EXTERN_C_END
- When compiled in C++ (__cplusplus is defined): The pre-processor translates EXTERN_C_START to extern "C" { and EXTERN_C_END to }. 
This informs the C++ compiler to disable name mangling for those functions.
- When compiled in C (__cplusplus is not defined): The pre-processor defines both as empty (no-op), 
allowing the code to compile cleanly without encountering the extern "C" syntax, which C does not understand.

### ALLOC_PRAGMA
wdm.h:
```
#define ALLOC_PRAGMA 1
```
Indicate that the AMD64 compiler supports the allocate pragmas.

### [alloc_text](https://learn.microsoft.com/en-us/cpp/preprocessor/alloc-text)
The alloc_text pragma doesn't handle C++ member functions or overloaded functions. 
It's applicable only to functions declared with C linkage, 
that is, functions declared with the extern "C" linkage specification. 
If you attempt to use this pragma on a function with C++ linkage, a compiler error is generated.
