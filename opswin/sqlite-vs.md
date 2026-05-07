---
layout: ../../layouts/MarkdownPostLayout.astro
title: ".net framework 4.6"
description: "SQLite v1.0.112"
date: 2026-05-07
author: xiaobin
tags: ["faq5", "javascript_projectsystem.msi", "Physical disconnection"]
---
The official website no longer provides the installation program.

down [ZIP-src](https://system.data.sqlite.org/home/rchvdwnld/7727af784b0f153b)

## install visual studio 2015
- use [network proxy](https://tdtc-hrb.github.io/csdn/post/ops_network_proxy)
> javascript_projectsystem.msi miss issue
### VSSDK
- You should see a tree view of custom features. Open Common Tools. 
You should see "Visual Studio Extensibility Tools" .
![](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/extensibility/media/vssdkinstall.png)
- Check Visual Studio Extensibility Tools , then click Next and continue the installation.

## build the System.Data.SQLite ("SDS") binaries
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
- build the binaries for x64
```
build.bat ReleaseNativeOnly x64
```

## inno
- Add App(iscc.exe) path to system path

### System.Data.SQLite.dll not exist
Due to official documentation corrections, the following two commands need to be added:
- build the binaries for Win32 (x86)
```cmd
build.bat Release Win32
```
- build the binaries for x64
```
build.bat Release x64
```
### done
- Modify the Inno version in bake.bat:
```
IF "%PROCESSOR_ARCHITECTURE%" == "x86" GOTO set_path_x86

SET INNOSETUPPATH=%ProgramFiles(x86)%\Inno Setup 7
GOTO set_path_done

:set_path_x86

SET INNOSETUPPATH=%ProgramFiles%\Inno Setup 7

:set_path_done
```
- Package installation
```
bake_all.bat
```

## Ref
- [v1.0.112](https://system.data.sqlite.org/home/doc/7727af784b0f153b/www/build.wiki)
- [visual studio 2015 javascript_projectsystem](https://stackoverflow.com/a/39130542)
- [Installing the Visual Studio SDK](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/extensibility/installing-the-visual-studio-sdk?view=vs-2015)
- [Visual Studio SDKs](https://www.visualstudioextensibility.com/downloads/vs-sdks/)
