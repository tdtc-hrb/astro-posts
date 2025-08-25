---
layout: ../../layouts/MarkdownPostLayout.astro
title: ".net framework 4.6"
description: "SQLite v1.0.112"
date: 2025-08-18
author: xiaobin
tags: ["faq5"]
---
- [vs16](https://aka.ms/vs/16/release/vs_Community.exe)
- [SQLite v1.0.112](https://system.data.sqlite.org/home/doc/trunk/www/downloads.wiki)

### Core Editor
```
--add Microsoft.VisualStudio.Component.CoreEditor `
--add Microsoft.VisualStudio.Workload.CoreEditor `
```

### .NET development tools
```
--add Microsoft.VisualStudio.Component.NuGet `
--add Microsoft.Net.Component.4.6.1.TargetingPack `
--add Microsoft.VisualStudio.Component.Roslyn.Compiler `
--add Microsoft.VisualStudio.Component.Roslyn.LanguageServices `
--add Microsoft.VisualStudio.Component.FSharp `
--add Microsoft.ComponentGroup.ClickOnce.Publish `
--add Microsoft.NetCore.Component.DevelopmentTools `
--add Microsoft.Net.Component.4.8.SDK `
--add Microsoft.Net.Component.4.7.2.TargetingPack `
--add Microsoft.Net.ComponentGroup.DevelopmentPrerequisites `
--add Microsoft.Component.MSBuild `
--add Microsoft.VisualStudio.Component.TextTemplating `
--add Microsoft.VisualStudio.Component.SQL.CLR `
--add Microsoft.VisualStudio.Component.ManagedDesktop.Core `
```
### .NET framework 4 - 4.6 development tools
```
--add Microsoft.Net.Component.4.5.2.TargetingPack `
--add Microsoft.Net.Component.4.5.TargetingPack `
--add Microsoft.Net.Component.4.TargetingPack `
--add Microsoft.Net.Component.4.5.1.TargetingPack `
--add Microsoft.Net.Component.4.6.TargetingPack `
--add Microsoft.Net.ComponentGroup.TargetingPacks.Common `
```
### Managed Desktop
```
--add Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites `
--add Microsoft.VisualStudio.Workload.ManagedDesktop"
```
