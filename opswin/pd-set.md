---
layout: ../../layouts/MarkdownPostLayout.astro
title: "PowerDesigner设置"
description: "PowerDesigner设置"
date: 2025-04-29
author: xiaobin
tags: ["Power Designer"]
---

# Gen pdm
> need JAVA_HOME(x86)

CDM-〉PDM转换的时候提示属性错误，
请把PDM GENERATION OPTIONS中的Check model钩取消掉.

## setup connection profile
```bash
jdbc driver class: com.mysql.jdbc.Driver
jdbc connection url: jdbc:mysql://106.14.141.40:3306/crm
jdbc driver jar file: D:\war\cas-server\lib\mysql-connector-java-5.1.49.jar
```

## gen pdm
- connect database
  
- reverse    
File -> Reverse engineer


## PowerDesigner设置code和name不联动的方法
tool->general option ->dialog    
"Name to code mirroring"勾号取掉

## 同名问题
“tool”-〉“Model Option”-〉“Model Setting”    
“Data Item”中的复选框    
“Unique code”和"Allow reuse"取消掉。

## [大小写问题](https://stackoverflow.com/questions/1174183/powerdesigner-prevent-db-name-to-be-uppercase-in-generated-sql)
1) Right-click on an empty spot in the model area.
2) Select "Model Options..." from the context menu.
3) Select "Naming Convention" from the tree.
4) Select "Code" from the tab group.
5) Select "Mixed case" beside "Character case".
6) Click OK.
