---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Deploy .net framework 4.7.2/4.8 on win7"
description: "How to Install SHA-2 Code Signing Support Updates"
date: 2025-08-06
author: xiaobin
tags: [".NET Framework 4.7.2", ".NET Framework 4.8", "SHA-2"]
---

This article explains the SHA-2 patch required when installing higher versions of the .NET Framework.

- Win7 SP1

## [enable SHA-2 Code signing support by installing](https://support.microsoft.com/en-us/topic/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus-64d1c82d-31ee-c273-3930-69a4cde8e64f), 
- Fx 4.7.2
- Fx 4.8

### fx 472
- win7
```
KB3033929
```
### fx 48
- win7
```
KB3033929
KB4490628
KB4474419
```

# Ref
- [How to Install SHA-2 Code Signing Support Updates](https://www.journeybytes.com/fix-certificate-install-error-net-framework-windows-7)
