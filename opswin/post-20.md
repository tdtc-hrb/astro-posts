---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Desktop development with C++"
description: "Use offline or online installation"
date: 2025-08-24
author: xiaobin
tags: ["Microsoft Visual C++"]
---

### offline
```
.\VisualStudioSetup.exe --layout D:\v17.14 `
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

### [online](https://visualstudio.microsoft.com/vs/community)
optional: 
- MSVC v143 - VS 2022 C++ x64/x86 build tools(Latest)
- vcpkg package manager
- Windows 10 SDK(10.0.19041.0)
