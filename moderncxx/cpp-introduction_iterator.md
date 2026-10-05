---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Introduction to Iterators in C++"
description: "Reprinted from geeksforgeeks.org"
date: 2026-03-16
author: xiaobin
tags: ["C++ standard"]
---
|CONTAINER|TYPES OF ITERATOR SUPPORTED|
|-|-|
|Vector|Random-Access|
|List|Bidirectional|
|Deque|Random-Access|
|Map|Bidirectional|
|Multimap|Bidirectional|
|Set|Bidirectional|
|Multiset|Bidirectional|
|Stack|No iterator Supported|
|Queue|No iterator Supported|
|Priority-Queue|No iterator Supported|

### Types of Iterators
![](https://media.geeksforgeeks.org/wp-content/uploads/20260120103112159278/random_access.webp)
#### Bidirectional
This iterator can move in both direction either in forward or backward. Alos it's have all functionalities of forward iterators.
#### Random-Access
Random-access iterators are iterators that can be used to access the element at the distance from the element they pointed to. 
And it's had all functionalities of bidirectional iterators.

#### Input
It is a read only iterator but not modified the value using input iterator.
#### Output
Output iterator is used to assign the values.
#### Forward
It is the combination of input and output iterator means for both access and assigning the values.

### Example
```
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1,2,3,4,5};

    // Get the iterator of first element of the vector
    vector<int>::iterator it = v.begin();

    for (; it != v.end(); ++it) {
        cout << *it << " ";
    }

    return 0;
}
```

## Ref
- [Introduction to Iterators in C++](https://www.geeksforgeeks.org/cpp/introduction-iterators-c/)
