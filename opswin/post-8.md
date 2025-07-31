---
layout: ../../layouts/MarkdownPostLayout.astro
title: "WinRE"
description: "update problem, error (0x80070643)"
date: 2024-11-30
author: xiaobin
tags: ["faq4", "lost WinRE", "KB5028997"]
---

- [update problem, error (0x80070643).](https://answers.microsoft.com/en-us/windows/forum/all/kb5034441-update-problem-error-0x80070643/0821b603-9707-4587-9da5-e5809cac3779)    
Required size: ≈750Mb

### [KB5028997](https://support.microsoft.com/en-us/topic/kb5028997-instructions-to-manually-resize-your-partition-to-install-the-winre-update-400faa27-9343-461c-ada9-24c8229763bf)
- To disable the WinRE
```
reagentc /disable
```
- diskpart tool
```
diskpart
```
- To re-enable WinRE
```
reagentc /enable
```

#### resize WinRE partition
```
sel disk 0
list part
```
To select the OS partition:
```
sel part 3
shrink desired=250 minimum=250
```
#### del WinRE partition
> tpye: Recovery
```
sel part 4
delete partition override
```
#### Create a new recovery partition
> GPT
```
create partition primary id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
format quick fs=ntfs label="Windows RE"
exit
```

### lost WinRE
If you formatted, merged or deleted the "Recovery" disk partition, 
then:
```
The Windows RE image was not found.
```

set path and enable:
```
reagentc /setreimage /path C:\Recovery\WindowsRE
reagentc /enable
```

#### Extract Winre.wim
Extract Winre.wim from install.wim.
- install.wim    
```
*.iso\sources
```
- Winre.win
```
Windows\System32\Recovery\
```
