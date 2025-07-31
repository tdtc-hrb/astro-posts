---
layout: ../../layouts/MarkdownPostLayout.astro
title: "串口读写工具 - Windows"
description: "MFC"
date: 2024-09-23
author: "tdtc"
---

<!-- Program on Windows XP - 1: https://gitee.com/xiaobin80/csdn/raw/master/images/20150118233218968.png -->
![Program on Windows 8.1 - UI1](https://github.com/tdtc-hrb/csdn/raw/master/images/prog81-0.png)
PC has no serial device
<!-- Program on Windows XP - 2: https://gitee.com/xiaobin80/csdn/raw/master/images/20150118233246359.png -->
![Program on Windows 8.1 - UI2](https://github.com/tdtc-hrb/csdn/raw/master/images/prog81-1.png)
PC has serial device

- CSerialPort    
![class diagram](https://gitee.com/xiaobin80/csdn/raw/master/images/20140427134802562.png)

- MFC and its multibyte character set    
[Multibyte MFC Library](https://learn.microsoft.com/en-us/cpp/mfc/mfc-mbcs-dll-add-on?view=msvc-140)


# 程序介绍
界面分三块： 端口配置、发送区域、接收区域

- v2.0    
使用[boost thread](https://tdtc-hrb.github.io/csdn/post/vc-boost/) + [SQLite3 library](https://tdtc-hrb.github.io/cnblogs/post/vc-sqlite3lib/)
实现串口数据存储到SQLite数据库.


## 1. 端口配置

### 1.1 在“Port Number”选择端口号；

### 1.2 Config
<!-- Program on Windows XP - 3: https://gitee.com/xiaobin80/csdn/raw/master/images/20150119144350996.png -->
![Program on Windows 8.1 - ui3](https://github.com/tdtc-hrb/csdn/raw/master/images/prog81-2.png)
配置串口比如，串口号，波特率，数据位，停止位等等。


## 2. 发送
- A类（自动化）
```
2.2-》2.3-》2.1
```
- B类（手动)
```
  2.3-》点击“Send”按钮。
```

### 2.1 Loop Send
  当我们钩选此复选框时，必须选择“发送间隔”，然后才能执行循环发送数据。

### 2.2 间隔
  选择其一：500、1000、2000毫秒。
<!-- Program on Windows XP - 4: https://gitee.com/xiaobin80/csdn/raw/master/images/20150119144408343.png -->
![Program on Windows 8.1 - ui4](https://github.com/tdtc-hrb/csdn/raw/master/images/prog81-3.png)
Setting time

如果要更改读取自定义的时间频率：
```
请将SerialCommView.cpp-Ln292，更为：((CComboBox *)GetDlgItem(IDC_COMBO1Timer))->GetWindowTextA(strTemp);)
```

### 2.3 数据
发送的数据


## 3. 接收
配置完串口，默认为接收状态

### 3.1 16进制显示
 Hex View: 是否16进制显示

### 3.2 清除
Clear: 清空接收框数据

### 3.3 保存
Save As: 保存接收框数据；    
默认为rtf


## 测试(无硬件串口)
[VMWare/VirtualBox](https://ubuntuforums.org/showthread.php?t=2197743)

### 设置 "Serial Port"
- connection    
Use named pipe

- I/O mode
```
Yield CPU on poll
```

#### connection
- name
```
\\.\pipe\com_1
```
- type
```
This end is the server
```
- type(other end)
```
The other end is a virtual machine
```

### 设置 putty
> connection type: Serial
- Serial line
```
\\.\pipe\com_1
```
- Speed
```
9600
```

### 开始测试
- Port Number
```
Communications Port (COM1)
```
- Baud rate
```
9600
```

### 发送数据
- data
```
hello world
```
- interval
```
1000
```
- repeat
Do you want to send data repeatedly?

yes:
```
Check the "Loop Send"
```
no:
```
Uncheck "Loop Send"
```



# code
- [SerialComm](https://github.com/xiaobin80/SerialComm.git)
![project file](https://gitee.com/xiaobin80/csdn/raw/master/images/20150119160142237.png)
- IDE    
Visual Studio series is backward compatible:
```
Visual Studio 2008 / Visual Studio 2010 / Visual Studio 2012 / Visual Studio 2013 / Visual Studio 2015, 
Visual Studio 2017 / Visual Studio 2019 / Visual Studio 2022 can all(皆可) open Visual Studio 2005 projects.
```

## flow diagram
![flow diagram](https://gitee.com/xiaobin80/csdn/raw/master/images/2020051500152383.png)

首先，如果有线程在运行则停止它。防止数据出现错读。    
然后，建立事件以及把它们的值放到数组中。    
这时要初始化临界区，准备进入临界编码。    
如果要设定的串口打开了，我们要关闭它。    
建立串口以及设置超时时间设定这时我们要设置等待事件，之后设置RTS为高。 获得通讯状态，配置DCB以及清空缓存。    
最后退出临界区编码。

## update
- GetVersionEx

### GetVersionEx
```
warning C4996: 'GetVersionExA': was declared deprecated
```
ConsoleApplication:
```
#pragma comment(lib, "netapi32.lib")

#include <iostream>
#include <windows.h>
#include <lm.h>

using namespace std;

bool GetWindowsVersion(unsigned long &major, unsigned long &minor)
{
	unsigned char * pinfoRawData;
	if (NERR_Success == NetWkstaGetInfo(NULL, 100, &pinfoRawData))
	{
		WKSTA_INFO_100 * pworkstationInfo = (WKSTA_INFO_100 *)pinfoRawData;
		major = pworkstationInfo->wki100_ver_major;
		minor = pworkstationInfo->wki100_ver_minor;
		::NetApiBufferFree(pinfoRawData);
		return true;
	}
	return false;
}

int main()
{
	unsigned long major = 0;
	unsigned long minor = 0;
	if (GetWindowsVersion(major, minor))
	{
		std::cout << "Major: " << major << "\nMinor: " << minor << endl;
	}
}

```

## Ref
- [NetWkstaGetInfo function (lmwksta.h)](https://learn.microsoft.com/en-us/windows/win32/api/lmwksta/nf-lmwksta-netwkstagetinfo)
- [Part1: Overcoming Windows 8.1's deprecation of GetVersionEx and GetVersion APIs](https://www.codeproject.com/articles/678606/part1-overcoming-windows-8-1s-deprecation-of-getve)

