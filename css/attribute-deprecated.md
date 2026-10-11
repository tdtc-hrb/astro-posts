---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Deprecated attributes of HTML 5"
description: "This feature is no longer recommended."
date: 2026-10-11
author: "tdtc"
---
- align
- bgcolor
### align
Specifies the alignment of the element

Deprecated in:
```
<caption>, <img>, <table>, <hr>, <div>, <h1>-<h6>, <p>
```
Alternate:
```
CSS text-align, float and vertical-align properties
```
### bgcolor
Specifies the background color

Deprecated in:
```
<body>, <table>, <tr>, <td>, <th>
```
Alternate:
```
CSS background-color Property
```
### language
Specifies scripting language

Deprecated in:
```
<script>
```
Alternate:
```
The type attribute
```

### other
|Attributes|Description|Deprecated in|Alternate|
|-|-|-|-|
|alink|Specifies the color of an active link in a document|`<body>`|CSS active Pseudo Class|
|background|Specifies the background image|`<body>`|CSS background-image Property|
|border|Specifies the width of the border|`<img>, <object>`|CSS border-width Property|
|clear|Clears any right or left alignments|`<br>`|CSS clear Property|
|compact|Specifies that the list should render smaller than normal|`<ol>, <ul>`|CSS font-size, margin and line-height for a tighter list|
|height|Specifies the height of the element|`<table>`|CSS height Property|
|hspace|Specifies the whitespace or padding on left or right sides of an element|`<img>, <object>`|CSS padding Property|
|link|Specifies the default color of the links|`<body>`|CSS link Pseudo Class|
|noshade|It specifies that a horizontal line should render in one solid color (noshaded)|`<hr>`|CSS border-style Property|
|nowrap|Specifies that the text should not wrap within the table cell|`<td>, <th>`|CSS white-space Property|
|size|Specifies the initial width for the input field and a number of visible rows for the select element|`<basefont>, <font>, <hr>`|CSS width Property|
|text|Specifies the color of the text|`<body>`|CSS color property|
|type|Specifies the type of list|`<li>`|CSS list-style-type Property|
|vlink|Specifies the color of visited links|`<body>`|CSS visited Pseudo Class|
|valign|Specifies vertical alignment of cell content|`<td>, <th>, <tr>`|CSS vertical-align Property|
|vspace|Specifies the whitespace or padding above or below an element|`<img>,<object>`|CSS padding Property|
|width|Specifies the width of the element|`<hr>,<pre>,<td>,<th>`|CSS width Property|

## Ref
- [List of deprecated HTML attributes](https://www.w3docs.com/learn-html/deprecated-html-attributes)
