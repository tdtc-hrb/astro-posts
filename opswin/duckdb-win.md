---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Compile DuckDB using CMake in MSVC/Clang"
description: "Compiling duckdb on Windows"
date: 2026-02-28
author: xiaobin
tags: ["DuckDB", "Microsoft Visual C++", "Clang"]
---
- [Source code (zip)](https://github.com/duckdb/duckdb/releases)

We recommend using a Clang-based VS Code environment.

## [Clang-win](https://tdtc-hrb.github.io/ops-win/posts/clang-win/)
- Stage 1
- Stage 2
### Stage 1 - static and dynamic library
```
File -> Open Folder
```
Open the root directory
```
C:\Users\hp262\Documents\duckdb-1.4.4
```
and `Build -> Build All`

### Stage 2 - Example
Open <i>embedded-c++</i> directory
```
C:\Users\hp262\Documents\duckdb-1.4.4\examples\embedded-c++
```
Edit CMakeLists to change the location of the lib directory; 
Original location: 
```
link_directories(../../build/release/src)
```
Modified location:
```
link_directories(../../build/src)
```
and `Build -> Build All`

## MSVC
- VS2019+ 
> includes C++ CMake tools for Windows

### Stage 1 - static and dynamic library
```
File -> CMake
```
Open CMakeLists.txt in the root directory
```
D:\d2b\duckdb-1.4.4\CMakeLists.txt
```
and `Build -> Build All`

### Stage 2 - Example
```
File -> CMake
```
Open CMakeLists.txt in the <i>embedded-c++</i> directory
```
D:\d2b\duckdb-1.4.4\examples\embedded-c++\CMakeLists.txt
```
Edit CMakeLists to change the location of the lib directory; 
Original location: 
```
link_directories(../../build/release/src)
```
Modified location:
```
link_directories(../../out/build/x64-Debug/src)
```
and `Build -> Build All`

## Test
Copy the following files to the same directory:
- example.exe
- duckdb.dll

The output will be displayed at the command prompt:
```
C:\Users\hp262\Documents>example.exe
i
INTEGER
[ Rows: 1]
3

```
