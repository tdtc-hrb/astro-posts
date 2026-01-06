---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex direction"
description: "Utilities for controlling the direction of flex items."
date: 2025-03-06
author: "tdtc"
---
|Class|Styles|
|-|-|
|flex-row|flex-direction: row;|
|flex-row-reverse|flex-direction: row-reverse;|
|flex-col|flex-direction: column;|
|flex-col-reverse|flex-direction: column-reverse;|

## flex-direction
- Row
- Row reversed
- Column
- Column reversed

### Using the spacing scale
Use <code>flex-row</code> to position flex items horizontally in the same direction as text:
```
<div class="flex flex-row ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
### Row reversed
Use <code>flex-row-reverse</code> to position flex items horizontally in the opposite direction:
```
<div class="flex flex-row-reverse ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
### Column
Use <code>flex-col</code> to position flex items vertically:
```
<div class="flex flex-col ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
### Column reversed
Use <code>flex-col-reverse</code> to position flex items vertically in the opposite direction:
```
<div class="flex flex-col-reverse ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

## Ref
- [flex direction](https://tailwindcss.com/docs/flex-direction)
- [Responsive design](https://tailwindcss.com/docs/flex-direction#responsive-design)
