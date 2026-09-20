---
layout: ../../layouts/MarkdownPostLayout.astro
title: "explicit - c++"
description: "C++17 standard"
date: 2026-04-05
author: xiaobin
tags: ["C++ standard"]
---
Prefixing the explicit keyword to the constructor prevents the compiler 
from using that constructor for implicit conversions. 
```
// Source - https://stackoverflow.com/a/121163
// Posted by Skizz, modified by community. See post 'Timeline' for change history
// Retrieved 2026-04-04, License - CC BY-SA 4.0

struct Foo {
    // Single parameter constructor, can be used as an implicit conversion.
    // Such a constructor is called "converting constructor".
    Foo(int x) {}
};
struct Faz {
    // Also a converting constructor.
    Faz(Foo foo) {}
};

// The parameter is of type Foo, not of type int, so it looks like
// we have to pass a Foo.
void bar(Foo foo) {};

int main() {
    // However, the converting constructor allows us to pass an int.
    bar(42);
    // Also allowed thanks to the converting constructor.
    Foo foo = 42;
    // Error! This would require two conversions (int -> Foo -> Faz).
    Faz faz = 42;
}

```

## Ref
- [explicit specifier](https://en.cppreference.com/w/cpp/language/explicit.html)
