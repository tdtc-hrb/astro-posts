---
layout: ../../layouts/MarkdownPostLayout.astro
title: "使用Internet Explorer测试COM"
description: "IE6 ~ IE11"
date: 2025-01-19
author: "tdtc"
---
- Target    
  x86

[创建COM](https://tdtc-hrb.github.io/csdn/post/com-wizards-vc/) 中 增加对IE支持： IObjectWithSite
<!-- VS2010: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420153532328.png -->
![atl simple object - Support](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-simple4.png)

## 增加方法
<!-- VS2010: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420160424359.png -->
![atl interface - list](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-interface3.png)
testSOW.h:
```
	STDMETHOD(Add)(LONG x, LONG y, LONG* ret);
	STDMETHOD(Sub)(LONG x, LONG y, LONG* ret);
	STDMETHOD(Mul)(LONG x, LONG y, LONG* ret);
	STDMETHOD(Div)(LONG x, LONG y, LONG* ret);
	STDMETHOD(Mod)(LONG x, LONG y, LONG* ret);
	STDMETHOD(Lg)(LONG x, LONG y, DOUBLE* ret);
```
### Add
```c++
STDMETHODIMP CtestSOW::Add(LONG x, LONG y, LONG* ret)
{
	// TODO: Add your implementation code here
	*ret = (x + y);

	return S_OK;
}
```

### Subtract
```c++
STDMETHODIMP CtestSOW::Sub(LONG x, LONG y, LONG* ret)
{
	// TODO: Add your implementation code here
	*ret = (x - y);

	return S_OK;
}
```

### Multiply
```c++
STDMETHODIMP CtestSOW::Mul(LONG x, LONG y, LONG* ret)
{
	// TODO: Add your implementation code here
	*ret = (x * y);

	return S_OK;
}
```

### Divide
```c++
STDMETHODIMP CtestSOW::Div(LONG x, LONG y, LONG* ret)
{
	// TODO: Add your implementation code here
	*ret = (x / y);

	return S_OK;
}
```

### Modulo
```c++
STDMETHODIMP CtestSOW::Mod(LONG x, LONG y, LONG* ret)
{
	// TODO: Add your implementation code here
	*ret = (x % y);

	return S_OK;
}
```

### Logarithm
```
STDMETHODIMP CtestSOW::Lg(LONG x, LONG y, DOUBLE* ret)
{
	// https://en.cppreference.com/w/c/numeric/math/log
	*ret = log(x) / log(y);

	return S_OK;
}
```


## 测试
- IE
- non-IE
### IE
[ActiveXObject](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2010/6958xykx(v=vs.100):
```c++
function ActiveXObject(ProgID : String [, location : String])
```
#### ActiveXObject
- ProgID    
![code ui](https://github.com/tdtc-hrb/csdn/raw/master/images/20140420162849875.png)
> 必选。
```
serverName.typeName
```
其中 serverName 是提供对象的应用程序的名称，
typeName 是要创建的对象的类型或类。

- location
> 可选项。

要在其中创建对象的网络访问器的名称。

#### testatl.html
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>调用ATL方法 - 测试网页</title>

</head>

<body>

数     值A：<input type="text" id="edtA" />
    
数     值B：<input type="text" id="edtB" />
<br>
<br>
计算结果：<input type="text" id="edtC" />
<br>
<br>
<input type="button" id="btnAdd" value="Add" onClick="ATLFun.add(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
<input type="button" id="btnMul" value="Mul" onClick="ATLFun.mul(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
<input type="button" id="btnDiv" value="Div" onClick="ATLFun.div(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
<input type="button" id="btnSub" value="Sub" onClick="ATLFun.sub(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
<input type="button" id="btnSub" value="Mod" onClick="ATLFun.mod(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
<input type="button" id="btnSub" value="base-5" onClick="ATLFun.lg(document.getElementById('edtA').value, document.getElementById('edtB').value)" />
</body>
<script type="text/javascript">
    var ATLFun = {
        };

    ATLFun.getObj = function(objName) {
        return new ActiveXObject(objName);
    };

    ATLFun.add = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Add(x, y);
    };

    ATLFun.mul = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Mul(x, y);
    };

    ATLFun.div = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Div(x, y);
    };

    ATLFun.sub = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Sub(x, y);
    };

    ATLFun.mod = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Mod(x, y);
    };

    ATLFun.lg = function(x, y) {
        var obj = ATLFun.getObj("testATL.testSOW");
        var edtC = document.getElementById("edtC");

        if (obj != null)
            edtC.value = obj.Lg(x, y);
    };
</script>
</html>
```

#### allow ActiveX
<!-- ie8: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420162140156.png -->
<!-- ie8: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420162309062.png -->
<!-- ie8: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420162513531.png -->
<!-- ie8: https://github.com/tdtc-hrb/csdn/raw/master/images/20140420162549156.png -->
![ie11 allow blocked content](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-allow-ie1.png)
![ie11 allow interaction](https://github.com/tdtc-hrb/csdn/raw/master/images/atl-allow-ie2.png)

### non-IE
- [VC](https://www.codeproject.com/Articles/3365/Embed-an-HTML-control-in-your-own-window-using-pla)
- GCC(msys2)    
Unzip cpp-mshtml(gcc).zip and execute DisplayHTML.exe:
```cmd
DisplayHTML.exe file://c:/users/xb/documents/testatl.html
```

#### Embed an HTML control in your own window using plain C - VC
The Simple directory contains a complete C example with everything in one source file.    
Study this to familiarize yourself with the technique of using the browser object in your own window.    
It demonstrates how to display either an HTML file on the web or disk, or an HTML string in memory, and creates 2 windows to do such.

- Simple.c    
Ln1676~Ln1687:
```c
		// Create another window with another browser object embedded in it.
		if ((msg.hwnd = CreateWindowEx(0, &ClassName[0], "test atl", WS_OVERLAPPEDWINDOW,
						CW_USEDEFAULT, 0, CW_USEDEFAULT, 0,
						HWND_DESKTOP, NULL, hInstance, 0)))
		{
			// For this window, display a URL. This could also be a HTML file on disk such as "c:\\myfile.htm".
			DisplayHTMLPage(msg.hwnd, "c:\\users\\xb\\documents\\testatl.html");

			// Show the window.
			ShowWindow(msg.hwnd, nCmdShow);
			UpdateWindow(msg.hwnd);
		}
```
Note!!!: 原来的文件名称已经变更为 Simple1.c

file name: cwebpage_src(vc141).zip

### attachment
<!-- testATL.7z(vc10): https://pan.baidu.com/s/1VFaDUD1AYmGHIeyg7wplhA  提取码: xysa -->
<!-- testATL(vc142).zip: https://pan.baidu.com/s/1lPI_sVBYQqh2-xfa_xVHHg?pwd=n2vk -->

- [testATL(vc140).zip](https://pan.baidu.com/s/1eATNR3x404qYBnHDtTGzag?pwd=cm5i)
- [cwebpage_src(vc141).zip](https://pan.baidu.com/s/1mnn875af_vfvQg6hKzSicQ?pwd=4yh3)
- [cpp-mshtml(gcc).zip](https://pan.baidu.com/s/1zQtLSKT8C0sZ2THdIPrWxw?pwd=aqke)
