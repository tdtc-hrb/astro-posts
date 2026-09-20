---
layout: ../../layouts/MarkdownPostLayout.astro
title: "hash map - C++"
description: "C++11 standard"
date: 2026-01-12
author: xiaobin
tags: ["C++ standard"]
---
- IDE: VS2022

### example
```
#include <iostream>
#include <unordered_map>
using namespace std;

int main() {

    // Creating an unordered_map with integer
    // keys and string values
    unordered_map<int, string> um =
    { {1, "Geeks"}, {2, "For"}, {3, "C++"} };

    for (auto i : um)
        cout << i.first << ": " << i.second
        << endl;
    return 0;
}
```

#### vs2015
```
Error (active)		no operator "<<" matches these operands	ConsoleApplication2	
c:\Users\hp25nov\Documents\Visual Studio 2015\Projects\ConsoleApplication1\ConsoleApplication2\ConsoleApplication2.cpp	17

Error	C2059	syntax error: '['	ConsoleApplication2	
c:\users\hp25nov\documents\visual studio 2015\projects\consoleapplication1\consoleapplication2\consoleapplication2.cpp	31
```

## Ref
- [std::unordered_map](https://en.cppreference.com/w/cpp/container/unordered_map.html)
- [Unordered Map in C++ STL](https://www.geeksforgeeks.org/cpp/unordered_map-in-cpp-stl/)
