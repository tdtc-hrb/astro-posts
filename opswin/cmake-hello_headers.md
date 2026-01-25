---
layout: ../../layouts/MarkdownPostLayout.astro
title: "learn CMake - Locations"
description: "Hello Headers"
date: 2026-01-24
author: xiaobin
tags: ["CMake"]
---
- [Latest Clang for VSCode](https://tdtc-hrb.github.io/ops-win/posts/clang-win/)

### [Locations](https://gitlab.kitware.com/cmake/community/-/wikis/doc/cmake/Useful-Variables#locations)
|Variable|Info|
|-|-|
|CMAKE_CURRENT_SOURCE_DIR|The current source directory if using sub-projects and directories.|
|CMAKE_CURRENT_LIST_DIR|(since 2.8.3) this is the directory of the listfile currently being processed.|
|CMAKE_SOURCE_DIR|this is the directory which contains the top-level CMakeLists.txt, i.e. the top level source directory.|
|PROJECT_SOURCE_DIR|contains the full path to the root of your project source directory, i.e. to the nearest directory where CMakeLists.txt contains the PROJECT() command.|

#### [Difference between CMAKE_CURRENT_SOURCE_DIR and CMAKE_CURRENT_LIST_DIR](https://stackoverflow.com/questions/15662497/difference-between-cmake-current-source-dir-and-cmake-current-list-dir)
The variables CMAKE_CURRENT_SOURCE_DIR and CMAKE_CURRENT_LIST_DIR may refer to different directories 
for a CMake list file that is included by another file with the include command. E.g., 
if a CMakeLists.txt is present in a directory project and contains the following directive
```
include(src/CMakeLists.txt)
```
then while src/CMakeLists.txt is being processed CMAKE_CURRENT_LIST_DIR 
will refer to project/src whereas CMAKE_CURRENT_SOURCE_DIR still points to the outer directory project.

CMAKE_CURRENT_LIST_DIR comes in handy, when you need to locate resource files like template files or 
batch scripts that are located next to the CMakeLists.txt file currently being processed.

#### [Are CMAKE_SOURCE_DIR and PROJECT_SOURCE_DIR the same in CMake?](https://stackoverflow.com/questions/32028667/are-cmake-source-dir-and-project-source-dir-the-same-in-cmake)
There is a difference between these variables. CMAKE_SOURCE_DIR does indeed refer to the folder where the top-level CMakeLists.txt is defined. 
However, PROJECT_SOURCE_DIR refers to the folder of the CMakeLists.txt containing the most recent project() command.

For example, say you have a top-level project called Outer and this contains a subdirectory with its own project called Inner. 
Outer's CMakeLists.txt has:
```
project(Outer)
add_subdirectory(Inner)
```
and Inner's:
```
project(Inner)
```
Then in both of these CMakeLists files, CMAKE_SOURCE_DIR will refer to Outer's source dir. 
But while PROJECT_SOURCE_DIR for Outer is also this same dir, this is not the case for Inner. 
Inner's PROJECT_SOURCE_DIR is the subdirectory containing its CMakeLists.txt.

This difference applies to all ```PROJECT_<var>``` vs ```CMAKE_<var>``` variables.

### example
```
cmake_minimum_required(VERSION 4.2)

# Set the project name
project(mytest)

# Add an executable with the above sources
add_executable(mytest main.c hex2int.c)

target_include_directories(mytest
    PRIVATE 
        ${PROJECT_SOURCE_DIR}
)
```
source from [十六进制转十进制](https://tdtc-hrb.github.io/csdn/post/c-string-h2i/)

## Ref
- [hello-headers](https://github.com/ttroy50/cmake-examples/tree/master/01-basic/B-hello-headers)
