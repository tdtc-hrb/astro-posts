---
layout: ../../layouts/MarkdownPostLayout.astro
title: "VC 创建 Component Object Model"
description: "ATL Project Wizard"
date: 2025-03-05
author: "tdtc"
---
- 建立ATL工程
- 建立ATL Simple Object
- 添加IDL方法

## ATL工程
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
- Short name: testSOW
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


## test
- 注册COM
```cmd
@echo
cd /d %~dp0
Regsvr32 xbfInfo.dll
```
- Debug版本    
拷贝
```
<Visual-Studio Installation Path>\vcruntime140d.dll
```
 and 
```
C:\Windows\SysWOW64\ucrtbased.dll
```
放到project目录

### VB Project
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

## Ref
- [ATL update](https://tdtc-hrb.github.io/com-vc/posts/update-atl)
- [ATL update 2](https://tdtc-hrb.github.io/com-vc/posts/update2-atl)
