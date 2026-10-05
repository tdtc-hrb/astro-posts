---
layout: ../../layouts/MarkdownPostLayout.astro
title: "noexcept - c++"
description: "C++11 standard"
date: 2026-04-05
author: xiaobin
tags: ["C++ standard"]
---
- `noexcept` is primarily used in inheritance.
- Sometimes it needs to be used in conjunction with `const`.

## Example
```
// C++ Program to demonstrate
// use of use of the noexcept specifier
#include <iostream>
using namespace std;

// Function that may throw an exception
int divide(int a, int b)
{
    if (b == 0) {
        throw runtime_error("Error: Division by zero");
    }
    return a / b;
}

// Function that will not throw any exceptions (using
// noexcept)
double safeDivide(double a, double b) noexcept
{
    if (b == 0) {
        // In this case, std::terminate will be called if b
        // is zero
        cerr << "Error: Division by zero in safeDivide"
             << std::endl;
        terminate();
    }
    return a / b;
}

int main()
{
    cout << "noexcept value for divide(): "
         << noexcept(divide(10, 0)) << "\n";

    cout << "noexcept value for safeDivide(): "
         << noexcept(safeDivide(10.0, 0.0));

    return 0;
}
```

## Ref
- [noexcept operator](https://en.cppreference.com/w/cpp/language/noexcept.html)
- [noexcept specifier](https://en.cppreference.com/w/cpp/language/noexcept_spec.html)
- [noexcept Operator in C++ 11](https://www.geeksforgeeks.org/cpp/noexcept-operator-in-cpp-11/)
- [Noexcept Specifier in C++17](https://www.geeksforgeeks.org/cpp/noexcept-specifier-in-cpp-17/)
- [27.9 — Exception specifications and noexcept](https://www.learncpp.com/cpp-tutorial/exception-specifications-and-noexcept/)


# const noexcept - google ai
In C++, const and noexcept are common qualifiers for member functions 
that serve different purposes: const guarantees the function won't modify the object's state, 
while noexcept guarantees it won't throw an exception. [1, 2] 
## Key Differences & Roles

| Feature [1, 2, 3, 4, 5, 6] | const | noexcept |
|---|---|---|
| Purpose | Logical constancy: Promises the function won't change data members. | Exception safety: Promises the function won't let exceptions propagate out. |
| Enforcement | Compile-time: The compiler prevents modifications to members (unless they are mutable). | Runtime: If an exception is thrown, the program calls std::terminate immediately. |
| Optimization | Minimal; mostly for "const-correctness" and code safety. | High; allows the compiler to skip stack unwinding logic and enables faster move semantics in containers. |

## Syntax and Order
When used together in a member function, the const qualifier must come before the noexcept specifier. [7, 8] 
```
class MyClass {
    int value = 0;
public:
    // Correct order: const then noexcept
    int getValue() const noexcept {
        return value;
    }
};
```
## Why Use Them Together?

   1. Interface Clarity: You are telling users (and the compiler) that calling this function 
   is "purely observational" and "guaranteed safe" from crashes or errors.
   2. Performance with Standard Containers: If a class has noexcept move constructors, 
   containers like std::vector can move elements instead of copying them during a resize, 
   providing a massive performance boost.
   3. Compiler Optimizations: By marking a function noexcept, 
   the compiler doesn't need to generate the complex "unwinding" code required to handle potential exceptions, 
   resulting in smaller and faster binaries. [1, 3, 4, 9] 

## Important Note on noexcept
Unlike const, which is checked at compile-time, 
the compiler does not always check if a noexcept function actually contains code that might throw. 
If you mark a function noexcept and it does throw an exception, your program will crash. [6, 9, 10, 11] 
Would you like to see how to use the noexcept operator to check these properties at compile-time?

[1] [https://www.geeksforgeeks.org](https://www.geeksforgeeks.org/cpp/noexcept-specifier-in-cpp-17/)
[2] [https://www.naukri.com](https://www.naukri.com/code360/library/const-keyword-in-cpp)
[3] [https://en.cppreference.com](https://en.cppreference.com/w/cpp/language/noexcept_spec.html)
[4] [https://www.youtube.com](https://www.youtube.com/watch?v=2xHfTLbEkko)
[5] [https://stackoverflow.com](https://stackoverflow.com/questions/10787766/when-should-i-really-use-noexcept)
[6] [https://stackoverflow.com](https://stackoverflow.com/questions/33210169/how-to-use-noexcept-in-c-or-how-does-it-work)
[7] [https://stackoverflow.com](https://stackoverflow.com/questions/60239765/why-when-i-write-noexcept-before-const-i-get-an-error)
[8] [https://arne-mertz.de](https://arne-mertz.de/2016/01/modern-c-features-keyword-noexcept/)
[9] [https://www.modernescpp.com](https://www.modernescpp.com/index.php/c-core-guidelines-the-noexcept-specifier-and-operator/)
[10] [https://learn.microsoft.com](https://learn.microsoft.com/fr-fr/cpp/cpp/noexcept-cpp?view=msvc-170)
[11] [https://www.youtube.com](https://www.youtube.com/watch?v=NCa-QKf5MZ8)
