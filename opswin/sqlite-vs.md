---
layout: ../../layouts/MarkdownPostLayout.astro
title: ".net framework 4.6"
description: "SQLite v1.0.112"
date: 2026-05-07
author: xiaobin
tags: ["faq5", "javascript_projectsystem.msi", "Physical disconnection"]
---
- VC
> MFC is not required.
- VSSDK
> SQLite.Designer is required during compilation.
![](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/extensibility/media/vssdkinstall.png)


## Automated Build - command line
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

## Manual Build - VS2019
If you don't have VS2015 installed, then build manually.

Open "SQLite.NET.2015.sln" with VS2019.

### About SQLite.NET.2015.sln and SQLite.NET.2015.MSBuild.sln
- SQLite.NET.2015.sln    
Provide for manual build
- SQLite.NET.2015.MSBuild.sln    
Provide for automated building

### Cannot open include file: 'malloc.h'
- Install Windows SDK

ref [Malloc library](https://developercommunity.visualstudio.com/t/malloc-library/63279),
[C header files missing to compile Sqlite3.c](https://stackoverflow.com/a/65878315),
[Compiling amalgamation with Visual Studio 2019](https://sqlite.org/forum/forumpost/76a60b19f8?t=c&unf)

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
- [Build Procedures](https://system.data.sqlite.org/home/doc/branch-v1/www/build.wiki)
- [v1.0.120.0](https://system.data.sqlite.org/home/info/7727af784b0f153b)
- [v1.0.105.2](https://system.data.sqlite.org/home/info/0fadcbe4d2827d69)
- [visual studio 2015 javascript_projectsystem](https://stackoverflow.com/a/39130542)
- [Installing the Visual Studio SDK](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/extensibility/installing-the-visual-studio-sdk?view=vs-2015)
- [Visual Studio SDKs](https://www.visualstudioextensibility.com/downloads/vs-sdks/)
