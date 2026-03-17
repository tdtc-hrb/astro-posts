---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio 2019+的在线下载"
description: "down format and Common"
date: 2025-09-28
author: xiaobin
tags: ["faq2", "Visual Studio Online"]
---
- [vs2017](http://aka.ms/vs/15/release/vs_community.exe)
- [vs2019](http://aka.ms/vs/16/release/vs_community.exe)
- [vs2022](http://aka.ms/vs/17/release/vs_community.exe)

Find components in [workload](https://learn.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools) and add them; 

Take "Microsoft Build Tools" as an example:
```
.\vs_Community.exe --layout D:\win10soft\vs20xx `
--add Microsoft.Component.MSBuild `
--lang en-US
```

### VC
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
