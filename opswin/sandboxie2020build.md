---
layout: ../../layouts/MarkdownPostLayout.astro
title: "编译sandboxie"
description: "使用vs2019/vs2022"
date: 2026-05-26
author: "tdtc"
---
- Sbox Driver
- Sbox Dll
- Sbie Control

## SboxDrv
wdk path: 
Sandbox32.props and Sandbox64.props:
```
<WDKPATH>\Program Files (x86)\Windows Kits\10</WDKPATH>
```
### path
- vs2019
```
10.0.19041.0
```
- vs2022
```
10.0.26100.0
```
#### include
```
$(WDKPATH)\Include\10.0.19041.0\km
$(WDKPATH)\Include\10.0.19041.0\ucrt
$(WDKPATH)\Include\10.0.19041.0\um
```
#### library
- x86
```
$(WDKPATH)\lib\10.0.19041.0\km\x86
```
- x64
```
$(WDKPATH)\lib\10.0.19041.0\km\x64
```

### Token Information Class
```
Error	C2365	'TokenIsAppContainer': redefinition; previous definition was 'enumerator'
```
- add old ddk

my_winnt.h:
```
#ifdef OLD_DDK
typedef enum _TOKEN_INFORMATION_CLASS2 {
    TokenIsAppContainer = 29,
    TokenCapabilities,
    TokenAppContainerSid,
    TokenAppContainerNumber,
    TokenUserClaimAttributes,
    TokenDeviceClaimAttributes,
    TokenRestrictedUserClaimAttributes,
    TokenRestrictedDeviceClaimAttributes,
    TokenDeviceGroups,
    TokenRestrictedDeviceGroups,
    TokenSecurityAttributes,
    TokenIsRestricted,
    TokenProcessTrustLevel,
    TokenPrivateNameSpace//,
    //MaxTokenInfoClass  // MaxTokenInfoClass should always be the last enum
} TOKEN_INFORMATION_CLASS2;
#endif // OLD_DDK
```

### wcsnicmp
```
Warning	C4996	'wcsnicmp': The POSIX name for this item is deprecated. 
Instead, use the ISO C and C++ conformant name: _wcsnicmp.
```

key_flt.c:
```
_wcsnicmp
```

### stdio_common_vswprintf
```
Error	LNK2001	unresolved external symbol ___stdio_common_vswprintf
```

[add it to the compiler's command line](https://stackoverflow.com/a/67745800):
```
/D_NO_CRT_STDIO_INLINE
```

## SboxDll
- afxres.h in resource.rc: Install MFC and ATL

### wcsnicmp
```
Error	LNK2001 unresolved external symbol __wcsnicmp
```

- [properties->Linker->Input->Additional Dependencies](https://stackoverflow.com/a/47148616)
```
vcruntime.lib
ucrt.lib
```

## SbieControl
Move the declaration of Common_RunStartExe() to a new header file.
- removed
```
apps/common/CommonUtils.h
```
- add
```
apps/common/RunStartExe.h:
```

### Common_RunStartExe()
- RunBrowser.cpp and MyApp.cpp
```
#include "apps/common/RunStartExe.h"
```

### CommonUtils.h
```
Error	C2065	'HINSTANCE': undeclared identifier
```
- add 
```
#include <windows.h>
```
