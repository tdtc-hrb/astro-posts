---
layout: ../../layouts/MarkdownPostLayout.astro
title: "间隙(gap) - 元素之间的间隔"
description: "Utilities for controlling gutters between grid and flexbox items."
date: 2025-03-12
author: "tdtc"
---
|Class|Styles|
|-|-|
|`gap-<number>`|`gap: calc(var(--spacing) * <value>);`|
|`gap-(<custom-property>)`|`gap: var(<custom-property>);`|
|`gap-[<value>]`|`gap: <value>;`|
|`gap-x-<number>`|`column-gap: calc(var(--spacing) * <value>);`|
|`gap-x-(<custom-property>)`|`column-gap: var(<custom-property>);`|
|`gap-x-[<value>]`|`column-gap: <value>;`|
|`gap-y-<number>`|`row-gap: calc(var(--spacing) * <value>);`|
|`gap-y-(<custom-property>)`|`row-gap: var(<custom-property>);`|
|`gap-y-[<value>]`|`row-gap: <value>;`|

- Basic example
- Changing row and column gaps independently
- Using a custom value

### Basic example
Use <code>gap-<number></code> utilities like <code>gap-2</code> and <code>gap-4</code> to 
change the gap between both rows and columns in grid and flexbox layouts:
```
<div class="grid grid-cols-2 gap-4">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
</div>
```
### Changing row and column gaps independently
Use <code>gap-x-<number></code> or <code>gap-y-<number></code> utilities 
like <code>gap-x-8</code> and <code>gap-y-4</code> to change the gap between columns and rows independently:
```
<div class="grid grid-cols-3 gap-x-8 gap-y-4">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
  <div>06</div>
</div>
```
### Using a custom value
Use utilities like <code>gap-[<value>]</code>,<code>gap-x-[<value>]</code>, 
and <code>gap-y-[<value>]</code> to set the gap based on a completely custom value:
```
<div class="gap-[10vw] ...">
  <!-- ... -->
</div>
```

## Ref
- [gap](https://tailwindcss.com/docs/gap)
- [Responsive design](https://tailwindcss.com/docs/gap#responsive-design)
