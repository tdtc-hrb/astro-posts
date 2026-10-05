---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex grow"
description: "Utilities for controlling how flex items grow."
date: 2025-03-07
author: "tdtc"
---
|Class|Styles|
|-|-|
|grow|flex-grow: 1;|
|`grow-<number>`|`flex-grow: <number>;`|
|`grow-[<value>]`|`flex-grow: <value>;`|
|`grow-(<custom-property>)`|`flex-grow: var(<custom-property>);`|

## flex-grow
- Allowing items to grow
- Growing items based on factor
- Preventing items from growing
- Using a custom value

### Allowing items to grow
Use <code>grow</code> to allow a flex item to grow to fill any available space:
```
<div class="flex ...">
  <div class="size-14 flex-none ...">01</div>
  <div class="size-14 grow ...">02</div>
  <div class="size-14 flex-none ...">03</div>
</div>
```
### Growing items based on factor
Use <code>grow-<number></code> utilities like <code>grow-3</code> to make flex items grow proportionally based 
on their growth factor, allowing them to fill the available space relative to each other:
```
<div class="flex ...">
  <div class="size-14 grow-3 ...">01</div>
  <div class="size-14 grow-7 ...">02</div>
  <div class="size-14 grow-3 ...">03</div>
</div>
```
### Preventing items from growing
Use <code>grow-0</code> to prevent a flex item from growing:
```
<div class="flex ...">
  <div class="size-14 grow ...">01</div>
  <div class="size-14 grow-0 ...">02</div>
  <div class="size-14 grow ...">03</div>
</div>
```
### Using a custom value
Use the <code>grow-[<value>]</code> syntax to set the flex grow factor based on a completely custom value:
```
<div class="grow-[25vw] ...">
  <!-- ... -->
</div>
```

## Ref
- [flex grow](https://tailwindcss.com/docs/flex-grow)
- [Responsive design](https://tailwindcss.com/docs/flex-grow#responsive-design)
