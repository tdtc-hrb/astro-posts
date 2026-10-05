---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Loading and unloading a minifilter"
description:  "Minifilter Driver Callback Routines for Instance Setup, Teardown, and Unload"
date: 2026-05-31
author: "tdtc"
---
- FilterUnloadCallback must be called.
- Optional, InstanceSetupCallback can be called.

### FilterUnloadCallback
This is the unload routine for this miniFilter driver. 
This is called when the minifilter is about to be unloaded. 
We can fail this unload request if this is not a mandatory unloaded indicated by the Flags parameter.

### InstanceSetupCallback
This routine is called whenever a new instance is created on a volume. 
This gives us a chance to decide if we need to attach to this volume or not.

- If this routine is not defined in the registration structure, 
automatic instances are alwasys created.

### InstanceQueryTeardownCallback
This is called when an instance is being manually deleted by a
 call to FltDetachVolume or FilterDetach thereby giving us a
 chance to fail that detach request.

- If this routine is not defined in the registration structure, explicit
 detach requests via FltDetachVolume or FilterDetach will always be failed.

### InstanceTeardownStartCallback
This routine is called at the start of instance teardown.

- If we have cache table, we have to clean up the table at this point.

### InstanceTeardownCompleteCallback
This routine is called at the end of instance teardown.

## Ref
- [Loading and unloading a minifilter](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/loading-and-unloading)
