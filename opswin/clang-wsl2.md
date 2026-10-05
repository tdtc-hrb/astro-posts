---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Clang for WSL2"
description:  "Note that CLion does not support legacy WSL."
date: 2026-02-18
author: "tdtc"
---
- [example](https://tdtc-hrb.github.io/com-vc/posts/boost-thread/)
- CMakeLists.txt
```
cmake_minimum_required(VERSION 4.2)
project(untitled)

set(CMAKE_CXX_STANDARD 17)

find_package(Boost COMPONENTS thread chrono system REQUIRED)

include_directories(${Boost_INCLUDE_DIRS})

add_executable(untitled main.cpp)

target_link_libraries(untitled ${Boost_LIBRARIES})
```

## Toolchain
- cmake
```wsl
sudo apt install cmake
```
- ninja
```wsl
sudo apt -y install ninja-build
```
- Clang
```wsl
sudo apt install libboost-all-dev
```

### [Update CMake on Ubuntu](https://linuxvox.com/blog/update-cmake-ubuntu/#method-2-using-the-kitware-apt-repository)
- Ubuntu 20.04 (focal)
```
# Install the necessary dependencies
sudo apt update
sudo apt install apt-transport-https ca-certificates gnupg software-properties-common wget
 
# Add the Kitware signing key
wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | sudo tee /usr/share/keyrings/kitware-archive-keyring.gpg >/dev/null
 
# Add the Kitware APT repository
echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ focal main' | sudo tee /etc/apt/sources.list.d/kitware.list >/dev/null
 
# Update the package list
sudo apt update
```
- install new version:
```
sudo apt upgrade
```

### clion setting
> 注意： 路径要使用 /usr/bin

![toolchain](https://github.com/tdtc-hrb/cnblogs/raw/main/images/cl_wsl_new_toolchain.png)
- Clion picture
![toolchain](https://resources.jetbrains.com/help/img/idea/2025.3/cl_wsl_new_toolchain.png)

## Ref
- [Linking Boost thread library](https://stackoverflow.com/a/41393896)
- [Configure WSL](https://www.jetbrains.com/help/clion/how-to-use-wsl-development-environment-in-product.html#wsl-general)
