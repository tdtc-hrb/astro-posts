---
layout: ../../layouts/MarkdownPostLayout.astro
title: "组 align"
description: "Utilities for controlling how flex and grid items are positioned along a container's cross axis."
date: 2025-03-13
author: "tdtc"
---
|Class|Styles|
|-|-|
|items-start|align-items: flex-start;|
|items-end|align-items: flex-end;|
|items-center|align-items: center;|
|items-baseline|align-items: baseline;|
|items-stretch|align-items: stretch;|

### Stretch
Use <code>items-stretch</code> to stretch items to fill the container's cross axis:
```
<div class="flex items-stretch ...">
  <div class="py-4">01</div>
  <div class="py-12">02</div>
  <div class="py-8">03</div>
</div>
```

### Start
Use <code>items-start</code> to align items to the start of the container's cross axis:
```
<div class="flex items-start ...">
  <div class="py-4">01</div>
  <div class="py-12">02</div>
  <div class="py-8">03</div>
</div>
```

### Center
Use <code>items-center</code> to align items along the center of the container's cross axis:
```
<div class="flex items-center ...">
  <div class="py-4">01</div>
  <div class="py-12">02</div>
  <div class="py-8">03</div>
</div>
```

### End
Use <code>items-end</code> to align items to the end of the container's cross axis:
```
<div class="flex items-end ...">
  <div class="py-4">01</div>
  <div class="py-12">02</div>
  <div class="py-8">03</div>
</div>
```

### Baseline
Use <code>items-baseline</code> to align items along the container's cross axis such that all of their baselines align:
```
<div class="flex items-baseline ...">
  <div class="pt-2 pb-6">01</div>
  <div class="pt-8 pb-12">02</div>
  <div class="pt-12 pb-4">03</div>
</div>
```

## Ref
- [align items](https://tailwindcss.com/docs/align-items)
- [Responsive design](https://tailwindcss.com/docs/align-items#responsive-design)
