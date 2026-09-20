---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Proteus Professional 安装"
description: "Proteus Professional v8/v9"
date: 2026-07-08
author: xiaobin
---
The current version 9.1 still has some issues.

When opening .DSN (an older project), the application cannot be closed!

## Installation
1. Disconnect from the Internet
2. Run the installation file.
3. Proteus Professional v8 requires a .lxk file; please select an available license file.
4. Continue installation and after finish it DO NOT START THE PROGRAM!

### Patch-Proteus v8
**don't checked "Verify Hash"**
***Please note that this patch does not work in WinXP, Win7***

for example:
```
Patch-Proteus-8.16-SP3-36097.0.exe
```

### Patch-Proteus v9
- open Licence Manager.exe at 
```
C:\Program Files\Labcenter Electronics\Proteus 9 Professional\Bin
```
- "Open Licence File" - button
```
please select an available license file.
```
- "Install Licence" - button
- close Licence Manager.exe
- copy 
```
.lxk
version.dll
```
to 
```
C:\Program Files\Labcenter Electronics\Proteus 9 Professional\Bin
```
