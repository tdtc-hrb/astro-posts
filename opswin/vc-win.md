---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Desktop development with C++"
description: "Use offline or online installation"
date: 2026-01-25
author: xiaobin
tags: ["Microsoft Visual C++"]
---

### offline
- v18
```
.\VisualStudioSetup.exe --layout D:\v18 `
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.Component.MSBuild `
--add Microsoft.VisualStudio.Component.TextTemplating `
--add Microsoft.VisualStudio.Component.DiagnosticTools `
--add Microsoft.VisualStudio.Component.VC.CoreIde `
--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 `
--add Microsoft.VisualStudio.Component.VC.Redist.14.Latest `
--add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core `
--add Microsoft.VisualStudio.Workload.NativeDesktop `
--add Microsoft.VisualStudio.Component.Windows11SDK.26100 `
--lang en-US
```

## [online](https://visualstudio.microsoft.com/vs/community)
optional: 
- msvc
- Windows SDK

### msvc
- vs2022    
MSVC v143 - VS 2022 C++ x64/x86 build tools(Latest)
- vs2026    
MSVC v145 - x64/x86 build tools(Latest)
