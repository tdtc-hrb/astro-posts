---
title: "使用 NSIS (Nullsoft Scriptable Install System)"
description: "生成sandboxie的安装分发"
date: 2022-09-03T00:08:08+08:00
---
- OS    
Win1809(x64)
- VS2017(v15.9)

# Installation
down [v2.51](https://sourceforge.net/projects/nsis/files/NSIS%202/2.51/)

## [InetC](https://nsis.sourceforge.io/Inetc_plug-in)
  From Inetc.zip, copy \Plugins\x86-ansi\InetC.dll to your NSIS plugins folder (e.g. C:\Program Files (x86)\NSIS\Plugins)

## UI
- System.nsh    
  Overwrite C:\Program Files (x86)\NSIS\Contrib\Modern UI\System.nsh with install\nsis_updates.zip\nsis\Contrib\Modern UI\System.nsh
- Languages    
  Copy language files from install\nsis_updates.zip\nsis\Contrib\Modern UI\Language files to 
```
C:\Program Files (x86)\NSIS\Contrib\Modern UI\Language files
```

## Iconv
down [libiconv-1.9.2-1-bin.zip](https://sourceforge.net/projects/gnuwin32/files/libiconv/1.9.2-1/libiconv-1.9.2-1-bin.zip/download) 
and [libiconv-1.9.2-1-dep.zip](https://sourceforge.net/projects/gnuwin32/files/libiconv/1.9.2-1/libiconv-1.9.2-1-dep.zip/download)

location:
```
C:\Users\tdtc\Documents\sandboxie\tools\iconv
```

These contain the 3 binaries that are required:    
- Iconv.exe
- Libiconv2.dll
- Libintl3.dll


# usage
- configure NSIS Project
- build Visual Studio Solution
- Generate installer file

## project file
  更改install\SandboxieVS.nsi.

### arch
```
!define _BUILDARCH		Win32
;!define _BUILDARCH		x64
```
默认为32位

### Compatible with XP
  移除"SystemCheck_Done_XP_2003"前面的";".

Ln559&Ln560:
```
StrCmp $0 "5.1" SystemCheck_Done_XP_2003
StrCmp $0 "5.2" SystemCheck_Done_XP_2003
```
Ln577:
```
SystemCheck_Done_XP_2003:
```

## compile sln
编译vs项目文件，以生成application(exe, dll and sys file).

location:    
- x86
```
Bin\Win32
```

- x64
```
Bin\x64
```

## exec NSIS
In Explorer, Right-click \install\SandboxieVS.nsi and select "Compile NSIS Script";    
Generate SandboxieInstall32.exe or SandboxieInstall64.exe.


# Ref
- [sandboxie install](https://gitee.com/xiaobin80/sandboxie/blob/master/install/ReadMe.txt)
