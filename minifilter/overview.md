---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Overview"
description:  "FltMgr and samples"
date: 2026-05-31
author: "tdtc"
---
- [example](https://github.com/apriorit/Protection-Against-Unauthorized-Launch-Minifilter-Driver)
- [File system and filter driver samples](https://learn.microsoft.com/en-us/windows-hardware/drivers/samples/file-system-driver-samples)

### [Filter Manager Concepts](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/filter-manager-concepts)
The Filter Manager (FltMgr.sys) is a system-supplied kernel-mode driver that implements 
and exposes functionality commonly required in file system filter drivers. 

FltMgr is installed with Windows, but it becomes active only when a minifilter driver is loaded. 
It attaches to the file system stack for a target volume. 
A minifilter driver attaches to the file system stack indirectly, 
by registering with FltMgr for the I/O operations that the minifilter driver chooses to filter.

Minifilters attach in a particular order. 
The operating system determines the order of attachment by load order groups and altitudes. 
The attachment of a minifilter driver at a particular altitude on a particular volume is called 
an instance of the minifilter driver.

A minifilter's altitude:

- Ensures that the instance of the minifilter driver is always loaded at the appropriate location relative 
to other minifilter driver instances.
- Determines the order in which FltMgr calls the minifilter driver to handle I/O.

The following figure shows a simplified I/O stack with the filter manager and three minifilter drivers.

![](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/images/filter-manager-architecture-1.gif)
