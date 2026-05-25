---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Desktop development with C++"
description: "installation and configuration"
date: 2026-05-21
author: xiaobin
tags: ["Microsoft Visual C++"]
---
Recommendation: 
- Use VS 2026 for development on Windows 10/11 versions higher than 28000; otherwise, use VS 2022.
- Use VS 2019 for Win7/8.1/Win10 version 1511.

|Windows|Latest build|
|-|-|
|26H1|28000.2113|
|24H2|26100.8457|
|21H2|19044.7291|

### Desktop development with C++
- vs2022    
MSVC v143 - VS 2022 C++ x64/x86 build tools(Latest)
- vs2026    
MSVC Build Tools for x64/x86(Latest)
- vs2019    
MSVC v142 - VS 2019 C++ x64/x86 build tools(Latest)

### Windows SDK
- Windows 11 SDK (10.0.28000.1839)
- Windows 11 SDK (10.0.26100.0)
- Windows 10 SDK (10.0.19041.0)

### Windows Driver Kit
Windows 11(Arm) development is supported starting with VS2022.

- Win SDK/WDK 10.0.22621.0
```
Installation of Component.Microsoft.Windows.DriverKit failed. 
The extension has a lower version than required by Visual Studio. 
Please install the extension from Visual Studio Installer instead.
```
You need to install SDK and WDK version 10.0.26100.0.

## configuration
- Cmake

### Cmake - update version
- vs2026
`Tools -> options -> CMake`
checked:
```
Enable custom CMake executable
```
