---
layout: ../../layouts/MarkdownPostLayout.astro
title: "parameters - template"
description: "C++ standard"
date: 2026-03-20
author: xiaobin
tags: ["C++ standard"]
---
Every template is parameterized by one or more template parameters.

Each parameter in template-parameter-list (see [template declaration syntax](https://en.cppreference.com/w/cpp/language/templates.html#Syntax)) belongs to one of the following categories:
- constant template parameter
- type template parameter
- template template parameter

```
#include <array>
#include <iostream>
#include <numeric>
 
// simple constant template parameter
template<int N>
struct S { int a[N]; };
 
template<const char*>
struct S2 {};
 
// complicated constant example
template
<
    char c,             // integral type
    int (&ra)[5],       // lvalue reference to object (of array type)
    int (*pf)(int),     // pointer to function
    int (S<10>::*a)[10] // pointer to member object (of type int[10])
>
struct Complicated
{
    // calls the function selected at compile time
    // and stores the result in the array selected at compile time
    void foo(char base)
    {
        ra[4] = pf(c - base);
    }
};
 
//  S2<"fail"> s2;        // error: string literal cannot be used
    char okay[] = "okay"; // static object with linkage
//  S2<&okay[0]> s3;      // error: array element has no linkage
    S2<okay> s4;          // works
 
int a[5];
int f(int n) { return n; }
 
// C++20: NTTP can be a literal class type
template<std::array arr>
constexpr
auto sum() { return std::accumulate(arr.cbegin(), arr.cend(), 0); }
 
// C++20: class template arguments are deduced at the call site
static_assert(sum<std::array<double, 8>{3, 1, 4, 1, 5, 9, 2, 6}>() == 31.0);
// C++20: NTTP argument deduction and CTAD
static_assert(sum<std::array{2, 7, 1, 8, 2, 8}>() == 28);
 
int main()
{
    S<10> s; // s.a is an array of 10 int
    s.a[9] = 4;
 
    Complicated<'2', a, f, &S<10>::a> c;
    c.foo('0');
 
    std::cout << s.a[9] << a[4] << '\n';
}
```

## Ref
- [template-parameters](https://www.modernescpp.com/index.php/alias-templates-and-template-parameters/)
- [parameters - template](https://en.cppreference.com/w/cpp/language/template_parameters.html)
