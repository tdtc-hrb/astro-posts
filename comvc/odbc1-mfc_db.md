---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ODBC1 - MFC"
description: "Begin ODBC"
date: 2026-09-19
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
- ODBC Internal version
- ODBC Internal Protocol

### ODBC Internal version
|name|ver|file|
|-|-|-|
|Administrator|10.0.17763.1|odbccp32.dll|
|Control Panel Startup|10.0.17763.1|odbcad32.dll|
|Cursor Library|10.0.17763.1|odbccr32.dll|
|Driver Manager|10.0.17763.1|odbc32.dll|
|Localized Resource DLL|10.0.17763.1|odbcint.dll|
|Unicode Cursor Library|10.0.17763.1|odbccu32.dll|

## Protocol
- TLS
- TDS
### tls
When using older versions of SQL Server, TLS 1.0 must be enabled.
```ps
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client" -Name "Enabled" -Value 1 -Type DWord

Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server" -Name "Enabled" -Value 1 -Type DWord
```
from [ms](https://learn.microsoft.com/en-us/windows/win32/secauthn/tls-10-11-deprecation-in-windows)

### Tabular Data Stream
|TDS version |Associated Microsoft SQL Server release(s) |
|-|-|
|7.1 |SQL Server 2000 |
|7.2 |SQL Server 2005 |
|7.3A |SQL Server 2008 |
|7.3B |SQL Server 2008 R2 |
|7.4 |SQL Server 2012, 2014, 2016, 2017, 2019|
|8.0 |SQL Server 2022 and 2025 |

## Ref
- [SQL version compatibility](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver17#sql-version-compatibility)
- [SQL Server versions and ODBC and OLE DB drivers](https://learn.microsoft.com/en-us/sql/connect/connect-history?view=sql-server-ver17#sql-server-versions-and-odbc-and-ole-db-drivers)
- [Release Notes for Microsoft ODBC Driver for SQL Server on Windows](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows?view=sql-server-ver17#previous-releases)
