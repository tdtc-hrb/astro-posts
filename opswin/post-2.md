---
layout: ../../layouts/MarkdownPostLayout.astro
title: 日文系统
author: xiaobin
description: "日文windows"
date: 2025-01-16
tags: ["英文键盘", "win7添加日文"]
---

## key101
> 日文改英文键盘

修改注册表主键：
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\i8042prt\Parameters
```bash
LayerDriver JPN: KBD101.DLL

OverrideKeyboardIdentifier: PCAT_101KEY
OverrideKeyboardSubtype:    0x00000000(0)
```

## [win7+添加日文输入](https://jingyan.baidu.com/article/e75aca855ed81f142fdac665.html)

1. “区域和语言“ ==> ”键盘和语言“

2. ”键盘和语言“中，点击”更改键盘“，
  点”添加“，找到 ”日语（日本）“，    
  勾选”Microsoft IME“和”日语“，其它不要勾选.

按键盘”Alt“+”Shift“即可调出日语输入法.
