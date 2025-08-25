---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio 2019+的在线下载"
description: "down format and Common"
date: 2025-08-14
author: xiaobin
tags: ["faq2", "Visual Studio Online"]
---
Find components in [workload](https://learn.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools) and add them; 

Take "Microsoft Build Tools" as an example:
```
.\vs_Community.exe --layout D:\win10soft\vs20xx `
--add Microsoft.Component.MSBuild `
--lang en-US
```
