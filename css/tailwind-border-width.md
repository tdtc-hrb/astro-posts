---
layout: ../../layouts/MarkdownPostLayout.astro
title: "border width"
description: "Utilities for controlling the width of an element's borders."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|border|border-width: 1px;|
|`border-<number>`|`border-width: <number>px;`|
|`border-(length:<custom-property>)`|`border-width: var(<custom-property>);`|
|`border-[<value>]`|`border-width: <value>;`|

#### The meaning of the letters
- x
```
inline
```
- y
```
block
```
- s
```
inline-start
```
- e
```
inline-end
```
- t
```
top
```
- r
```
right
```
- b
```
bottom
```
- l
```
left
```

#### Between children
- x
- y
- x-reverse
- y-reverse


### Basic example
Use border or <code>border-<number></code> utilities like <code>border-2</code> and <code>border-4</code> to 
set the border width for all sides of an element:
```
<div class="border border-indigo-600 ..."></div>
<div class="border-2 border-indigo-600 ..."></div>
<div class="border-4 border-indigo-600 ..."></div>
<div class="border-8 border-indigo-600 ..."></div>
```

### Individual sides
Use utilities like <code>border-r</code> and <code>border-t-4</code> to set the border width for one side of an element:
```
<div class="border-t-4 border-indigo-500 ..."></div>
<div class="border-r-4 border-indigo-500 ..."></div>
<div class="border-b-4 border-indigo-500 ..."></div>
<div class="border-l-4 border-indigo-500 ..."></div>
```

### Horizontal and vertical sides
Use utilities like <code>border-x</code> and <code>border-y-4</code> to set the border width on 
two sides of an element at the same time:
```
<div class="border-x-4 border-indigo-500 ..."></div>
<div class="border-y-4 border-indigo-500 ..."></div>
```

### Using logical properties
Use utilities like <code>border-s</code> and <code>border-e-4</code> 
to set the <code>border-inline-start-width</code> and <code>border-inline-end-width</code> [logical properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties/Basic_concepts), 
which map to either the left or right border based on the text direction:
```
<div dir="ltr">
  <div class="border-s-4 ..."></div>
</div>
<div dir="rtl">
  <div class="border-s-4 ..."></div>
</div>
```

### Between children
Use utilities like <code>divide-x</code> and <code>divide-y-4</code> to add borders between child elements:
```
<div class="grid grid-cols-3 divide-x-4">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
#### Reversing children order
If your elements are in reverse order (using say <code>flex-row-reverse</code> or <code>flex-col-reverse</code>), 
use the <code>divide-x-reverse</code> or <code>divide-y-reverse</code> utilities to ensure the border is added to the correct side of each element:
```
<div class="flex flex-col-reverse divide-y-4 divide-y-reverse divide-gray-200">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Using a custom value
Use the <code>border-[<value>]</code> syntax to set the border width based on a completely custom value:
```
<div class="border-[2vw] ...">
  <!-- ... -->
</div>
```

## Ref
- [border width](https://tailwindcss.com/docs/border-width)
- [Responsive design](https://tailwindcss.com/docs/border-width#responsive-design)
