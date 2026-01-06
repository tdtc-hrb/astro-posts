---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex"
description: "Utilities for controlling how flex items both grow and shrink."
date: 2025-03-04
author: "tdtc"
---
|Class|Styles|
|-|-|
|`flex-<number>`|`flex: <number>;`|
|`flex-<fraction>`|`flex: calc(<fraction> * 100%);`|
|flex-auto|flex: 1 1 auto;|
|flex-initial|flex: 0 1 auto;|
|flex-none|flex: none;|
|`flex-(<custom-property>)`|`flex: var(<custom-property>);`|
|`flex-[<value>]`|`flex: <value>;`|

## flex
- Basic example
- Initial
- Auto
- None
- Using a custom value

### Basic example
Use <code>flex-<number></code> utilities like <code>flex-1</code> to allow 
a flex item to grow and shrink as needed, ignoring its initial size:
```
<div class="flex">
  <div class="w-14 flex-none ...">01</div>
  <div class="w-64 flex-1 ...">02</div>
  <div class="w-32 flex-1 ...">03</div>
</div>
```
### Initial
Use <code>flex-initial</code> to allow a flex item to shrink but not grow, taking into account its initial size:
```
<div class="flex">
  <div class="w-14 flex-none ...">01</div>
  <div class="w-64 flex-initial ...">02</div>
  <div class="w-32 flex-initial ...">03</div>
</div>
```
### Auto
Use <code>flex-auto</code> to allow a flex item to grow and shrink, taking into account its initial size:
```
<div class="flex ...">
  <div class="w-14 flex-none ...">01</div>
  <div class="w-64 flex-auto ...">02</div>
  <div class="w-32 flex-auto ...">03</div>
</div>
```
### None
Use <code>flex-none</code> to prevent a flex item from growing or shrinking:
```
<div class="flex ...">
  <div class="w-14 flex-none ...">01</div>
  <div class="w-32 flex-none ...">02</div>
  <div class="flex-1 ...">03</div>
</div>
```
### Using a custom value
Use the <code>flex-[<value>]</code> syntax to set the flex shorthand property based on a completely custom value:
```
<div class="flex-[3_1_auto] ...">
  <!-- ... -->
</div>
```

## Ref
- [flex](https://tailwindcss.com/docs/flex)
- [Responsive design](https://tailwindcss.com/docs/flex#responsive-design)
