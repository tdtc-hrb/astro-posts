---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio 2019+的在线下载"
description: "down format and Common"
date: 2025-08-14
author: xiaobin
tags: ["faq2", "Visual Studio Online"]
---
- [Old version Fx - v4.6](https://tdtc-hrb.github.io/ops-win/posts/post-11)

Recommendation: Starting October 14, 2025, do not use ATL or MFC in new projects.

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
