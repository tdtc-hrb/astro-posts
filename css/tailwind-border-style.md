---
layout: ../../layouts/MarkdownPostLayout.astro
title: "border style"
description: "Utilities for controlling the style of an element's borders."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|border-solid|border-style: solid;|
|border-dashed|border-style: dashed;|
|border-dotted|border-style: dotted;|
|border-double|border-style: double;|
|border-hidden|border-style: hidden;|
|border-none|border-style: none;|

#### divider style
- divide-solid
- divide-dashed
- divide-dotted
- divide-double
- divide-hidden
- divide-none

### Basic example
Use utilities like <code>border-solid</code> and <code>border-dotted</code> to 
control an element's border style:
```
<div class="border-2 border-solid ..."></div>
<div class="border-2 border-dashed ..."></div>
<div class="border-2 border-dotted ..."></div>
<div class="border-4 border-double ..."></div>
```

### Setting the divider style
Use utilities like <code>divide-dashed</code> and <code>divide-dotted</code> to 
control the border style between child elements:
```
<div class="grid grid-cols-3 divide-x-3 divide-dashed divide-indigo-500">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Removing a border
Use the <code>border-none</code> utility to remove an existing border from an element:
```
<button class="border-none ...">Save Changes</button>
```

## Ref
- [border style](https://tailwindcss.com/docs/border-style)
- [Responsive design](https://tailwindcss.com/docs/border-style#responsive-design)
