---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Grid system"
description: "Bootstrap2, 3, 4"
date: 2023-03-10
author: "tdtc"
---
  在V2.3.2中，栅格系统默认是不支持移动设备的；     
  但V3.0版本，已经默认支持移动设备。

  在V4.6.x, 更加细化了移动设备支持。

# v2
[Bootstrap(v2)](https://getbootstrap.com/2.3.2/scaffolding.html#gridSystem) 默认的栅格系统为12列 ，
形成一个940px宽的容器，默认没有启用 "[响应式布局特性](https://getbootstrap.com/2.3.2/scaffolding.html#responsive)" 。    
如果加入响应式布局CSS文件，栅格系统会自动根据可视窗口的宽度从724px到1170px进行动态调整。    
在可视窗口低于767px宽的情况下，列将不再固定并且会在垂直方向堆叠。

## example
```xml
<div class="row">
  <div class="span4">...</div>
  <div class="span8">...</div>
</div>
```

# v3
> class变化：.span* -〉.col-md-*

[Bootstrap(v3)](https://getbootstrap.com/docs/3.4/css/#grid) 内置了一套响应式、移动设备优先的流式栅格系统，
随着屏幕设备或视口（viewport）尺寸的增加，系统会自动分为最多12列。
它包含了易于使用的[预定义classe](https://getbootstrap.com/docs/3.4/css/#grid-example-basic)，
还有强大的[mixin用于生成更具语义的布局](https://getbootstrap.com/docs/3.4/css/#grid-less)。

## [Grid options](https://getbootstrap.com/docs/3.4/css/#grid-options)
|Name|Size|
|-|-|
|Extra small devices Phones|<768px|
|Small devices Tablets|≥768px|
|Medium devices Desktops|≥992px|
|Large devices Desktops|≥1200px|

## example
```xml
<div class="row">
  <div class="col-md-4">...</div>
  <div class="col-md-8">...</div>
</div>
```

# v4
[Bootstrap(v4)](https://getbootstrap.com/docs/4.6/layout/grid/) 调整了小屏幕的适配。
Switch from Less to Sass for the source CSS files

## [Grid options](https://getbootstrap.com/docs/4.6/layout/grid/#grid-options)
|Name|Size|
|-|-|
|Extra small|<576px|
|Small|≥576px|
|Medium|≥768px|
|Large|≥992px|
|Extra large|≥1200px|

## example
```xml
<div class="row">
  <div class="col-lg-4">...</div>
  <div class="col-lg-8">...</div>
</div>
```
