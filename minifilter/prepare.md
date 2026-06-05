---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Development Environment Preparation"
description:  "visual studio 2019/2022 and vm"
date: 2026-05-31
author: "tdtc"
---
- VS2019
- VirtualBox

### [Spectre-mitigated libraries](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc)
- install
```
MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitgated libs(Latest)
```

### [WDK](https://docs.microsoft.com/en-us/windows-hardware/drivers/other-wdk-downloads)
|Windows Version|Build Number|Supported Visual Studio|SDK|WDK|Comments|
|-|-|-|-|-|-|
|Windows 11 25H2 (Ge)|26100.6584|VS 2022|SDK|WDK|This version is the default supported kit for Windows driver development in VS2022.|
|Windows 10 2004 (VB)|19041.5738|VS 2019|SDK|WDK|Supported for Windows 7/Windows 8/Windows 8.1 driver development only.|

## Guest OS
- Windows 10 1809
- [DebugView.zip](https://learn.microsoft.com/en-us/sysinternals/downloads/debugview)
### Disable driver signature enforcement
- Open your Start Menu and click on Settings.
- Navigate to Update & Security and select Recovery from the left-hand menu.
- Under the Advanced startup section, click Restart now.
- Once your PC reboots to a blue screen, 
select Troubleshoot > Advanced options > Startup Settings.
- Click the Restart button.
- Upon restarting, you will see a list of options. 
Press 7 or F7 on your keyboard to Disable driver signature enforcement.

### DebugView setting
1. Capture -> Capture Kernel
2. Capture -> Enable Verbose Kernel Output
