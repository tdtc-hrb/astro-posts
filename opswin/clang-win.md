---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Latest Clang for VSCode"
description: "Standalone Cmake and Clang in VS Code"
date: 2026-01-24
author: xiaobin
tags: ["faq2", "Microsoft Visual C++", "Clang"]
---
- [clang](https://github.com/llvm/llvm-project/releases)
- [cmake](https://github.com/Kitware/CMake/releases)
- [ninja-build](https://github.com/ninja-build/ninja/releases)
- [Visual Studio Code](https://code.visualstudio.com) - [CMake-tools plugin](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)

### [MSVC](https://en.wikipedia.org/wiki/Microsoft_Visual_C%2B%2B)
- [v14.1+](https://tdtc-hrb.github.io/ops-win/posts/vc-win)

About: [clang-cl](https://clang.llvm.org/docs/UsersManual.html#clang-cl) is an alternative command-line interface to Clang, 
designed for compatibility with the Visual C++ compiler, cl.exe.

### cmake - visual studio
- [Visual Studio 2026 will require CMake Version 4.2 or later](https://cmake.org/cmake/help/latest/generator/Visual%20Studio%2018%202026.html)
- [Visual Studio 2022 will require CMake Version 3.21 or later](https://llvm.org/docs/GettingStartedVS.html)

## project
├── Circular.cpp    
├── Circular.h    
├── testCir2.cpp    
├── CMakeLists.txt

### src
- [source files](https://tdtc-hrb.github.io/csdn/post/c-console_app)
- [CMakeLists.txt](https://github.com/microsoft/vscode-cmake-tools/issues/2391)
```
cmake_minimum_required(VERSION 3.23)
project(mytest CXX)
add_executable(testCir2 testCir2.cpp Circular.cpp)
```
### build
- Open the Command Palette (Ctrl+Shift+P) and run
```
CMake: Select a Kit
```
- Select the compiler you want to use.
```
Clang-cl <version> x86_64-pc-windows-msvc
```
These names are stored in "cmake-tools-kits.json"
```
%USERPROFILE%\AppData\Local\CMakeTools
```
- Build all projects
right click "CMakeLists.txt",
```
Build all projects
```

## Ref
- [Getting Started: Building and Running Clang](https://clang.llvm.org/get_started.html)
- [Get started with CMake Tools on Linux](https://code.visualstudio.com/docs/cpp/cmake-linux)
- [How do I install latest Clang for VSCode? ](https://www.reddit.com/r/cpp_questions/comments/1j6fcjg/how_do_i_install_latest_clang_for_vscode_on/?rdt=60458)
