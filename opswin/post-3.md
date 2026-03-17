---
layout: ../../layouts/MarkdownPostLayout.astro
title: 文件或目录
author: xiaobin
description: "无法读取的所在逻辑盘; 以及删除老的windows文件夹"
date: 2025-02-01
tags: ["逻辑盘", "Old Windows Folder"]
---

## 文件或目录损坏且无法读取
> [无法读取的所在逻辑盘E:](https://www.cnblogs.com/hf1432/p/5643193.html)
```bash
chkdsk /F E:
```

## How to Delete Old Windows Folder in Windows 10 – Access Denied?
```bash
takeown /F "C:\Windows.old" /A /R /D Y
icacls "C:\Windows.old" /T /grant administrators:F
rmdir /s /q "C:\Windows.old"
```
