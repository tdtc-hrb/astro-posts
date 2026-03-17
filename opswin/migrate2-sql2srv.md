---
layout: ../../layouts/MarkdownPostLayout.astro
title: "SQL Server 2005数据库 安装"
description: "MS Database 迁移之二"
date: 2025-12-15
author: xiaobin
tags: ["SQL Server 2005", "SQL Server 2000"]
---
- Windows Server 2003 R2 简体中文(x86)

### 安装介质
- VHD
- [MSDN](https://msdn.itellyou.cn)    
只有中文版

#### VHD
- [Windows Server 2008 w/ SQL Server 2005](https://www.microsoft.com/en-us/download/details.aspx?id=1367)
- Microsoft Virtual PC 2007 (x64) (English)    
 无法运行在 [Win10](http://www.win3x.org/win3board/viewtopic.php?t=19227)

#### MSDN
开发版DVD SQL Server 2005 Developer Edition（32 位和 64 位）
```
ed2k://|file|cs_sql_2005_dev_all_dvd.iso|1870581760|25D3E5CEFB407E7CA1036BE303AC4643|/
```

#### Service Package
- [Microsoft SQL Server 2005 Service Pack 4 (KB2463332)](https://catalog.update.microsoft.com/search.aspx?q=kb2463332)

![Service Pack 4](https://github.com/tdtc-hrb/csdn/raw/master/images/sp4req-sql2k5.png)

下载 x64 和 x86 版本。
## instation
- .net framework 2.0    
[Microsoft .NET Framework 2.0 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=16614)
- IIS

![iis require](https://github.com/tdtc-hrb/csdn/raw/master/images/iis1-sql2k5.png)

![iis - add feature](https://github.com/tdtc-hrb/csdn/raw/master/images/iis2-sql2k5.png)

### 安装升级顾问
![Upgrade Advisor](https://github.com/tdtc-hrb/csdn/raw/master/images/ua-sql2k5.png)

### 安装服务器组件
![wecome 1](https://github.com/tdtc-hrb/csdn/raw/master/images/step1-sql2k5.png)

![wecome 2](https://github.com/tdtc-hrb/csdn/raw/master/images/step2a-sql2k5.png)

![wecome 2b](https://github.com/tdtc-hrb/csdn/raw/master/images/step2b-sql2k5.png)

#### 本地账户
![wecome 2c](https://github.com/tdtc-hrb/csdn/raw/master/images/step2c-sql2k5.png)
#### sa
> default password: pass2word1

![wecome 2d](https://github.com/tdtc-hrb/csdn/raw/master/images/step2d-sql2k5.png)
#### 排序规则
![wecome 2e](https://github.com/tdtc-hrb/csdn/raw/master/images/step2e-sql2k5.png)
