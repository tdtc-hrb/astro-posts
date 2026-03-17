---
layout: ../../layouts/MarkdownPostLayout.astro
title: "SQL Server 2000数据库 安装"
description: "MS Database 迁移之一"
date: 2025-12-15
author: xiaobin
tags: ["SQL Server 2005", "SQL Server 2000"]
---
- Windows Server 2003 R2 简体中文(x86)

### Migrate
- [SQL Server 2014: Hardware and Software Requirements](https://learn.microsoft.com/en-us/previous-versions/sql/2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014)
- [How to migrate a database from SQL Server 2000 to SQL server 2022 without paying for all the versions inbetween](https://learn.microsoft.com/en-us/answers/questions/1486928/how-to-migrate-a-database-from-sql-server-2000-to)

升级路线图：
```
SQL 2000 -> SQL 2005(x86)
SQL 2005(x64) -> SQL 2014(x64)
```
x64平台建议： Windows Server 2008 R2

## instation
SQL Server 2000 Developer Edition (Chinese-Simplified)
```
ed2k://|file|sc_sql_2000a_dev.iso|476665856|FC321271C84BD389F862C0D580B4ECC7|/
```
### 安装服务器组件
![require sp3](https://github.com/tdtc-hrb/csdn/raw/master/images/sp3req-sql2k0.png)

![welcome 1a](https://github.com/tdtc-hrb/csdn/raw/master/images/step1a-sql2k0.png)

![welcome 1b](https://github.com/tdtc-hrb/csdn/raw/master/images/step1b-sql2k0.png)

![welcome 2a](https://github.com/tdtc-hrb/csdn/raw/master/images/step2a-sql2k0.png)

![welcome 2b](https://github.com/tdtc-hrb/csdn/raw/master/images/step2b-sql2k0.png)

#### 本地账户
![welcome 2c](https://github.com/tdtc-hrb/csdn/raw/master/images/step2c-sql2k0.png)
#### sa
> default password: pass2word1

![welcome 2d](https://github.com/tdtc-hrb/csdn/raw/master/images/step2d-sql2k0.png)

### SP4
- [sp4-chs](http://download.microsoft.com/download/9/b/f/9bff6646-2cdb-4069-ada0-548be9cb9338/SQL2000-KB884525-SP4-x86-CHS.EXE)

安装SQL2000-KB884525-SP4-x86-CHS.EXE后，默认解压的目录为："C:\SQL2KSP4"; 
进入该目录，双击"setup.bat"即可。
