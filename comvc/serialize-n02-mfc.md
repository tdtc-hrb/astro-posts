---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Constructors and member initializer lists - C++"
description: "Initialization order"
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
```
#include <iostream>

using namespace std;

struct S
{
    int n;

    S(int);       // constructor declaration

    S() : n(7) { cout << n << endl; } // constructor definition:
    // ": n(7)" is the initializer list
    // ": n(7) {}" is the function body
};

S::S(int x) : n{ x } { cout << n; } // constructor definition: ": n{x}" is the initializer list

int main()
{
    S s;      // calls S::S()
    S s2(10); // calls S::S(int)
}
```
output:
```
7
10
```

### { and } , ( and )
- x(x),     // x (member) is initialized with x (parameter)
- y{0},     // y initialized to 0
```
#include <fstream>
#include <string>
#include <mutex>
 
struct Base
{
    int n;
};   
 
struct Class : public Base
{
    unsigned char x;
    unsigned char y;
    std::mutex m;
    std::lock_guard<std::mutex> lg;
    std::fstream f;
    std::string s;
 
    Class(int x) : Base{123}, // initialize base class
        x(x),     // x (member) is initialized with x (parameter)
        y{0},     // y initialized to 0
        f{"test.cc", std::ios::app}, // this takes place after m and lg are initialized
        s(__func__), // __func__ is available because init-list is a part of constructor
        lg(m),    // lg uses m, which is already initialized
        m{}       // m is initialized before lg even though it appears last here
    {}            // empty compound statement
 
    Class(double a) : y(a + 1),
        x(y), // x will be initialized before y, its value here is indeterminate
        lg(m)
    {} // base class initializer does not appear in the list, it is
       // default-initialized (not the same as if Base() were used, which is value-init)
 
    Class()
    try // function try block begins before the function body, which includes init list
      : Class(0.0) // delegate constructor
    {
        // ...
    }
    catch (...)
    {
        // exception occurred on initialization
    }
};
 
int main()
{
    Class c;
    Class c1(1);
    Class c2(0.1);
}
```

### [ConnectString - MFC Class](https://tdtc-hrb.github.io/com-vc/posts/serialize-n01-mfc)
- No parameter
```
CConnectString();
```
- parameter
```
CConnectString(CString srv, CString db, CString user, CString password, int iType);
```
#### impl
- Assign a null value
```
CConnectString::CConnectString()
    : Server(_T("")), Db(_T("")), User(_T("")), Pwd(_T("")), Type(0)
{
}
```
- Assign a specified value
```
CConnectString::CConnectString(CString srv, CString db, CString user, CString password, int iType)
    : Server(srv), Db(db), User(user), Pwd(password), Type(iType)
{
}
```

## Ref
- [Constructors and member initializer lists](https://en.cppreference.com/w/cpp/language/initializer_list.html)
- [Constructors (C++)](https://learn.microsoft.com/en-us/cpp/cpp/constructors-cpp?view=msvc-170)
