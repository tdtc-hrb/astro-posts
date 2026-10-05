---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Inno setup"
description: "Includes part of the source script"
date: 2026-05-03
author: xiaobin
tags: ["Installer", "inno"]
---
The setup script wizard is basically the same as [Wise](https://en.wikipedia.org/wiki/Wise_Solutions).

### Flags
- checkedonce
```
Flags: checkedonce
```
**If the UsePreviousTasks=no, this flag is effectively disabled.**
- unchecked
```
Flags：unchecked
```
### src
- [Tasks section](https://jrsoftware.org/ishelp/topic_taskssection.htm)
```
[Tasks]
Name: "desktopicon"; Description: "{cm:CreateDesktopIcon}"; GroupDescription: "{cm:AdditionalIcons}"; Flags: checkedonce
```
- [Run section](https://jrsoftware.org/ishelp/topic_runsection.htm)
```
[Run]
Filename: "{app}\{#MyAppExeName}"; Description: "{cm:LaunchProgram,{#StringChange(MyAppName, '&', '&&')}}"; Flags: nowait postinstall skipifsilent unchecked
```

### Ref
- [Inno Setup: Set default value for desktop icon-check box to true](https://stackoverflow.com/questions/2622906/inno-setup-set-default-value-for-desktop-icon-check-box-to-true)
