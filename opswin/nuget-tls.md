---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Visual Studio 2013/2015 NuGet issue"
description: "Visual Studio 2013/2015 NuGet package management doesn't work well"
date: 2026-05-03
author: xiaobin
tags: ["tls1.2", "nuget"]
---
[Visual Studio 2013 NuGet package management doesn't work well.](https://developercommunity.visualstudio.com/t/visual-studio-2013-nuget-package-management-doesnt/1096344)
```
When I try to install nuget packages in Visual Studio 2013, 
I can’t connect to the nuget.org and can’t see any nuget packages to download and install.

Reproduce Steps:

Launch Visual Studio 2013 > Create a simple new project (maybe C# console app) 
> right-click the project > Manage NuGet Packages… > Online > All

Then you can see the “Retrieving information…” displays, but after a while, 
VS still displaying “Retrieving information”.
```

**NuGet Recommendation: Visual Studio 2017 and later!**

### Operating Systems
- query
```cmd
reg query "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v Enabled /reg:32
reg query "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v Enabled /reg:64
```
- Enabled
```cmd
reg add "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v DisabledByDefault /t REG_DWORD /d 0 /f /reg:32
reg add "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v DisabledByDefault /t REG_DWORD /d 0 /f /reg:64
reg add "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v Enabled /t REG_DWORD /d 1 /f /reg:32
reg add "HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client" /v Enabled /t REG_DWORD /d 1 /f /reg:64
```
### powershell(admin)
```cmd
reg add HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 /v SystemDefaultTlsVersions /t REG_DWORD /d 1 /f /reg:64
reg add HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319 /v SystemDefaultTlsVersions /t REG_DWORD /d 1 /f /reg:32
```
- pmc(Package Manager Console) and powershell
```
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bOR [Net.SecurityProtocolType]::Tls12
```
Note:
```
In Windows Server 2012 R2, you need to enter this command in PMC before using "Manage NuGet Packages".
```

## Ref
- [Deprecating TLS 1.0 and 1.1 on NuGet.org](https://devblogs.microsoft.com/dotnet/deprecating-tls-1-0-and-1-1-on-nuget-org/)
