---
layout: ../../layouts/MarkdownPostLayout.astro
title: "铁路车号读取"
description: "使用IE"
date: 2025-01-19
author: "tdtc"
---
> - replace(regexp/substr,replacement)
> 使用这个函数来替换多余的空格。
```js
str.replace(/\s/g, "");
```
> - split(separator,howmany)
> 字符串转换成字符数组。
```js
string.split(",");
```

# 一、js部分
我们把所有的方法放到一个对象（RepoInfo）中。
```js
var RepoInfo = { };
```

## 1. 获取对象
```js
RepoInfo.getObj = function(objName) {
		return new ActiveXObject(objName);
	};
```

## 2. 获取数组
```js
RepoInfo.getArray = function(str) {
  var ret = new Array(16);

  var string = str.replace(/\s/g, "");

  ret = string.split(",");

  return ret;
};
```

## 3. 解码字串
### 输入字串校验
  如果字串空，退出。

### 输出框清空
  每次赋值前，清空。

### 执行COM中的方法
  在获取对象非空的情况下，执行。

```js
RepoInfo.decode = function(string) {
  if (string == null) return;

  var obj = RepoInfo.getObj("repoInfo.LabelInfo");
  var edtView = document.getElementById("edtView");
  edtView.value = " ";

  var str = RepoInfo.getArray(string);
  if (obj != null)
    edtView.value = obj.getInfo(str);
};
```

# 二、html部分
## 按钮事件
  从输入框获取字串作为js方法的输入参数，注意：两种引号的配合使用。
```html
<input type="button" id="btnOk" value="执行数据解析" onClick="RepoInfo.decode(document.getElementById('edtData').value)" />
```

## 源代码（含js代码）
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>报文数据信息 - IE</title>

<script type="text/javascript">
	var RepoInfo = {
		};

	RepoInfo.getObj = function(objName) {
		return new ActiveXObject(objName);
	};

	RepoInfo.getArray = function(str) {
		var ret = new Array(16);

		var string = str.replace(/\s/g, "");
		alert(string);

		ret = string.split(",");

		return ret;
	};

	RepoInfo.decode = function(string) {
		if (string == null) return;

		var obj = RepoInfo.getObj("repoInfo.LabelInfo");
		var edtView = document.getElementById("edtView");
		edtView.value = " ";

		var str = RepoInfo.getArray(string);
		if (obj != null)
			edtView.value = obj.getInfo(str);
	};

</script>
</head>

<body>
                    
	  
	<textarea name="note" cols="98" rows="7" readonly="readonly">
       注意：本测试只能运行在IE浏览器！

  首先，要注册Dll（regsvr32 repoInfo.dll）；
  然后，从“BinJiang_2005.rep”（滨江站），复制行数据到“标签数据”框。

  示例（固定格式）：
    0xD3, 0x05, 0x94, 0x84, 0x00, 0x13, 0x51, 0x2F, 0x59, 0x34, 0x57, 0x45, 0x58, 0x50, 0x41, 0x98</textarea>
<br>
<br>
标签数据：<input type="text" id="edtData" size="98" />

<br>
<br>
执行结果：<input type="text" id="edtView" size="50" />
<br>
<br>
                  
<input type="button" id="btnOk" value="执行数据解析" onClick="RepoInfo.decode(document.getElementById('edtData').value)" />
</body>
</html>
```

# Test
- 二进制文件工具：[EditPlus](https://www.editplus.com/download.html)    
Edit -> Hex Viewer

|File Name(.DAT)|Car Number|
|-|-|
|D2011914|312490215|
|D2011926|331926515|
|D2011955|342272515|
|D2012009|346553415|
|D2012035|345000715|
|D2021643|350199715|
|D2021741|345008515|
|D2021743|345001615|
|D2021926|332465615|
|D2021959|342312215|
|D2022011|345005915|
|D2022044|342018915|
|D2031744|342637015|
|D2031752|345003215|
|D2031913|340937115|
|D2031932|332869515|
|D2031958|331071015|
|D2032039|340848715|
|D2032042|345008015|
|D2032339|346034315|
|D2032344|312071215|
|D2041241|350324015|
|D2041738|350323015|
|D2041808|345006515|
|D2042012|345002415|
|D2042017|346445515|
|D2042038|340173615|
|D2042140|312747515|
|D2051607|350323415|
|D2051746|345007615|
|D2051922|331183715|
|D2051934|346033215|
|D2051946|312525215|
|D2052008|345200015|
|D2052022|345005215|
|D2061808|345002915|
|D2061920|332753815|
|D2061945|342158015|
|D2061957|340534815|
|D2062015|345002115|
|D2071750|345004115|
|D2071915|342772915|
|D2071934|346033215|
|D2071949|342700815|
|D2072018|345008715|
|D2072047|346288015|
|D2081108|331115215|
|D2081118|331115215|
|D2081325|350338915|
|D2081757|345000715|
|D2081917|342941715|


# 参考文档(W3School)：
- [replace 方法](http://www.w3school.com.cn/jsref/jsref_replace.asp)
- [RegExp 对象](http://www.w3school.com.cn/jsref/jsref_obj_regexp.asp)
- [split 方法](http://w3school.com.cn/jsref/jsref_split.asp)
