---
layout: ../../layouts/MarkdownPostLayout.astro
title: "justify content"
description: "Utilities for controlling how flex and grid items are positioned along a container's main axis."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|justify-start|justify-content: flex-start;|
|justify-end|justify-content: flex-end;|
|justify-center|justify-content: center;|
|justify-between|justify-content: space-between;|
|justify-around|justify-content: space-around;|
|justify-evenly|justify-content: space-evenly;|
|justify-stretch|justify-content: stretch;|
|justify-baseline|justify-content: baseline;|
|justify-normal|justify-content: normal;|

### Start
Use <code>justify-start</code> to justify items against the start of the container's main axis:
```
<div class="flex justify-start ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Center
Use <code>justify-center</code> to justify items along the center of the container's main axis:
```
<div class="flex justify-center ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### End
Use <code>justify-end</code> to justify items against the end of the container's main axis:
```
<div class="flex justify-end ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Space between
Use <code>justify-between</code> to justify items along the container's main axis 
such that there is an equal amount of space between each item:
```
<div class="flex justify-between ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Space around
Use <code>justify-around</code> to justify items along the container's main axis 
such that there is an equal amount of space on each side of each item:
```
<div class="flex justify-around ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Space evenly
Use <code>justify-evenly</code> to justify items along the container's main axis 
such that there is an equal amount of space around each item, 
but also accounting for the doubling of space you would normally see between 
each item when using <code>justify-around</code>:
```
<div class="flex justify-evenly ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Stretch
Use <code>justify-stretch</code> to allow content items to fill the available space along the container's main axis:
```
<div class="flex justify-stretch ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Normal
Use <code>justify-normal</code> to pack content items in their 
default position as if no <code>justify-content</code> value was set:
```
<div class="flex justify-normal ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
</div>
```

## Ref
- [justify content](https://tailwindcss.com/docs/justify-content)
- [Responsive design](https://tailwindcss.com/docs/justify-content#responsive-design)
