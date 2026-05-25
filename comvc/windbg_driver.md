---
layout: ../../layouts/MarkdownPostLayout.astro
title: "windbg调试sandboxie driver"
description: "串口方式"
date: 2026-05-25
author: "tdtc"
---
- [WDK](https://docs.microsoft.com/en-us/windows-hardware/drivers/other-wdk-downloads)

|Windows Version|Build Number|Supported Visual Studio|SDK|WDK|Comments|
|-|-|-|-|-|-|
|Windows 11 25H2 (Ge)|26100.6584|VS 2022|SDK|WDK|This version is the default supported kit for Windows driver development in VS2022.|
|Windows 11 22H2 (Ni)|22621.5193|VS 2022|SDK|WDK|Supported for Windows 10 x86/ARM32 driver development only.|
|Windows 10 2004 (VB)|19041.5738|VS 2019|SDK|WDK|Supported for Windows 7/Windows 8/Windows 8.1 driver development only.|

#### Enterprise WDK (EWDK)
Instead of downloading Visual Studio, the SDK, and the WDK separately, you can download the EWDK. 
The EWDK is a standalone, self-contained command-line environment for building drivers. 
It includes Visual Studio Build Tools, the SDK, and the WDK.

# Prepare
- VMware(v10.0.7)
- Vbox

## VM setting - serial port
> vmware or vbox
```
\\.\pipe\com_1
```

### vmware
i/o mode:
```
yield CPU on poll
```

### vbox
Port 2:    
uncheck:
```
Connect to existing pipe/socket
```

## windbg
about version:    
The operating system needs to match the same or higher version of windbg.    
Otherwise the OS version will not be recognized!!

### home path
- v7.1    
```
C:\WinDDK\7600.16385.1\Debuggers\
```
- x86
```
C:\Program Files (x86)\Windows Kits\10\Debuggers\x86
```
- x64
```
C:\Program Files (x86)\Windows Kits\10\Debuggers\x64
```

### ShortCute
If you use a shortcut, you don't need to set the download path in the command.
```
<home path> -y "srv*c:\symbols*https://msdl.microsoft.com/download/symbols"
```

## guest os
- Win7 SP1(x86) [latest update](https://blog.simplix.info/update7/)
- Win8.1(x86) [latest update](https://winfuture.de/downloadvorschalt,3087.html)

### display os list
Add an OS to display the OS list:
```cmd
bcdedit /copy {current} /d "Sandboxie Usage"
```

### debug settings
```
bcdedit /debug on
```
```
bcdedit /dbgsettings serial debugport:2 baudrate:115200
```

### Disable Driver Signature Enforcement
- Win7    
  After each startup, press F8 (laptop Fn+F8).

- Win8+    
1. Settings -> Update and recovery → Recovery

2. Troubleshoot and then Advanced options.

3. Go to "Advanced options" and click Start-up Settings.

4. Under "Start-up Settings" click Restart.


### install application
setup "SandboxieInstall32.exe"


# start working
- Visual Studio 2017    
  Compile the source code with vs2017 in order to generate pdb.
- WDK    
v7.1

## kernel debug
com:    
- port
```
\\.\pipe\com_1
```
- pipe
checked

- reconnect
checked

### [path](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/-sympath--set-symbol-path-)
config:
```
.sympath SRV*c:\symbols*http://msdl.microsoft.com/download/symbols
```

details:
```
!sym noisy
```
把需要调试的pdb放入指定的文件夹。    
注意每次调试新os的时候，文件夹位置会不同!!!    
For example, the first time:
```
C:\symbols\SbieDrv.pdb\BF241AE76B2D4145B6A1B57B13335E8C1
```
the second time:
```
C:\symbols\SbieDrv.pdb\33C23FFE03A8402BA6E16961BA2880CE1
```


# command
Enable Debugger Markup Language (DML) with .prefer_dml
```
.prefer_dml 1
```

## [Reload Module](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/-reload--reload-module-)
load all modules:
```
.reload /f
```
Specified module:
```
.reload /f /i SbieDrv.sys
```

## [List Loaded Modules](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/lm--list-loaded-modules-)
show specified module:
```
lm m SbieDrv v
```

## [Break point](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bp--bu--bm--set-breakpoint)

### Unresolved Breakpoint
Sets a breakpoint that is unresolved when the module is unloaded and re-enables when the module reloads.
```
bu SbieDrv!Api_CopySidStringFromUser
bu SbieDrv!Api_Init
bu SbieDrv!Api_CopyBoxNameFromUser
bu SbieDrv!Api_CopyStringToUser
bu SbieDrv!Api_GetHomePath
bu SbieDrv!Api_GetVersion
bu SbieDrv!Api_Irp_CLEANUP
bu SbieDrv!Api_LogMessage
bu SbieDrv!Api_SetFunction
bu SbieDrv!Api_SendServiceMessage
bu SbieDrv!Api_GetWork
bu SbieDrv!Api_FastIo_DEVICE_CONTROL
bu SbieDrv!Api_SetServicePort
bu SbieDrv!Api_AddWork
bu SbieDrv!Api_DelWork
bu SbieDrv!Api_Irp_CREATE
bu SbieDrv!Api_Disable
bu SbieDrv!Api_ResetServiceProcess
bu SbieDrv!Api_Unload
```
Activate the above debugging:    
"Create a new sandbox",    
"Run web Browser";    
right click web link, "Save target as".


### [Breakepoint List](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bl--breakpoint-list-)
List the current breakpoints to confirm that the breakpoint was set by typing the bl command.
```
bl
```

## run and quit
go:
```
g
```
break:
```
Debug -> Break
```
quit debug:
```
qd
```


# Ref
- [Debug Drivers - Step by Step Lab](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debug-universal-drivers--kernel-mode-)
- [getting started with windbg](https://docs.microsoft.com/zh-cn/windows-hardware/drivers/debugger/getting-started-with-windbg)
- [symbol prompts](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/-sym)
- [command](http://windbg.info/doc/1-common-cmds.html)
- [Debugging using Windbg : Symbols loading](https://www.technlg.net/windows/symbol-server-path-windbg-debugging/)
- [Setting up kernel debugging using WinDbg and VMware](https://www.triplefault.io/2017/07/setting-up-kernel-debugging-using.html)
- [Setting Up a Windows 7+ Virtualbox VM for Kernel Mode Debugging](https://medium.com/@eaugusto/setting-up-a-windows-7-virtualbox-vm-for-kernel-mode-debugging-367911889316)
