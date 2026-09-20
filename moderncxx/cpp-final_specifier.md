---
layout: ../../layouts/MarkdownPostLayout.astro
title: "C++ final Specifier"
description: "C++11 standard"
date: 2026-01-12
author: xiaobin
tags: ["C++ standard"]
---
- IDE: VS2013

In Java, we can use final for a function to make sure that it cannot be overridden. 
We can also use final in Java to make sure that a class cannot be inherited. 
Similarly, the latest C++ standard C++ 11 added final.

### method
```
#include "stdafx.h"
#include <iostream>
using namespace std;

class Base
{
public:
    virtual void myfun() final
    {
        cout << "myfun() in Base";
    }
};
class Derived : public Base
{
    void myfun()
    {
        cout << "myfun() in Derived\n";
    }
};

int main()
{
    Derived d;
    Base &b = d;
    b.myfun();
    return 0;
}
```
output:
```
Error	1	error C3248: 'Base::myfun': function declared as 'final' cannot be overridden by 'Derived::myfun'
c:\users\hp25nov\documents\visual studio 2013\projects\consoleapplication2\consoleapplication2\consoleapplication2.cpp	18	1	ConsoleApplication2

```

### class
```
#include "stdafx.h"
#include <iostream>
class Base final
{
};

class Derived : public Base
{
};

int main()
{
    Derived d;
    return 0;
}
```
output:
```
Error	1	error C3246: 'Derived' : cannot inherit from 'Base' as it has been declared as 'final'	
c:\users\hp25nov\documents\visual studio 2013\projects\consoleapplication3\consoleapplication3\consoleapplication3.cpp	11	1	ConsoleApplication3
```

## Ref
- [C++ final Specifier](https://www.geeksforgeeks.org/cpp/c-final-specifier/)
- [final specifier (since C++11)](https://en.cppreference.com/w/cpp/language/final.html)
