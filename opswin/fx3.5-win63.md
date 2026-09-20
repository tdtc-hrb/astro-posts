---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Using .NET Framework 3.5 on Windows 8 and above"
description: "Using the Windows DVD"
date: 2025-02-22
author: xiaobin
tags: ["faq6", ".NET Framework 3.5", "PowerShell"]
---

[.NET Framework 3.5 - Windows 8](https://www.askvg.com/how-to-install-microsoft-net-framework-3-5-offline-in-windows-8-without-internet-connection/)

first, mount windows installation DVD(ISO)
- DVD
```
D:
```
Then, execute PowerShell as Administrator
```ps
dism /online /enable-feature /featurename:NetFx3 /All /Source:D:\sources\sxs /LimitAccess
```
