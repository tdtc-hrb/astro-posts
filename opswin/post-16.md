---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio Code"
description: ".NET extension for Visual Studio Code"
date: 2025-02-08
author: xiaobin
tags: ["faq5", ".NET extension", "Windows Guest Additions"]
---
Version view:
- [dotnet runtime](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.vscode-dotnet-runtime)
- [c sharp](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)
- [c sharp dev kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit)

### supported os
- [LTSB 1607+](https://github.com/dotnet/core/blob/main/release-notes/9.0/supported-os)
- [Platforms](https://code.visualstudio.com/Docs/supporting/requirements#_platforms)

### down
Based on the version number, change the link.
https://marketplace.visualstudio.com/_apis/public/gallery/publishers/ms-dotnettools/vsextensions/
- dotnet runtime
```
vscode-dotnet-runtime/<Version-Num>/vspackage
```
- c sharp
```
csharp/<Version-Num>/vspackage?targetPlatform=win32-x64
```
- c sharp dev kit
```
csdevkit/<Version-Num>/vspackage?targetPlatform=win32-x64
```
