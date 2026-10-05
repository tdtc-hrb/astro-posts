---
layout: ../../layouts/MarkdownPostLayout.astro
title: "sing-box"
description: "config"
date: 2026-06-18
author: xiaobin
---

- Relay: Listening on port 2080; 
Proxy server address and port.
```
{
    "inbounds": [
        {
            "type": "http",
            "listen": "::",
            "listen_port": 2080
        }
    ],
    "outbounds": [
        {
            "tag": "out",
            "type": "http",
            "server": "192.168.0.108",
            "server_port": 9910
        }
    ]
}
```

## Ref
- [sing-box's socks5 inbound implementation is not compatible with RouterOS's sockify feature](https://github.com/SagerNet/sing-box/issues/3495)
