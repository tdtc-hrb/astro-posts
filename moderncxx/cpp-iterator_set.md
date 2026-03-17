---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Iterator - C++"
description: "C++11 standard"
date: 2026-03-16
author: xiaobin
tags: ["C++ standard"]
---
They are declared as container_type::iterator it; or auto it = container.begin();.

### Set
```
#include <iostream>
#include <set>
using namespace std;

int main()
{
    set<int> s = {10, 20, 30, 40, 50};

    // Iterator to the beginning of the set
    auto it = s.begin();

    // Iterating through the set
    while (it != s.end())
    {
        // Accessing value via iterator
        cout << *it << " ";

        // Moving to the next element
        ++it;
    }

    return 0;
}
```
- iterator
```
    set<int>::iterator it2 = s.begin();

    while (it2 != s.end()) {
        cout << *it2 << " ";
        ++it2;
    }
```

## Ref
- [Iterators in C++ STL](https://www.geeksforgeeks.org/cpp/iterators-c-stl)
- [Introduction to Iterators in C++](https://www.geeksforgeeks.org/cpp/introduction-iterators-c/)
