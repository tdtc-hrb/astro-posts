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
- build the binaries for x64
```
build.bat ReleaseNativeOnly x64
```

## inno
- Add App(iscc.exe) path to system path
- remove SQLite.Designer.x
```
;;;Components: Application\Designer; Source: ..\..\bin\{#Year}\{#BaseConfiguration}\bin\SQLite.Designer.dll; DestDir: {app}\bin; Flags: restartreplace uninsrestartdelete
;;;Components: Application\Designer and Application\Symbols; Source: ..\..\bin\{#Year}\{#BaseConfiguration}\bin\SQLite.Designer.pdb; DestDir: {app}\bin; Flags: restartreplace uninsrestartdelete
```
### System.Data.SQLite.dll not exist
Choose one of the two options:
- a) Change the switch.
- b) Change the path.

#### a - ln194
```
#if Pos("NativeOnly", AppConfiguration) == 1
```
#### b
```
Components: Application\Core\MSIL; Tasks: gac; Source: ..\..\bin\{#Year}\{#BaseConfiguration}\bin\System.Data.SQLite.dll; DestDir: {app}\GAC; StrongAssemblyName: "System.Data.SQLite, Version={#AppVersion}, Culture=neutral, PublicKeyToken={#AppPublicKey}, ProcessorArchitecture={#GacProcessor}"; Flags: restartreplace uninsrestartdelete uninsnosharedfileprompt sharedfile gacinstall
Components: Application\Core\MSIL; Source: ..\..\bin\{#Year}\{#BaseConfiguration}\bin\System.Data.SQLite.dll; DestDir: {app}\bin; Flags: restartreplace uninsrestartdelete
Components: Application\Core\MSIL and Application\Symbols; Source: ..\..\bin\{#Year}\{#BaseConfiguration}\bin\System.Data.SQLite.pdb; DestDir: {app}\bin; Flags: restartreplace uninsrestartdelete
```

### done
```
bake_all.bat
```

## Ref
- [v1.0.112](https://system.data.sqlite.org/home/doc/7727af784b0f153b/www/build.wiki)
- [visual studio 2015 javascript_projectsystem](https://stackoverflow.com/a/39130542)
