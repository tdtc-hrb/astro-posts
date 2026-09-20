---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Change the default ATL project properties in VC"
description: "ATL project"
date: 2026-02-19
author: "tdtc"
---


## Change the default project properties
- MSB8011
> RegisterOutput
### RegisterOutput
```
Linker: Register Output为 “No”；
```
#### x64 for vs2022+
```
Linker -> All Options -> 
Register Output: No
```

### UseOfAtl
```
General -> Use of ATL
Not Using ATL
```

### SDLCheck
```
C/C++ -> SDL checks
Use the backspace key to delete.
```
Microsoft's SDL solution here in contrast is not portable, nor is it safe.


## runtime exception
- ucrt
### ucrt
仅安装ucrt（通用Windows sdk）会出现：
```bash
  cannot find the resource compiler dll. please make sure the path is correct.
```
解决办法：    
安装Windows 8.1/Windows 10 SDK

### c-sharp exception
```
System.Runtime.InteropServices.COMException (0x80040154): 
Retrieving the COM class factory for component with CLSID 
{7A6E7413-F0E2-41B8-9BB7-036229C90FE5} failed due to the following 
error: 80040154 Class not registered (Exception from HRESULT: 0x80040154 (REGDB_E_CLASSNOTREG)).
```
A: vs高版本已经使用[32/64位](https://stackoverflow.com/a/4664073)    
It means the class id 877AA945-1CB2-411C-ACD7-C70B1F9E2E32 is not in the registry.

You can verify this by opening regedit.exe, browsing to HKEY_CLASSES_ROOT\CLSID\{877AA945-1CB2-411C-ACD7-C70B1F9E2E32}.    
If your running a 32-bit app on a 64 bit OS, look for HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{877AA945-1CB2-411C-ACD7-C70B1F9E2E32}

If it is there, it may be some other issue but it is probably missing.    
To resolve this you will usually run the installer that distributes this COM object.    
If you don't have one and you know what dll implements the object, you can run regsvr32.exe (or regasm.exe for a managed dll).


## Ref
- [Don't expect too much from it - SDL](https://stackoverflow.com/a/18309123)
- [Changes to Project Templates and Code Wizards in 15.3](https://devblogs.microsoft.com/cppblog/changes-to-project-templates-and-code-wizards-in-15-3/)
