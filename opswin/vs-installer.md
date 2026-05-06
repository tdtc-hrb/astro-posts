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

### EOL
|name|eol - Official|
|-|-|
|Visual Studio 2019|April 2029|
|Visual Studio 2017|April 2027|

#### 32-bit
NOTE: Visual Studio 2019 (16.11.55) now ships with the updated NodeJS version 22, specifically 22.21.1. 
It's worth noting that NodeJS 22.x will be the final release supporting 32-bit NodeJS development, 
marking the end of an era for those using 32-bit platforms.

NodeJS 22.x is scheduled to reach End Of Life in April 2027.

#### win7
Earlier versions of Visual Studio 2017 could be installed on Windows 7.

[The latest version no longer supports this.](https://www.reddit.com/r/VisualStudio/comments/1nzzt4p/is_windows_7_no_longer_supported_for_visual_studio/)

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
### fx
- v16
```
.\vs_Community.exe --layout D:\vs2019 `
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.Component.MSBuild `
--add Microsoft.VisualStudio.Component.TextTemplating `
--add Microsoft.VisualStudio.Component.IntelliCode `
--add Microsoft.VisualStudio.Component.Debugger.JustInTime `
--add Microsoft.VisualStudio.Component.NuGet `
--add Microsoft.Net.Component.4.6.1.TargetingPack `
--add Microsoft.VisualStudio.Component.Roslyn.LanguageServices `
--add Microsoft.VisualStudio.Component.FSharp `
--add Microsoft.ComponentGroup.ClickOnce.Publish `
--add Microsoft.NetCore.Component.DevelopmentTools `
--add Microsoft.Net.Component.4.8.SDK `
--add Microsoft.Net.Component.4.7.2.TargetingPack `
--add Microsoft.Net.ComponentGroup.DevelopmentPrerequisites `
--add Microsoft.VisualStudio.Component.ManagedDesktop.Core `
--add Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites `
--add Microsoft.VisualStudio.Workload.ManagedDesktop `
--add Microsoft.Net.Component.4.5.2.TargetingPack `
--add Microsoft.Net.Component.4.5.TargetingPack `
--add Microsoft.Net.Component.4.TargetingPack `
--add Microsoft.Net.Component.4.5.1.TargetingPack `
--add Microsoft.Net.Component.4.6.TargetingPack `
--add Microsoft.Net.ComponentGroup.TargetingPacks.Common `
--lang en-US
```
