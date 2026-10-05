---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Interface - C++"
description: "C++98 standard"
date: 2026-01-12
author: xiaobin
tags: ["C++ standard"]
---
- IDE: VS2022

An interface class is a class that has no member variables, and where all of the functions are pure virtual! 
Interfaces are useful when you want to define the functionality that derived classes must implement, 
but leave the details of how the derived class implements that functionality entirely up to the derived class.

#### enable c++17
The default is C++14.
```
Project -> Properties -> General
```
C++ Language Standard:
```
ISO C++17 Standard
```
string_view can only be used in C++17 and above.

### example
```
#include <string_view>

class IErrorLog
{
public:
    virtual bool openLog(std::string_view filename) = 0;
    virtual bool closeLog() = 0;

    virtual bool writeError(std::string_view errorMessage) = 0;

    virtual ~IErrorLog() {} // make a virtual destructor in case we delete an IErrorLog pointer, so the proper derived destructor is called
};
```

## Ref
- [25.7 — Pure virtual functions, abstract base classes, and interface classes](https://www.learncpp.com/cpp-tutorial/pure-virtual-functions-abstract-base-classes-and-interface-classes/)
- [virtual function specifier](https://en.cppreference.com/w/cpp/language/virtual.html)
