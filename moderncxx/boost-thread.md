---
layout: ../../layouts/MarkdownPostLayout.astro
title: "thread库 - boost"
description:  "Portable C++ multi-threading. C++11, C++14, C++17."
date: 2026-02-18
author: "tdtc"
---
A note to MinGW users: 
not supported—they may or may not work.

### [Example 44.1. Using boost::thread](https://theboostcpplibraries.com/boost.thread-management#ex.thread_01)
```c++
#include <boost/thread.hpp>
#include <boost/chrono.hpp>
#include <iostream>

void wait(int seconds)
{
    boost::this_thread::sleep_for(boost::chrono::seconds{ seconds });
}

void thread()
{
    for (int i = 0; i < 5; ++i)
    {
        wait(1);
        std::cout << i << std::endl;
    }
}

int main()
{
    boost::thread t{ thread };
    t.join();
}
```

## Ref
- [Boost.Thread](https://www.boost.org/library/latest/thread/)
- [The Boost C++ Libraries](https://theboostcpplibraries.com/)
- [Creating and Managing Threads](https://theboostcpplibraries.com/boost.thread-management)
- [Getting Started on Windows](https://www.boost.org/doc/libs/latest/more/getting_started/windows.html)
