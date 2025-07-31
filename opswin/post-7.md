---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Enterprise Architect"
description: "design-patterns, gof"
date: 2023-11-30
author: xiaobin
tags: ["faq3", "GoF"]
---
[china mirror - EA](http://tool.uml.com.cn/ToolsEA/download.asp):
- [v16.1](http://tool.uml.com.cn/ToolsEA/ea16.1/easetup_x86.msi)

## class view
"Model" 点击右键 "add view":
```
Initial Content: Package Only
```
name: <design-patterns name>

### import code
切换到 "Develop" 选项卡；
在"Source Code" -> Files:
```
Import Source Directory
```
- Package    
所有的代码放入一个包内； 这样在导入代码的时候，会生成类图。

### Generic Type
需要手动放置<code>Associate</code> 并设置 "Direction":
```
Source -> Destination
```

### 折线
按住“CTRL” + 点击鼠标左键


## issues
- sandboxie

### sandboxie
> v1.12.3
使用 v16.1时，无法关闭剩余进程


# GoF
> Alt + 5
>> enter: gof
```
Design > Diagram > Toolbox
```

## Creational Design Pattern
- [Prototype](https://sourcemaking.com/design_patterns/prototype)
![dp prototype](https://github.com/tdtc-hrb/cnblogs/raw/master/images/dp-prototype.png)
- [Abstract Factory](https://sourcemaking.com/design_patterns/abstract_factory)
![dp abstract factory](https://github.com/tdtc-hrb/cnblogs/raw/master/images/dp-abstr_factory.png)


### Prototype
- Specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.
- Co-opt one instance of a class for use as a breeder of all future instances.
- The <code>new</code> operator considered harmful.

### Abstract Factory
Abstract Factory classes are often implemented with Factory Methods, 
but they can also be implemented using Prototype.    
Abstract Factory might store a set of Prototypes from which to clone and return product objects.

- Factory Method: creation through inheritance.
- Prototype: creation through delegation.
- Virtual constructor: defer choice of object to create until run-time.


# Ref
- [Diagram Toolbox](https://sparxsystems.com/enterprise_architect_user_guide/14.0/modeling_tools/objecttoolbar.html)
