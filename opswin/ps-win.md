---
layout: ../../layouts/MarkdownPostLayout.astro
title: "PowerShell"
description: "执行本地ps1脚本"
date: 2025-08-30
author: xiaobin
tags: ["faq4", "Set-ExecutionPolicy", "offline Chrome", "MS Edge"]
---

- To get all of the execution policies that affect the current session and display them in precedence order:
```
Get-ExecutionPolicy -List
```
- local script
```
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
```

### [Policy](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4#change-the-execution-policy)
- To set the execution policy in a particular scope:
```
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

#### [policies](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4#powershell-execution-policies)
- AllSigned
- Bypass
- Default
- RemoteSigned
- Restricted
- Undefined
- Unrestricted

### [win server](https://community.spiceworks.com/t/gui-instalation-for-windows-2012-server-with-cli/1010685)
```
powershell (enter PowerShell prompt)
mkdir c:\mount
dism /mount-wim /wimfile:d:\sources\install.wim /index:4 /mountdir:c:\mount /readonly
install-windowsfeature server-gui-mgmt-infra,server-gui-shell –restart –source c:\mount\windows\winsxs
```
