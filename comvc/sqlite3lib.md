---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Windows的SQLite静态库"
description: "debug和release版"
date: 2024-11-19
author: "tdtc"
---
Num(Current Version): 3470000

# Debug版
"Source Code" -> [sqlite-amalgamation-Num.zip](https://sqlite.org/download.html)

## 新建DLL工程
project name: sqlite3（使用这个名字主要是在生成lib的时候不用更改输出名了）
<!-- vs2013: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-1-0prj(vs2013).png -->
<!-- vs2013: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-1-1prj(vs2013).png -->
<!-- vs2019: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-1prj.png -->
![VS2022 prj1](https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-1prj(vs2022).png)

### 添加SQLite源文件
拷贝以下文件到工程根目录:
- sqlite3.h
- sqlite3ext.h
- sqlite3.c
<!-- vs2013: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-2prj(vs2013).png -->
<!-- vs2019: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-2prj.png -->
![VS2022 prj2](https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-2prj(vs2022).png)

<!-- vs2013: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-3prj(vs2013).png -->
<!-- vs2019: https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-3prj.png -->
![VS2022 prj21](https://github.com/tdtc-hrb/cnblogs/raw/main/images/sqlite3-3prj(vs2022).png)


## 编译工程
Project ==> Properties ==> General
```
Configureation Type : Static library(.lib)
```
编译即可
```
Build -> Rebuild sqlite3
```

### 预编译头文件
Project ==> Properties ==> C/C++ ==> Precompiled Header
```
Not Using Precompiled Headers
```

- vs2019
```
sqlite3.c : fatal error C1853: 'Debug\sqlite3.pch' precompiled header file is from a previous version of the compiler,
or the precompiled header is C++ and you are using it from C (or vice versa)
```

- vs2022
```
sqlite3.c : error C1010: unexpected end of file while looking for precompiled header. Did you forget to add '#include "pch.h"' to your source?
```

### XP support
> vs2013
Project ==> Properties ==> General
```
Platform Toolset -> Visual Studio 2013 - Windows XP(v120_xp)
```


# Release版
從[Precompiled Binaries for Windows](https://sqlite.org/download.html), 下载
```
sqlite-dll-win32-x86-Num.zip
```

## output lib file
Start menu -> Visual Studio 2022 -> x86 Native Tools Command Prompt for VS 2022    
Enter the following command:
```bash
cd C:\Users\tdtc\Documents\sqlite-dll-win32-x86-Num
lib /def:sqlite3.def /out:sqlite3.lib /machine:x86
```


# Ref
- [Creating a Windows .lib file for SQLite for use with Visual Studio](https://raginginverno.wordpress.com/2013/01/23/welcome/)
