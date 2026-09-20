---
layout: ../../layouts/MarkdownPostLayout.astro
title: "background position"
description: "Utilities for controlling the position of an element's background image."
date: 2025-04-12
author: "tdtc"
---

|Class|Styles|
|-|-|
|bg-top-left|background-position: top left;|
|bg-top|background-position: top;|
|bg-top-right|background-position: top right;|
|bg-left|background-position: left;|
|bg-center|background-position: center;|
|bg-right|background-position: right;|
|bg-bottom-left|background-position: bottom left;|
|bg-bottom|background-position: bottom;|
|bg-bottom-right|background-position: bottom right;|
|`bg-position-(<custom-property>)`|`background-position: var(<custom-property>);`|
|`bg-position-[<value>]`|`background-position: <value>;`|

### Basic example
Use utilities like <code>bg-center</code>, <code>bg-right</code>, and <code>bg-top-left</code> to 
control the position of an element's background image:
```
<div class="bg-[url(/img/mountains.jpg)] bg-top-left"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-top"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-top-right"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-left"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-center"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-right"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-bottom-left"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-bottom"></div>
<div class="bg-[url(/img/mountains.jpg)] bg-bottom-right"></div>
```

### Using a custom value
Use the <code>bg-position-[<value>]</code> syntax to set 
the background position based on a completely custom value:
```
<div class="bg-position-[center_top_1rem] ...">
  <!-- ... -->
</div>
```

## Ref
- [background-position](https://tailwindcss.com/docs/background-position)
- [Responsive design](https://tailwindcss.com/docs/background-position#responsive-design)
