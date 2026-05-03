---
layout: ../../layouts/MarkdownPostLayout.astro
title: ".net framework 4.6"
description: "SQLite v1.0.112"
date: 2026-05-04
author: xiaobin
tags: ["faq5", "javascript_projectsystem.msi", "Physical disconnection"]
---
The official website no longer provides the installation program.

down [ZIP-src](https://system.data.sqlite.org/home/rchvdwnld/7727af784b0f153b)

### install visual studio 2015
- use [network proxy](https://tdtc-hrb.github.io/csdn/post/ops_network_proxy)
- 不连接网络

### build the System.Data.SQLite ("SDS") binaries
```cmd
cd <root>\Setup
```
- build the managed-only binaries
```cmd
build.bat ReleaseManagedOnly
```
- build the binaries for Win32 (x86)
```cmd
build.bat ReleaseNativeOnly Win32
```

## Ref
- [v1.0.112](https://system.data.sqlite.org/home/doc/7727af784b0f153b/www/build.wiki)
- [visual studio 2015 javascript_projectsystem](https://stackoverflow.com/a/39130542)
