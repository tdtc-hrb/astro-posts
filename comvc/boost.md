---
layout: ../../layouts/MarkdownPostLayout.astro
title: "安装boost库(VC)"
description:  "vc11+ "
date: 2024-11-19
author: "tdtc"
---

support of [MSVC](https://en.wikipedia.org/wiki/Microsoft_Visual_C%2B%2B#Internal_version_numbering)
|     名称  | VS版本|Minimum version|
|      -   | -    | -    |
|msvc-11.0 |VS2012|[1.52.0](https://sourceforge.net/projects/boost/files/boost-binaries)|
|msvc-12.0 |VS2013|[1.55.0](https://sourceforge.net/projects/boost/files/boost-binaries)|
|msvc-14.0 |VS2015|[1.59.0](https://sourceforge.net/projects/boost/files/boost-binaries)|
|msvc-14.1 |VS2017|[1.64.0](https://boostorg.jfrog.io/artifactory/main/release)|
|msvc-14.2 |VS2019|[1.71.0](https://boostorg.jfrog.io/artifactory/main/release)|
|msvc-14.3 |VS2022|[1.78.0](https://boostorg.jfrog.io/artifactory/main/release)|

Current Version(xyz): [1.86.0](https://www.boost.org/users/download/)

# 1. 编译(x86)
x86 Native Tools Command Prompt for VS xxxx

- [About b2 vs bjam](https://www.boost.org/build/doc/html/bbv2/faq/names.html)
```
as of Boost 1.47.0, the official name of the executable was changed to b2.
```

## Gen b2 and build
```cmd
cd C:\boost_x_y_z
bootstrap.bat
```
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-cmd1.png -->
<!-- vs2015: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-cmd1(vs2015).png -->
<!-- vs2022.6: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-cmd1(vs2022).png -->
![windows cmd1](https://github.com/tdtc-hrb/csdn/raw/master/images/boost-cmd1(vs2022.12).png)

### build
- VS2022
```bash
b2 stage --toolset=msvc-14.3 --without-graph --without-graph_parallel --without-math --without-mpi --without-python --without-serialization --without-wave --stagedir="C:\boost\bin\vc143" link=static runtime-link=shared runtime-link=static threading=multi debug release
```

- VS2019
```bash
b2 stage --toolset=msvc-14.2 
...
--stagedir="C:\boost\bin\vc142"
...
```


# 2. 使用
Copy the 'C:\boost_x_y_z\boost' folder to 'C:' disk

## Project Properties
```
Project->Properties->Configuration Properties
```

### 头文件
> VC++ Directories->General

- Additional Include Directories:
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-header1.png -->
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-header2.png -->
![VS2022 directories](https://github.com/tdtc-hrb/csdn/raw/master/images/boost-header1(vs2022).png)
<!-- boost v1.82: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-header2(v182).png -->
![VS2022 header2](https://github.com/tdtc-hrb/csdn/raw/master/images/boost-header2(v186).png)

### 库链接
> Linker->General

- Additional Library Directories:
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-linker1.png -->
<!-- vs2015: https://github.com/tdtc-hrb/csdn/raw/master/images/boost-linker1(vs2015).png -->
![VS2022 linker1](https://github.com/tdtc-hrb/csdn/raw/master/images/boost-linker1(vs2022).png)

### [Spectre mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc)
> vs2017/vs2019

- c/c++->Code Generation
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/gen1-vc142.png -->
![VS2022 c++](https://github.com/tdtc-hrb/csdn/raw/master/images/gen1-vc143.png)


## Example - [Creating and Managing Threads](https://theboostcpplibraries.com/boost.thread-management)
```c++
#include <boost/thread.hpp>
#include <boost/chrono.hpp>
#include <iostream>

void wait(int seconds)
{
    boost::this_thread::sleep_for(boost::chrono::seconds{ seconds });
}

void thread()
{
    for (int i = 0; i < 5; ++i)
    {
        wait(1);
        std::cout << i << std::endl;
    }
}

int main()
{
    boost::thread t{ thread };
    t.join();
}
```

### VS2015/13/12

The top of the reference header add:
```
#include "stdafx.h"
```
