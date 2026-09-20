---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Virtual Box"
description: "Windows Guest Additions 安装失败问题"
date: 2025-02-08
author: xiaobin
tags: ["faq5", "Virtual Box", "Windows Guest Additions"]
---

[virtual box](https://download.virtualbox.org/virtualbox) Requires VC2019+ distribution package

### [option - install](https://www.sysnettechsolutions.com/en/fix-python-win32api-virtualbox/)
```cmd
py -m pip install pywin32
python.exe -m pip install --upgrade pip
```

### [Installing the Windows Guest Additions](https://www.virtualbox.org/manual/ch04.html#additions-windows)
> In v7.1.6+, you must first install the Code Signing Certificate

Run CMD as administrator on the guest OS:
```cmd
VBoxCertUtil.exe add-trusted-publisher vbox*.cer
```
You can install Guest Additions normally in Windows 7/8.1
