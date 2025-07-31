---
title: "Desktop development environment for .NET"
description: ".NET development tools"
date: 2025-02-22
author: xiaobin
tags: ["faq6", ".NET Framework 4", "Visual Studio 2019", "Visual Studio 2022"]
---

An error occurred trying to load the page.    
Could not load file or assembly 'Microsoft.VSDesigner, Version=x.x.x.x, Culture=neutral, PublicKeyToken=y' or one of its dependencies.    
The system cannot find the file specified.
```
Control Panel -> Add/Remove Programs
right click "Visual Studio 20xx" -> Change
Check ".NET desktop development"
```

### Download Offline package
.NET Framework 4 – 4.6 development tools:
```
--add Microsoft.Net.Component.4.5.2.TargetingPack `
--add Microsoft.Net.Component.4.5.TargetingPack `
--add Microsoft.Net.Component.4.TargetingPack `
--add Microsoft.Net.Component.4.5.1.TargetingPack `
--add Microsoft.Net.Component.4.6.TargetingPack `
--add Microsoft.Net.ComponentGroup.TargetingPacks.Common `
```
These options are available in [Visual Studio 2017 及以上版本的在线下载](https://tdtc-hrb.github.io/ops-win/posts/post-6)：
- [vs2019 - v16.11](https://aka.ms/vs/16/release/vs_Community.exe)
- [vs2017 - v15.9](https://aka.ms/vs/15/release/vs_community.exe)
