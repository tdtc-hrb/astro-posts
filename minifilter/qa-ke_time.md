---
title: "KeQuerySystemTime undefined"
description: "at x64"
date: 2026-06-09T00:08:08+08:00
---
Issue:
```
'KeQuerySystemTime' undefined; assuming extern returning int SboxDrv C:\Users\tdtc\Documents\sandboxie\core\drv\session.c 513
...
```
- solved    
from [bobkjelgaard](https://groups.google.com/g/microsoft.public.development.device.drivers/c/13mRFMToGIc/m/1boYViK1-TYJ)
```
#ifdef _AMD64_
#define KI_USER_SHARED_DATA 0xFFFFF78000000000UI64
#define SharedSystemTime (KI_USER_SHARED_DATA + 0x14)
#define KeQuerySystemTime(CurrentCount) *((PULONG64)(CurrentCount)) = *((volatile ULONG64*)(SharedSystemTime))
#endif
```
