---
layout: ../../layouts/MarkdownPostLayout.astro
title: "arguments - template"
description: "C++ standard"
date: 2026-03-20
author: xiaobin
tags: ["C++ standard"]
---
In order for a template to be instantiated, every template parameter must be replaced by a corresponding template argument. 
The arguments are either explicitly provided, deduced or defaulted.

Each parameter in template-parameter-list (see template identifier syntax) belongs to one of the following categories:
- constant template argument
- type template argument
- template template argument

```
// templateTypeDeduction.cpp

template <typename T>
void funcValue(T param) { }

template <typename T>
void funcReference(T& param) { }

template <typename T>
void funcUniversalReference(T&& param) { }

class RVal{};

int main() {

    const int lVal{};
    const int& ref = lVal;
  
    funcValue(lVal);                  // (1)
    funcValue(ref);
  
    funcReference(lVal);              // (2)
  
    funcUniversalReference(lVal);     // (3)
    funcUniversalReference(RVal());

}
```

## Ref
- [template-arguments](https://www.modernescpp.com/index.php/template-arguments/)
- [args - template](https://en.cppreference.com/w/cpp/language/template_arguments.html)
