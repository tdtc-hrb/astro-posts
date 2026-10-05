---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Windows的SQLite静态库 - wx"
description: "debug和release版"
date: 2026-02-27
author: "tdtc"
---
- debug/release
> debug:ud, release:u
- Win32/x64

## wxMsw
- [setup.exe](https://github.com/wxWidgets/wxWidgets/releases/download/v3.2.9/wxMSW-3.2.9-Setup.exe)

### 编译
- `C:/wxWidgets-3.2.9/build/msw/wx_vc17.sln` default: debug and x64

choose: Release and Win32
```
Build Solution
```
Copy vc_lib to the lib directory of wxSqlite and rename it to vc14x_lib.

## wxSqlite
- Root directory
```
C:/wxsqlite3-4.11
```
- [wxWidgets-3.2.9_Headers.7z](https://github.com/wxWidgets/wxWidgets/releases/download/v3.2.9/wxWidgets-3.2.9-headers.7z)
> Unzip wxWidgets-3.2.9_Headers.7z and cut it to the root directory.

### wx_setup
> build/wx_setup.props

- release
```
  <PropertyGroup Label="UserMacros">
    <IncludePath>C:\wxsqlite3-4.11\lib\vc14x_lib\mswu;$(IncludePath)</IncludePath>
  </PropertyGroup>
```
- debug
```
  <PropertyGroup Label="UserMacros">
    <IncludePath>C:\wxsqlite3-4.11\lib\vc14x_lib\mswud;$(IncludePath)</IncludePath>
  </PropertyGroup>
```

Then open `C:/wxsqlite3-4.11/build/wxsqlite3_vc17.sln`

### Lnk1104
```
cannot open file 'wxbase32u.lib'
project: minimal and treeview
```
解决办法：
```
VC++ Directories -> Library Directories
```
- wxbase32u.lib
```
C:\wxsqlite3-4.11\lib\vc14x_lib
```

## Ref
- [wxsqlite3](https://github.com/utelle/wxsqlite3#wxmsw)
