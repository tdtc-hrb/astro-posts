---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Desktop development with C++"
description: "Use offline or online installation"
date: 2025-09-30
author: xiaobin
tags: ["Microsoft Visual C++"]
---

### offline
- vs17/vs16
```
.\vs_community.exe --layout D:\v17v16 `
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.VisualStudio.Component.TextTemplating `
--add Microsoft.Component.MSBuild `
--add Microsoft.VisualStudio.Component.VC.CoreIde `
--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 `
--add Microsoft.VisualStudio.Component.VC.Redist.14.Latest `
--add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core `
--add Microsoft.VisualStudio.Workload.NativeDesktop `
--add Microsoft.VisualStudio.Component.Windows10SDK.19041 `
--lang en-US
```

#### vs15
```
.\vs_community.exe --layout D:\v15 `
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.Component.MSBuild `
--add Microsoft.VisualStudio.Component.Static.Analysis.Tools `
--add Microsoft.VisualStudio.Component.TextTemplating `
--add Microsoft.VisualStudio.Component.VC.CoreIde `
--add Microsoft.VisualStudio.Component.VC.Redist.14.Latest `
--add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core `
--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 `
--add Microsoft.Component.VC.Runtime.UCRTSDK `
--add Microsoft.VisualStudio.Component.Windows81SDK `
--add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 `
--add Microsoft.VisualStudio.Workload.NativeDesktop `
--lang en-US
```

## [online](https://visualstudio.microsoft.com/vs/community)
optional: 
- msvc
- Windows SDK

### msvc
- vs2017    
VC++ 2017 version 15.9 v14.16 latest v141 tools
- vs2019    
MSVC v142 - VS 2019 C++ x64/x86 build tools(Latest)
- vs2022    
MSVC v143 - VS 2022 C++ x64/x86 build tools(Latest)
- vs2026    
MSVC v145 - x64/x86 build tools(Latest)

### Win SDK
- vs2017    
Windows 8.1 SDK and UCRT SDK
- vs2019    
Windows 10 SDK(10.0.19041.0)
- vs2022    
Windows 11 SDK(10.0.22621.0)
- vs2026    
Windows 11 SDK(10.0.26100.x)
