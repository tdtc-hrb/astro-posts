---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Timeline 1x"
description: "C++ standard"
date: 2026-03-17
author: xiaobin
tags: ["C++ standard"]
---
- C++ Standard is backward compatible.
- When we say "supports C++11", it is better to use the C++17 standard.
- C++11 and later are new languages.

## Deprecated
|feature point|description|
|-|-|
|export |Used to mark a template definition exported.
</br>In C++11 see related extern template. In C++20 see related to modules.|
|register |Automatic storage duration specifier.
</br>In C++11, the keyword is reserved and unused.|
|throw()|Dynamic exception specification.
</br>In C++11, see related noexcept.|
|std::auto_ptr |Legacy smart pointer.
</br>In C++11, see related to smart pointers, particularly std::unique_ptr.|
|std::unary_function
</br>std::binary_function |Base class for function objects.
</br>In C++11, see the more general std::function.|
|std::bind1st
</br>std::bind2nd |Binds the argument(s) to the parameter of a function object.
</br>In C++11, see std::bind.|
|std::ptr_fun
</br>std::pointer_to_unary_function
</br>std::pointer_to_binary_function |Creates a function wrapper object.
</br>In C++11, see the more general std::function and std::ref.|
|std::mem_fun |Creates a member function wrapper object.
</br>In C++11, see std::mem_fn.
</br>Implicit lambda capture of this using `[=]` |In C++20 prefer capturing explicitly using `[=, this]` or `[=, *this]`.

## Compiler
- [gcc](https://gcc.gnu.org/projects/cxx-status.html)
- [msvc](https://learn.microsoft.com/en-us/cpp/overview/visual-cpp-language-conformance)
- [clang](https://clang.llvm.org/cxx_status.html)

### gcc
- gcc 8    
c++ 17

### msvc
- vs2019    
C++ 17
- vs2022    
C++ 20

### clang
- Clang 5    
C++ 17
- Clang 17    
> partial
C++ 20

## Ref
- [C++ 11](https://cppreference.com/w/cpp/11.html)
- [C++ 14](https://cppreference.com/w/cpp/14.html)
- [C++ 17](https://cppreference.com/w/cpp/17.html)
- [Modern C++ Features (C++11, C++14, C++17, C++20)](https://cognitivewaves.wordpress.com/modern-cpp-features/)
- [The Key Differences Between C++14, C++17, and C++20](https://www.geeksforgeeks.org/cpp/cpp14-vs-cpp17-vs-cpp20/)
- [C++ compiler support](https://en.cppreference.com/w/cpp/compiler_support.html)
