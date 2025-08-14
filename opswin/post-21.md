---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Clang/LLVM support in Visual Studio"
description: "Visual Studio 2019(v16.7) 及以上版本"
date: 2025-08-14
author: xiaobin
tags: ["faq2", "Microsoft Visual C++", "Clang"]
---
- [Visual Studio 2019 16.7 or later](https://clang.llvm.org/get_started.html)
- [Visual Studio 在线](https://visualstudio.microsoft.com/vs/community)

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
### [Clang/LLVM support in Visual Studio](https://learn.microsoft.com/en-us/cpp/build/clang-support-msbuild)
- C++ Clang tools for Windows
```
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang
```
includes:
- C++ Clang Compiler for Windows
```
Microsoft.VisualStudio.Component.VC.Llvm.Clang
```
- C++ Clang-cl for v143 build tools (x64/x86)
```
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset
```
