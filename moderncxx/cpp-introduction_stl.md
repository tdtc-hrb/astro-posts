---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Standard Template Library (STL) in C++"
description: "Reprinted from geeksforgeeks.org"
date: 2026-03-16
author: xiaobin
tags: ["C++ standard"]
---
STL is a collection of pre-built classes and functions that make it easy to manage data using common data structures like vectors, stacks, and maps. 
It saves time and effort by providing ready-to-use, efficient algorithms and containers.

### Components of STL
The components of STL are the features provided by STL in C++ that can be classified into 3 types:
![](https://media.geeksforgeeks.org/wp-content/uploads/20250818102717729926/components_of_stl.webp)
These components are designed to be efficient, flexible, and reusable, making them an integral part of modern C++ programming. 
### Containers
Containers can be further classified into 4 types:
- Sequence Containers : Vector, Deque, List, Forward List, Array
- Container Adaptors : Stack, Queue, Priority Queue
- Associative Containers : Set, Multiset, Map, Multimap
- Unordered Associated Containers : Unordered Set, Unordered Multiset, Unordered Map, Unordered Multimap

### Algorithms
STL algorithms offer a wide range of functions to perform common operations on data (mainly containers). 
These functions implement the most efficient version of the algorithm for tasks such as sorting, searching, modifying and manipulating data in containers, etc. 
All STL algorithms are defined inside the <algorithm> and <numeric> header file. Some of the most frequently used algorithms are:

- Sort : Arranges elements in ascending order (default).
- Binary Search : Checks whether a value exists in a sorted range.
- Find : Searches for the first occurrence of a given value.
- Count : Counts how many times a value appears in the given range.
- Reverse : Reverses the order of elements in the given range.
- Accumulate : Computes the sum of all elements in the range.
- Unique : Removes consecutive duplicate elements.
- Lower bound : Returns iterator to the first element ≥ value in a sorted range.
- Upper bound : Returns iterator to the first element > value in a sorted range.
- Replace : Replaces all occurrences of old value with new value in the given range.

### Iterators
Iterators are the pointer like objects that are used to point to the memory addresses of STL containers. 
They are one of the most important components that contributes the most in connecting the STL algorithms with the containers. 
Iterators are defined inside the <iterator> header file.

## Ref
- [Standard Template Library (STL) in C++](https://www.geeksforgeeks.org/cpp/the-c-standard-template-library-stl)
