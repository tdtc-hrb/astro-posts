---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Virtual destructors"
description: "C++98 standard"
date: 2026-01-12
author: xiaobin
tags: ["C++ standard"]
---
- IDE: VS2013

You should always make your destructors virtual if you’re dealing with inheritance.

### Incorrect result
```
#include <iostream>
class Base
{
public:
    ~Base() // note: not virtual
    {
        std::cout << "Calling ~Base()\n";
    }
};

class Derived: public Base
{
private:
    int* m_array {};

public:
    Derived(int length)
      : m_array{ new int[length] }
    {
    }

    ~Derived() // note: not virtual (your compiler may warn you about this)
    {
        std::cout << "Calling ~Derived()\n";
        delete[] m_array;
    }
};

int main()
{
    Derived* derived { new Derived(5) };
    Base* base { derived };

    delete base;

    return 0;
}
```
output:
```
Calling ~Base()
```
This is not the result we wanted!

### Correct result
```
#include <iostream>
class Base
{
public:
    ~Base() // note: not virtual
    {
        std::cout << "Calling ~Base()\n";
    }
};

class Derived: public Base
{
private:
    int* m_array {};

public:
    Derived(int length)
      : m_array{ new int[length] }
    {
    }

    ~Derived() // note: not virtual (your compiler may warn you about this)
    {
        std::cout << "Calling ~Derived()\n";
        delete[] m_array;
    }
};

int main()
{
    Derived* derived { new Derived(5) };
    Base* base { derived };

    delete base;

    return 0;
}
```
output:
```
Calling ~Derived()
Calling ~Base()
```
This is the result we wanted!


#### Rule
Whenever you are dealing with inheritance, you should make any explicit destructors virtual.

### Should we make all destructors virtual?
This is a common question asked by new programmers. As noted in the top example, if the base class destructor isn’t marked as virtual, 
then the program is at risk for leaking memory if a programmer later deletes a base class pointer that is pointing to a derived object. 
One way to avoid this is to mark all your destructors as virtual. But should you?

It’s easy to say yes, so that way you can later use any class as a base class -- but there’s a performance 
penalty for doing so (a virtual pointer added to every instance of your class). 
So you have to balance that cost, as well as your intent.

We’d suggest the following: If a class isn’t explicitly designed to be a base class, 
then it’s generally better to have no virtual members and no virtual destructor. The class can still be used via composition. 
If a class is designed to be used as a base class and/or has any virtual functions, then it should always have a virtual destructor.


## Ref
- [25.4 — Virtual destructors, virtual assignment, and overriding virtualization](https://www.learncpp.com/cpp-tutorial/virtual-destructors-virtual-assignment-and-overriding-virtualization)
