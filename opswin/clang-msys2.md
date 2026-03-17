---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Clang for Clion"
description: "MSYS2 + Clion"
date: 2026-02-17
author: xiaobin
tags: ["MSYS2", "Clion"]
---
- [random demo](https://www.boost.org/doc/libs/latest/libs/random/example/random_demo.cpp)
### [use boost](https://gist.github.com/yeiichi/974515fcd2d593460fd9991a991ea147)
CMakeLists.txt:
```
cmake_minimum_required(VERSION 4.1)
project(untitled)

set(CMAKE_CXX_STANDARD 20)

find_package(Boost REQUIRED)

include_directories(${Boost_INCLUDE_DIRS})

add_executable(untitled main.cpp)
```

## [msys2](https://www.msys2.org)
```
C:\msys64\clang64\bin
```
加到PATH

### installation
open "MSYS2 CLANG64" from the Start menu.

- clang
```
pacman -S mingw-w64-clang-x86_64-toolchain
```
- cmake
```
pacman -S mingw-w64-x86_64-cmake
```
- nija
```
pacman -S mingw-w64-x86_64-ninja
```
#### gdb - option
```
pacman -S mingw-w64-clang-x86_64-gdb
```

### library
- boost
```
pacman -S mingw-w64-x86_64-boost
```

## Clion
[Clion](https://www.jetbrains.com/clion/) bundles a version of the MinGW toolset for quick setup. 
The exact version bundled is MinGW-w64 13.1 
with <i>posix</i> threads, and <i>seh</i> exceptions.

#### Thread model - threads
- [mcf](https://github.com/lhmouse/mcfgthread/blob/master/README.md)    
MCF Gthread is a threading support library for Windows 7 and above that implements the gthread interface set, 
which is used internally both by GCC to provide synchronization of initialization of local static objects, 
and by libstdc++ to provide C++11 threading facilities.
- win32    
Windows All Versions
- posix    
Unix-like
#### Exception Handling - exceptions
- [dwarf](https://dwarfstd.org/doc/Debugging%20using%20DWARF-2012.pdf)
> Debugging With Arbitrary Record Formats
- Structured Exception Handling (SEH)

### [Upgrade MingW bundled with Clion](https://github.com/niXman/mingw-builds-binaries) - option
把x86_64-15.2.0-release-posix-seh-ucrt-rt_v13-rev0.7z覆盖到
```
<CLion-HOME>\bin\mingw
```

### Toolchain
> Go to Settings | Build, Execution, Deployment | Toolchains and create a MinGW toolchain
> Set the Toolset to C:\msys64\clang64. Set other paths manually in case they are not detected automatically.

![toolchain](https://github.com/tdtc-hrb/cnblogs/raw/main/images/cl_clang_mingw.png)

- Clion picture

![toolchain](https://resources.jetbrains.com/help/img/idea/2025.3/cl_clang_mingw.png)

## Ref
- [Set up the Clang compiler for MinGW](https://www.jetbrains.com/help/clion/quick-tutorial-on-configuring-clion-on-windows.html#setup-clang)
- [Using CMake in MSYS2](https://www.msys2.org/docs/cmake/)
