---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio 2017 及以上版本的在线下载"
description: "down format and Common"
date: 2025-07-24
author: xiaobin
tags: ["faq2", "Visual Studio Online"]
---
- [Old version(4.6.2) Fx](https://aka.ms/vs/16/release/vs_Community.exe)
- [VC](https://aka.ms/vs/17/release/vs_Community.exe)

## [down options](https://learn.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools)
exec:
```
.\vs_Community.exe --layout D:\win10soft\vs20xx `
--add <Component Name>
--lang en-US
```
### format
- target directory
```
--layout TARGET
```
- components
```
--add NAME(Component)
```
- language
```
--lang en-US
```

### Common
- Core
```
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.VisualStudio.Component.TextTemplating `
```
- Microsoft Build Tools
```
--add Microsoft.Component.MSBuild `
```
- JIT
```
--add Microsoft.VisualStudio.Component.Debugger.JustInTime `
```
- IntelliCode
```
--add Microsoft.VisualStudio.Component.IntelliCode `
```
