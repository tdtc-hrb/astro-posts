---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Input Method Editor"
description: "Windows 11 24H2"
date: 2025-02-08
author: xiaobin
tags: ["faq5", "IME", "Windows Photo Viewer"]
---

- [win11 输入法不显示选字栏](https://answers.microsoft.com/zh-hans/windows/forum/all/%E5%8D%87%E7%BA%A7win11%E5%90%8E%E5%BE%AE%E8%BD%AF/65e4f45d-72ef-4ef2-ba07-0c8ee4ab15d3)

### [Revert to a previous version of an IME (Input Method Editor)](https://support.microsoft.com/en-us/windows/revert-to-a-previous-version-of-an-ime-input-method-editor-adcc9caa-17cb-44d8-b46e-f5b473b4dd77)
1. In the search box on the taskbar, type Settings, and then either select it in the list of results or select Enter.
2. Type IME settings into the search box within Settings and select the IME settings that are appropriate to your language—for example Japanese IME Settings.
3. Select General.
4. Turn on Use previous version of Microsoft IME.

## [照片查看器](https://jingyan.baidu.com/article/14bd256ebabbb8bb6d261287.html)
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations
```
### string value
> PhotoViewer.FileAssoc.Tiff

- .jpg
- .png
