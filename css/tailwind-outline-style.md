---
layout: ../../layouts/MarkdownPostLayout.astro
title: "outline style"
description: "Utilities for controlling the style of an element's outline."
date: 2025-03-13
author: "tdtc"
---
|Class|Styles|
|-|-|
|outline-solid|outline-style: solid;|
|outline-dashed|outline-style: dashed;|
|outline-dotted|outline-style: dotted;|
|outline-double|outline-style: double;|
|outline-none|outline-style: none;|
|outline-hidden|outline: 2px solid transparent; outline-offset: 2px;|

#### [border 和 outline](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline#border_%E5%92%8C_outline)
- outline 不占据空间，绘制于元素内容周围。
- 可以是非矩形的。

### Basic example
Use utilities like <code>outline-solid</code> and <code>outline-dashed</code> to set the style of an element's outline:
```
<button class="outline-2 outline-offset-2 outline-solid ...">Button A</button>
<button class="outline-2 outline-offset-2 outline-dashed ...">Button B</button>
<button class="outline-2 outline-offset-2 outline-dotted ...">Button C</button>
<button class="outline-3 outline-offset-2 outline-double ...">Button D</button>
```

### Hiding an outline
Use the <code>outline-hidden</code> utility to hide the default browser 
outline on focused elements, while still preserving the outline in forced colors mode:
```
<input class="focus:border-indigo-600 focus:outline-hidden ..." type="text" />
```
It is highly recommended to apply your own focus styling for accessibility when using this utility.

### Removing outlines
Use the <code>outline-none</code> utility to completely remove the default browser outline on focused elements:
```
<div class="focus-within:outline-2 focus-within:outline-indigo-600 ...">
  <textarea class="outline-none ..." placeholder="Leave a comment..." />
  <button class="..." type="button">Post</button>
</div>
```
It is highly recommended to apply your own focus styling for accessibility when using this utility.

## Ref
- [outline style](https://tailwindcss.com/docs/outline-style)
- [Responsive design](https://tailwindcss.com/docs/outline-style#responsive-design)
