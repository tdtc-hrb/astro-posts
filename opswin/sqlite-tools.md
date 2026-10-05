---
layout: ../../layouts/MarkdownPostLayout.astro
title: "打开不同的sqlite tool"
description: "rc4: sqlite expert; chacha20(etc.): wxSQLite"
date: 2026-02-26
author: xiaobin
tags: ["SQLite 3"]
---

Since version 1.0.113.0 the public System.Data.SQLite package does not support its prior RC4 encryption 
any longer due to the removal of the SQLITE_HAS_CODEC interface in SQLite version 3.32.0.

## Tools
- [SQLiteStudio](https://sourceforge.net/projects/sqlitestudio.mirror)
- [SQLite Expert](http://www.sqliteexpert.com/download.html)

#### About wxSQLite3
SQLite Expert does not support wxSQLite and SQLCipher

#### About Sqlit Cipher
[DBrowser](https://github.com/sqlitebrowser/sqlitebrowser/releases) supports SQLCipher version 4.6.1; 
the latest [SQLCipher](https://github.com/sqlcipher/sqlcipher/releases) version is 4.13.

### SQLiteStudio
```
Database -> add a database
```
- database type: 
WxSQLite3
- Cipher: 
System.Data.SQLite:RC4

### SQLite Expert
First, copy the old version(v1.0.112) of System.Data.SQLite.dll to the bin directory; 

For example, the bin directory of the professional version:
```
C\Program Files (x86)\SQLite Expert\Professional 5
```

- SQLite library
```
Tools -> Options
```
choose:
```
System.Data.SQLite.dll 3.30.1 [FTS3 FTS4 RTREE ENC2]
```

## Ref
- [wxSQLite3 4.6.0 released](https://forums.wxwidgets.org/viewtopic.php?t=47449)
- [Open encrypted SQLite database with SQLiteStudio](https://stackoverflow.com/questions/49048770/open-encrypted-sqlite-database-with-sqlitestudio#comment140308593_70102978)
