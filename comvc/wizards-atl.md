---
layout: ../../layouts/MarkdownPostLayout.astro
title: "VC 创建 Component Object Model"
description: "ATL Project Wizard"
date: 2025-01-19
author: "tdtc"
---
!!! 除了IE的ActiveX项目，不推荐ATL !!!    
!!! ATL is not recommended except for IE ActiveX projects. !!!

Use Visual Studio's wizard to create COM
- Visual Studio 2013 ~ 2019    
> x86 IDE
- Visual Studio 2022    
> x64 IDE

step by step:
- 建立ATL工程
- 建立ATL Simple Object
- 添加IDL方法
- 测试添加的method


# 建立ATL工程
File->New->Project
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200201162120769.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new1(vs2013).png -->
<!-- vs2015: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new1(vs2015).png -->
```
name: testATL
```
Note: name即是要生成的DLL文件    
![project type](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new1(vs2019).png)
![project name](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new2(vs2019).png)

选择"MFC/ATL"中"ATL Project":    
> Default

<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200201171441614.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new2(vs2013).png -->
![project property](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-new3(vs2019).png)

### Choice Platform
Build -> Configuration Manager
```
x64 or x86
```

### 取消编译时注册Dll
> Project -> Properties
```
Linker -> Register Output
No
```
#### x64 for vs2022+
```
Linker -> All Options -> 
Register Output: No
```

## Add ATL Simple Object
> 右击项目名称
- vs2013/vs2015:    
Add -> Class
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313201050286.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple1(vs2013).png -->
- vs2017/vs2019:    
Add -> New Item
<!-- vs2019: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple1.png -->
- vs2022:    
Add -> Module    
![atl simple object - item](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple1(vs2022).png)

ATL Simple Object:
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313201948199.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple2(vs2013).png -->
![atl simple object - new](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple2.png)

### 设置
Short name: testSOW

- Simple Object ID    
ProgID: testATL.testSOW
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313202352422.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple3(vs2013).png -->
![atl simple object - progID](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple3.png)

#### IE支持
- vs2013/vs2015    
Options -> Support
- vs2017/vs2019/vs2022    
Other Options
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313202901252.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple4(vs2013).png -->
![atl simple object - Support](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple4.png)


## 添加IDL方法
> Tab switching from "Solution Explorer" to "Class View"
>> vs2022: View -> Class View

Select the interface, Right-click -> add -> add method
```
name: ItestSOW
```
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313210151687.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface1(vs2013).png -->
![atl interface - add](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface1.png)
添加方法名称以及参数    
<!-- vs2017: https://gitee.com/xiaobin80/csdn/raw/master/images/20200313210840198.png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface2.1(vs2013).png -->
<!-- vs2013: https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface2.2(vs2013).png -->
![atl interface - property](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface2.png)

### MIDL attribute
- [in](https://learn.microsoft.com/en-us/windows/win32/midl/in)
- [retval](https://learn.microsoft.com/en-us/windows/win32/midl/retval)
testATL.idl(part):
```
	[id(1), helpstring("add method")] HRESULT Add([in] LONG x, [in] LONG y, [out, retval] LONG* ret);
	[id(2), helpstring("sub method")] HRESULT Sub([in] LONG x, [in] LONG y, [out, retval] LONG* ret);
```


# test
- 注册COM
```cmd
@echo
cd /d %~dp0
Regsvr32 xbfInfo.dll
```
- Debug版本    
拷贝
```
C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Redist\MSVC\14.42.34433\x86\Microsoft.VC143.CRT\vcruntime140d.dll
```
 and 
```
C:\Windows\SysWOW64\ucrtbased.dll
```
放到testATL.dll所在的目录

## VB Project
Project -> Add Reference
![vb import dll](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-import16.png)

按钮事件：
```vb.net
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
        Dim obj As New testATLLib.testSOW
        Dim int1 As Long

        'vs2010/vs2013'int1 = obj.Add(2, 3)
        obj.Add(2, 3, int1)
        Label1.Text = int1
    End Sub
```
拷贝Interop.testATLLib.dll和WindowsApplication1.exe即可
![运行](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-exec16.png)

## Issues
Q: Vs 2012+
```
System.Runtime.InteropServices.COMException (0x80040154): 
Retrieving the COM class factory for component with CLSID 
{7A6E7413-F0E2-41B8-9BB7-036229C90FE5} failed due to the following 
error: 80040154 Class not registered (Exception from HRESULT: 0x80040154 (REGDB_E_CLASSNOTREG)).
```
A: vs高版本已经使用[32/64位](https://stackoverflow.com/a/4664073)    
It means the class id 877AA945-1CB2-411C-ACD7-C70B1F9E2E32 is not in the registry.

You can verify this by opening regedit.exe, browsing to HKEY_CLASSES_ROOT\CLSID\{877AA945-1CB2-411C-ACD7-C70B1F9E2E32}.    
If your running a 32-bit app on a 64 bit OS, look for HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{877AA945-1CB2-411C-ACD7-C70B1F9E2E32}

If it is there, it may be some other issue but it is probably missing.    
To resolve this you will usually run the installer that distributes this COM object.    
If you don't have one and you know what dll implements the object, you can run regsvr32.exe (or regasm.exe for a managed dll).

### ucrt
仅安装ucrt（通用Windows sdk）会出现：
```bash
  cannot find the resource compiler dll. please make sure the path is correct.
```

解决办法：    
安装Windows 8.1/Windows 10 SDK


# 参考文章
- [ATL 项目向导](https://learn.microsoft.com/en-us/cpp/atl/reference/atl-project-wizard?view=msvc-170)
- [ATL 项目向导的应用程序设置](https://learn.microsoft.com/en-us/cpp/atl/reference/application-settings-atl-project-wizard?view=msvc-170)
- [添加 ATL 简单对象](https://learn.microsoft.com/en-us/cpp/atl/reference/adding-an-atl-simple-object?view=msvc-170)
- [ATL 简单对象向导](https://learn.microsoft.com/en-us/cpp/atl/reference/atl-simple-object-wizard?view=msvc-170)
- [ATL 简单对象向导的"选项"](https://learn.microsoft.com/en-us/cpp/atl/reference/options-atl-simple-object-wizard?view=msvc-170)
- [添加方法](https://learn.microsoft.com/en-us/cpp/ide/adding-a-method-visual-cpp?view=msvc-170)
- [Changes to Project Templates and Code Wizards in 15.3](https://devblogs.microsoft.com/cppblog/changes-to-project-templates-and-code-wizards-in-15-3/)
