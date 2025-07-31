---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex wrap"
description: "Utilities for controlling how flex items wrap."
date: 2025-03-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|flex-nowrap|flex-wrap: nowrap;|
|flex-wrap|flex-wrap: wrap;|
|flex-wrap-reverse|flex-wrap: wrap-reverse;|

## flex-wrap
- Don't wrap
- Wrap normally
- Wrap reversed

### Don't wrap
Use <code>flex-nowrap</code> to prevent flex items from wrapping, 
causing inflexible items to overflow the container if necessary:
```
<div class="flex flex-nowrap">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
### Wrap normally
Use <code>flex-wrap</code> to allow flex items to wrap:
```
<div class="flex flex-wrap">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```
### Wrap reversed
Use <code>flex-wrap-reverse</code> to wrap flex items in the reverse direction:
```
<div class="flex flex-wrap-reverse">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

## Ref
- [flex wrap](https://tailwindcss.com/docs/flex-wrap)
- [Responsive design](https://tailwindcss.com/docs/flex-wrap#responsive-design)
