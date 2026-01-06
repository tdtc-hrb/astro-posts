---
layout: ../../layouts/MarkdownPostLayout.astro
title: "z-index"
description: "Utilities for controlling the stack order of an element."
date: 2025-04-12
author: "tdtc"
---

|Class|Styles|
|-|-|
|`z-<number>`|`z-index: <number>;`|
|z-auto|z-index: auto;|
|`z-[<value>]`|`z-index: <value>;`|
|`z-(<custom-property>)`|`z-index: var(<custom-property>);`|

### Basic example
Use the <code>z-<number></code> utilities like <code>z-10</code> 
and <code>z-50</code> to control the stack order (or three-dimensional positioning) 
of an element, regardless of the order it has been displayed:
```
<div class="z-40 ...">05</div>
<div class="z-30 ...">04</div>
<div class="z-20 ...">03</div>
<div class="z-10 ...">02</div>
<div class="z-0 ...">01</div>
```

### Using negative values
To use a negative z-index value, prefix the class name with a dash to convert it to a negative value:
```
<div class="...">05</div>
<div class="...">04</div>
<div class="-z-10 ...">03</div>
<div class="...">02</div>
<div class="...">01</div>
```

### Using a custom value
Use the <code>z-[<value>]</code> syntax to set the stack order based on a completely custom value:
```
<div class="z-[calc(var(--index)+1)] ...">
  <!-- ... -->
</div>
```

## Ref
- [z-index - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index)
- [z-index - tw](https://tailwindcss.com/docs/z-index)
- [Responsive design](https://tailwindcss.com/docs/z-index#responsive-design)
