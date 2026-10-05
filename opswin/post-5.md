---
layout: ../../layouts/MarkdownPostLayout.astro
title: command line
author: xiaobin
description: "command line的设置"
date: 2025-02-28
tags: ["ssh", "cmd乱码"]
---

## ssh - It is also possible that a host key has just been changed
```bash
D:\program-d\putty0.7>scp f:\docker-soft\go1.12.4.linux-amd64.tar.gz xiaobin@192.168.42.243:/home/xiaobin/
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:DQR6moZJCBRrFjiNg/JWlv9MoBHopZHb8yWyHX+IeYo.
Please contact your system administrator.
Add correct host key in C:\\Users\\xiaobin/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in C:\\Users\\xiaobin/.ssh/known_hosts:1
ECDSA host key for 192.168.42.243 has changed and you have requested strict checking.
Host key verification failed.
lost connection
```

- 解决：    
删除 C:\Users\xiaobin> del c:\Users\xiaobin\.ssh\known_hosts

## cmd乱码
> only win10!

所有设置-》时间和语言-》语言
“管理语言设置”
在“非Unicode 程序的语言”中点击“更改系统区域设置”
![win info](https://gitee.com/xiaobin80/csdn/raw/master/images/20200323173824208.png)
