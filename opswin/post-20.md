---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Microsoft Visual C++ 及 Windows SDK"
description: "After vs2022 17.12, the main productivity for VC"
date: 2025-02-24
author: xiaobin
tags: ["faq2", "Microsoft Visual C++", "Windows SDK"]
---
These options are available in [Visual Studio 在线](https://tdtc-hrb.github.io/ops-win/posts/post-6)

## VC
```
--add Microsoft.VisualStudio.Component.VC.CoreIde `
--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 `
--add Microsoft.VisualStudio.Component.VC.Redist.14.Latest `
```

### [Windows SDK](https://learn.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools)
- win10
```
--add Microsoft.VisualStudio.Component.Windows10SDK.19041 `
```
- win11
```
--add Microsoft.VisualStudio.Component.Windows11SDK.26100 `
```

### ATL
```
--add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core `
--add Microsoft.VisualStudio.Component.VC.ATL `
--add Microsoft.VisualStudio.Workload.NativeDesktop `
```

## MFC
```
--add Microsoft.VisualStudio.Component.VC.ATLMFC `
```
