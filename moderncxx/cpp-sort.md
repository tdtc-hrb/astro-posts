---
layout: ../../layouts/MarkdownPostLayout.astro
title: "sort - C++"
description: "C++11 standard"
date: 2026-03-23
author: xiaobin
tags: ["C++ standard"]
---
The sort() function is used to sort elements in a container or array. It provides a simple and efficient way to sort data in C++.

- Works on random-access iterators (arrays, vectors, deques).
- Default sort is ascending order.

## sort - algorithm
```
#include <algorithm>
#include <array>
#include <functional>
#include <iostream>
#include <string_view>
 
int main()
{
    std::array<int, 10> s{5, 7, 4, 2, 8, 6, 1, 9, 0, 3};
 
    auto print = [&s](std::string_view const rem)
    {
        for (auto a : s)
            std::cout << a << ' ';
        std::cout << ": " << rem << '\n';
    };
 
    std::sort(s.begin(), s.end());
    print("sorted with the default operator<");
 
    std::sort(s.begin(), s.end(), std::greater<int>());
    print("sorted with the standard library compare function object");
 
    struct
    {
        bool operator()(int a, int b) const { return a < b; }
    }
    customLess;
 
    std::sort(s.begin(), s.end(), customLess);
    print("sorted with a custom function object");
 
    std::sort(s.begin(), s.end(), [](int a, int b)
                                  {
                                      return a > b;
                                  });
    print("sorted with a lambda expression");
}
```

## Ref
- [sort - cppreference](https://en.cppreference.com/w/cpp/algorithm/sort.html)
- [sort() in C++ STL](https://www.geeksforgeeks.org/cpp/sort-c-stl)
