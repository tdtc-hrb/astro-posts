---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex shrink"
description: "Utilities for controlling how flex items shrink."
date: 2025-03-08
author: "tdtc"
---
|Class|Styles|
|-|-|
|shrink|flex-shrink: 1;|
|`shrink-<number>`|`flex-shrink: <number>;`|
|`shrink-[<value>]`|`flex-shrink: <value>;`|
|`shrink-(<custom-property>)`|`flex-shrink: var(<custom-property>);`|

## flex-shrink
- Allowing flex items to shrink
- Preventing items from shrinking
- Using a custom value

### Allowing flex items to shrink
Use <code>shrink</code> to allow a flex item to shrink if needed:
```
<div class="flex ...">
  <div class="h-14 w-14 flex-none ...">01</div>
  <div class="h-14 w-64 shrink ...">02</div>
  <div class="h-14 w-14 flex-none ...">03</div>
</div>
```
### Preventing items from shrinking
Use <code>shrink-0</code> to prevent a flex item from shrinking:
```
<div class="flex ...">
  <div class="h-16 flex-1 ...">01</div>
  <div class="h-16 w-32 shrink-0 ...">02</div>
  <div class="h-16 flex-1 ...">03</div>
</div>
```
### Using a custom value
Use the <code>shrink-[<value>]</code> syntax to set the flex shrink factor based on a completely custom value:
```
<div class="shrink-[calc(100vw-var(--sidebar))] ...">
  <!-- ... -->
</div>
```

## Ref
- [flex shrink](https://tailwindcss.com/docs/flex-shrink)
- [Responsive design](https://tailwindcss.com/docs/flex-shrink#responsive-design)
