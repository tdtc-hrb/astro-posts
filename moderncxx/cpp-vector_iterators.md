---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The C++ Equivalent to Java’s ArrayList: Exploring std::vector"
description: "C++11 standard"
date: 2026-01-12
author: xiaobin
tags: ["C++ standard"]
---
- IDE: VS2013

## Iterators
- [begin()](https://en.cppreference.com/w/cpp/container/vector/begin.html)
- [end()](https://en.cppreference.com/w/cpp/container/vector/end.html)
- [rbegin()](https://en.cppreference.com/w/cpp/container/vector/rbegin.html)
- [rend()](https://en.cppreference.com/w/cpp/container/vector/rend.html)

### normal
```
#include "stdafx.h"
#include <algorithm>
#include <iostream>
#include <numeric>
#include <string>
#include <vector>

int main()
{
	std::vector<int> nums{ 1, 2, 4, 8, 16 };
	std::vector<std::string> fruits{ "orange", "apple", "raspberry" };
	std::vector<char> empty;

	// Print vector.
	std::for_each(nums.begin(), nums.end(), [](const int n) { std::cout << n << ' '; });
	std::cout << '\n';

	// Sums all integers in the vector nums (if any), printing only the result.
	std::cout << "Sum of nums: "
		<< std::accumulate(nums.begin(), nums.end(), 0) << '\n';

	// Prints the first fruit in the vector fruits, checking if there is any.
	if (!fruits.empty())
		std::cout << "First fruit: " << *fruits.begin() << '\n';

	if (empty.begin() == empty.end())
		std::cout << "vector 'empty' is indeed empty.\n";
}
```
output:
```
1 2 4 8 16
Sum of nums: 31
First fruit: orange
vector 'empty' is indeed empty.
```

### reverse
```
#include "stdafx.h"
#include <algorithm>
#include <iostream>
#include <numeric>
#include <string>
#include <vector>
 
int main()
{
    std::vector<int> nums{1, 2, 4, 8, 16};
    std::vector<std::string> fruits{"orange", "apple", "raspberry"};
    std::vector<char> empty;
 
    // Print vector.
    std::for_each(nums.rbegin(), nums.rend(), [](const int n) { std::cout << n << ' '; });
    std::cout << '\n';
 
    // Sums all integers in the vector nums (if any), printing only the result.
    std::cout << "Sum of nums: "
              << std::accumulate(nums.rbegin(), nums.rend(), 0) << '\n';
 
    // Prints the first fruit in the vector fruits, checking if there is any.
    if (!fruits.empty())
        std::cout << "First fruit: " << *fruits.rbegin() << '\n';
 
    if (empty.rbegin() == empty.rend())
        std::cout << "vector 'empty' is indeed empty.\n";
}
```
output:
```
16 8 4 2 1
Sum of nums: 31
First fruit: raspberry
vector 'empty' is indeed empty.
```

## Ref
- [The C++ Equivalent to Java’s ArrayList: Exploring std::vector](https://medium.com/@adam.rizk9/the-c-equivalent-to-javas-arraylist-exploring-std-vector-b3a4afc8e9c6)
- [What's the C++ version of Java's ArrayList](https://stackoverflow.com/questions/3971049/whats-the-c-version-of-javas-arraylist)
- [std::vector](https://en.cppreference.com/w/cpp/container/vector.html)
