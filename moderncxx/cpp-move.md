---
layout: ../../layouts/MarkdownPostLayout.astro
title: "move - C++"
description: "C++11 standard"
date: 2026-03-17
author: xiaobin
tags: ["C++ standard"]
---
Move semantics is a feature that allows our program to transfer ownership of resources (like memory, files, etc.) 
from one object to another instead of copying them. This results iin:
- Faster performance
- Less memory usage
- Better efficiency, especially with big objects (like std::vector, std::string, or file streams)

### Move Semantics in STL Containers
One of the most practical and important uses of move semantics is in standard library containers like std::vector, std:: map, std:: set and others. 
These containers use move operations internally to improve performance and avoid unnecessary copying.

STL containers like std::vector use move semantics to improve performance in two main cases:

1. During Reallocation

When a container grows and needs more space, it reallocates memory transfers existing elements.
If the element type supports move, the container moves elements instead of copying them - making reallocation faster.

2. When Inserting Elements

Move semantics are also used when inserting elements:
- push_back(std::move(x)) - Moves an existing object into the container.
- emplace_back(args...) - Constructs the object directly in-place, avoiding copies or moves.

Example:
```
std::string temp = "Alice";
// Moves temp into vector
names.push_back(std::move(temp)); 
// Constructs "Bob" directly in vector
names.emplace_back("Bob");
```
These operations reduce unnecessary copying and make insertion more efficient. 

## Ref
- [std::move](https://en.cppreference.com/w/cpp/utility/move.html)
- [Move Semantics in C++](https://www.geeksforgeeks.org/cpp/stdmove-in-utility-in-c-move-semantics-move-constructors-and-move-assignment-operators/)
