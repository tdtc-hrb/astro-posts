---
layout: ../../layouts/MarkdownPostLayout.astro
title: "line height"
description: "Utilities for controlling the leading, or line height, of an element."
date: 2025-04-08
author: "tdtc"
---
|Class|Styles|
|-|-|
|leading-none|line-height: 1;|
|`leading-<number>`|`line-height: calc(var(--spacing) * <number>);`|
|`leading-(<custom-property>)`|`line-height: var(<custom-property>);`|
|`leading-[<value>]`|`line-height: <value>;`|


### Basic example
Use font size utilities like <code>text-sm/6<code> and <code>text-lg/7<code> to 
set the font size and line-height of an element at the same time:
```
<p class="text-base/6 ...">So I started to walk into the water...</p>
<p class="text-base/7 ...">So I started to walk into the water...</p>
<p class="text-base/8 ...">So I started to walk into the water...</p>
```

### Setting independently
Use <code>leading-<number></code> utilities like <code>leading-6</code> and <code>leading-7</code> to 
set the line height of an element independent of the font-size:
```
<p class="text-sm leading-6">So I started to walk into the water...</p>
<p class="text-sm leading-7">So I started to walk into the water...</p>
<p class="text-sm leading-8">So I started to walk into the water...</p>
```

### Using a custom value
Use the <code>leading-[<value>]</code> syntax to set the line height based on a completely custom value:
```
<p class="leading-[1.5] ...">
  Lorem ipsum dolor sit amet...
</p>
```

## Ref
- [line height](https://tailwindcss.com/docs/line-height)
- [Responsive design](https://tailwindcss.com/docs/line-height#responsive-design)
