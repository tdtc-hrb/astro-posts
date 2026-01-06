---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'disabled Windows feature'
date: 2025-01-01
description: "禁止Windows的一些功能"
author: "xiaobin"
tags: ["Delivery Optimization", "记事本"]
---

## Delivery Optimization
> windows 10 2004+
startup -> settings: Update & security:
```
Allow downloads from other PCs : off
```
### Limit
> Advanced options
set minimum
#### Download settings
- background
```
5%
```
- foreground
```
5%
```

## 禁止记事本
1. 开始->运行->gpedit.msc->计算机配置->windows设置->安全设置->软件限制策略

2. 右键点软件限制策略->创建软件限制策略

3. 点其他规则->右键新建路径规则->
在“路径”下的空白输入框中“\%windir%\notepad.exe“（或者c盘是系统盘的情况下：c:\windows\notepad.exe)->在“安全级别”中选择“不允许”

> 附：如果你要限制.txt的程序打开，可以在路径中输入*.txt。
