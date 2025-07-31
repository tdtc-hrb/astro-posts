---
layout: ../../layouts/MarkdownPostLayout.astro
title: "SafeArray数据"
description: "SafeArrayCreateVector()"
date: 2025-01-19
author: "tdtc"
---
!!! 除了IE的ActiveX项目，不推荐ATL !!!    
!!! ATL is not recommended except for IE ActiveX projects. !!!

# COM
> vc

## 1. 定义SAFEARRAY变量
```c++
SAFEARRAY *pSArray = NULL;
```

## 2. 释放此变量
```c++
SafeArrayDestroy(pSArray);
```

## 3. 建立向量表
```c++
pSArray = SafeArrayCreateVector(VT_UI1, 0, 32);
```

### 向量变量(VT_UI1)
- Definition in wtypes.h
```wtypes.h
typedef unsigned short VARTYPE;
/*
 * VARENUM usage key,
 *
 * * [V] - may appear in a VARIANT
 * * [T] - may appear in a TYPEDESC
 * * [P] - may appear in an OLE property set
 * * [S] - may appear in a Safe Array
 */
typedef enum VARENUM {
//...
  VT_UI1 = 17,
//...
} ;
```
- [Constants](https://learn.microsoft.com/en-us/windows/win32/api/wtypes/ne-wtypes-varenum#constants)
```html
VT_UI1
Variable type is unsigned char.
```

## 4. 写入数据
```c++
SafeArrayPutElement(pSArray, &l, &inqReport[l]);
```

## getInqRepo方法：
> AA：屏蔽的数值

```c++
STDMETHODIMP CRepoFmt::getInqRepo(ULONG iStation, SAFEARRAY** ret)
{
	SAFEARRAY *pSArray = NULL;

	unsigned char inqReport[32];
	unsigned char xorByte = AA;
	int iStationID = 0;

	if (iStation < 1)
		iStationID = 1;
	else
		iStationID = iStation;

	inqReport[0]  = AA;
	inqReport[1]  = AA;
	inqReport[2]  = AA;
	inqReport[3]  = AA;
	inqReport[4]  = (iStationID % AA);
	inqReport[5]  = (iStationID / AA);
	inqReport[6]  = AA;
	inqReport[7]  = AA;
	inqReport[8]  = AA;
	inqReport[9]  = AA;
	inqReport[10] = AA;
	inqReport[11] = AA;

	for (int i = 1; i < 18; i++)
		xorByte ^= inqReport[i];

	inqReport[18] = xorByte;

	// Fill the inqReport etc.
	for (int j = 12; j < 18; j++)
		inqReport[j] = 0;
	for (int k = 19; k < 32; k++)
		inqReport[k] = 0;

	if (!ret)
		return E_POINTER;

	if (*ret) {
		SafeArrayDestroy(pSArray);
		*ret = NULL;
	}

	pSArray = SafeArrayCreateVector(VT_UI1, 0, 32);
	for (long l = 0; l < 32; l++)
		SafeArrayPutElement(pSArray, &l, &inqReport[l]);

	*ret = pSArray;

	return S_OK;
}
```

# 调用COM
> c#的按钮事件

```c sharp
// clear TextBox
edtAck.Text = "";
edtInq.Text = "";

repoInfoLib.RepoFmtClass report = new RepoFmtClass();
Array retAck = report.getAckRepo((uint)Int32.Parse(edtStation.Text));

foreach (Byte bt in retAck)
    edtAck.Text += "0x" + bt.ToString("X2") + " ";

Array retInq = report.getInqRepo((uint)Int32.Parse(edtStation.Text));

foreach (Byte bt in retInq)
    edtInq.Text += "0x" + bt.ToString("X2") + " ";
```

- 建立COM实例    
> 第5行

- 调用COM方法
> 第6, 10行    
> 此方法返回SafeArray数据

- 赋值    
> 第8，9行和第12，13行    
> 把每个数组中的数据赋值给TextBox控件，并以十六进制方式显示（0xYY）。
