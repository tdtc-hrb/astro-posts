---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Install TCL development libraries"
description: "Tool Command Language (Tcl) for Windows"
date: 2026-02-23
author: xiaobin
tags: ["Microsoft Visual C++", "TCL"]
---
TCL is a generic "Bash" that is not bundled with an operating system.

It provides shell operations for installing package tools (e.g., InstallShield, Wise, NSIS) and operating systems.

## win
- [tcl](https://www.tcl.tk/software/tcltk/download.html)
- [VC14.1+](https://tdtc-hrb.github.io/ops-win/posts/vc-win)
### config
- x86
- x64

#### x86
- install directry:
```
c:\tcl32
```
- x86 Native Tools Command Prompt
#### x64
- install directry:
```
c:\tcl
```
- x64 Native Tools Command Prompt

### Install
Untar or unzip the source archive.
```
cd win
nmake /f makefile.vc INSTALLDIR=c:\tcl32 release
nmake /f makefile.vc INSTALLDIR=c:\tcl32 install
```
- rename    
tclsh90.exe rename tclsh.exe

- add path    
Add `c:\Tcl\bin` to your %PATH%.

## Ref
- [Install TCL development libraries](https://github.com/sqlcipher/sqlcipher/blob/master/doc/compile-for-windows.md)
- [How to Compile Tcl](https://www.tcl-lang.org/doc/howto/compile.html)
- [Tcl as a Shell Scripting Replacement](https://www.karl.berlin/tcl-blog.html)
