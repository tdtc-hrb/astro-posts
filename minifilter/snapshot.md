---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Snapshot of I/O operation status"
description:  "FltMgr provides support that allows minifilter drivers to associate their contexts 
with FltMgr's objects to preserve state across I/O operations."
date: 2026-06-01
author: "tdtc"
---
- [Registering Context Types](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/registering-context-types)
- [Creating Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/creating-contexts)
- [Setting Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/setting-contexts)
- [Getting Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/getting-contexts)
- [Referencing Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/referencing-contexts)
- [Releasing Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/releasing-contexts)
- [Deleting Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/deleting-contexts)
- [Freeing Contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/freeing-contexts)

### Context sample code
See the [CTX sample](https://github.com/Microsoft/Windows-driver-samples/tree/main/filesys/miniFilter/ctx) 
for an example of a minifilter driver that uses contexts.

## Ref
- [Managing minifilter contexts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/managing-contexts-in-a-minifilter-driver)
