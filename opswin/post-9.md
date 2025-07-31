---
layout: ../../layouts/MarkdownPostLayout.astro
title: "PowerShell"
description: "执行本地ps1脚本"
date: 2024-11-30
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

## Google Chrome
- [How to Download Older Version of Google Chrome](https://squirrelistic.com/blog/how_to_download_older_version_of_google_chrome)

### MS-Edge
Regardless of Microsoft’s reasoning, you now know how to toggle the sidebar on or off in Edge 119. 
Just head to Settings > Sidebar > Copilot > Always Show Sidebar. Alternatively, you can use the Ctrl + Shift + / shortcut.
