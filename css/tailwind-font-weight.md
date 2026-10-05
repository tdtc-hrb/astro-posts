---
layout: ../../layouts/MarkdownPostLayout.astro
title: "font weight"
description: "Utilities for controlling the font weight of an element."
date: 2025-03-13
author: "tdtc"
---
|Class|Styles|
|-|-|
|font-thin|font-weight: 100;|
|font-extralight|font-weight: 200;|
|font-light|font-weight: 300;|
|font-normal|font-weight: 400;|
|font-medium|font-weight: 500;|
|font-semibold|font-weight: 600;|
|font-bold|font-weight: 700;|
|font-extrabold|font-weight: 800;|
|font-black|font-weight: 900;|
|`font-(<custom-property>)`|`font-weight: var(<custom-property>);`|
|`font-[<value>]`|`font-weight: <value>;`|

### Basic example
Use utilities like <code>font-thin</code> and <code>font-bold</code> to set the font weight of an element:
```
<p class="font-light ...">The quick brown fox ...</p>
<p class="font-normal ...">The quick brown fox ...</p>
<p class="font-medium ...">The quick brown fox ...</p>
<p class="font-semibold ...">The quick brown fox ...</p>
<p class="font-bold ...">The quick brown fox ...</p>
```

### Using a custom value
Use the <code>font-[<value>]</code> syntax to set the font weight based on a completely custom value:
```
<p class="font-[1000] ...">
  <!-- ... -->
</p>
```

## Ref
- [font weight](https://tailwindcss.com/docs/font-weight)
- [Responsive design](https://tailwindcss.com/docs/font-weight#responsive-design)
