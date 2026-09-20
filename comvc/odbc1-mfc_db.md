---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC1 - MFC"
description: "Begin ODBC"
date: 2025-12-19
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
In the long run, ODBC will inevitably replace OLE DB as the mainstream driver in MS SQL Server.

1. Cross-platform
2. similar to JDBC

### [SQL Server versions and ODBC and OLE DB drivers](https://learn.microsoft.com/en-us/sql/connect/connect-history?view=sql-server-ver17#sql-server-versions-and-odbc-and-ole-db-drivers)
|SQL Server Version|ODBC Driver|OLE DB Provider|Notes|
|-|-|-|-|
|SQL Server 2000|SQL Server ODBC Driver (legacy)|SQL Server OLE DB Provider (legacy)|Deprecated|
|SQL Server 2014|Microsoft ODBC Driver 11 for SQL Server|SQL Native Client 11.0 (deprecated)|SNAC/OLE DB deprecated|
|SQL Server 2016|Microsoft ODBC Driver 13|SQL Native Client 11.0 (deprecated)|ODBC maintained OLE DB deprecated|
|SQL Server 2017|Microsoft ODBC Driver 13.1 (14)|SQL Native Client 11.0 (deprecated)|OLE DB deprecated|
|SQL Server 2019|Microsoft ODBC Driver 17|Microsoft OLE DB Driver (MSOLEDBSQL)|OLE DB undeprecated/reintroduced|
|SQL Server 2022|Microsoft ODBC Driver 17|Microsoft OLE DB Driver (MSOLEDBSQL)|Actively maintained|
|SQL Server 2025|Microsoft ODBC Driver 18|Microsoft OLE DB Driver 19 (MSOLEDBSQL19)|Actively maintained|

#### [Release Notes for Microsoft ODBC Driver for SQL Server on Windows](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#previous-releases)
- [ODBC 11](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#11)
- [ODBC 13](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#13)
- [ODBC 13.1](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#131)
- [ODBC 17](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#170)
- [ODBC 18](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#180)

### Cross-platform
- [Install the Microsoft ODBC driver for SQL Server (macOS)](https://learn.microsoft.com/en-us/sql/connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos?view=sql-server-ver17)
- [Install the Microsoft ODBC driver for SQL Server (Linux)](https://learn.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-ver17)

## Ref
- [Ole DB 未弃用](https://learn.microsoft.com/zh-cn/archive/blogs/sqlnativeclient/announcing-the-new-release-of-ole-db-driver-for-sql-server)
- [SQL version compatibility](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver17#sql-version-compatibility)
