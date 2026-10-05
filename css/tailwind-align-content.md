---
layout: ../../layouts/MarkdownPostLayout.astro
title: "align content(flex and grid)"
description: "Utilities for controlling how rows are positioned in multi-row flex and grid containers."
date: 2025-04-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|content-normal|align-content: normal;|
|content-center|align-content: center;|
|content-start|align-content: flex-start;|
|content-end|align-content: flex-end;|
|content-between|align-content: space-between;|
|content-around|align-content: space-around;|
|content-evenly|align-content: space-evenly;|
|content-baseline|align-content: baseline;|
|content-stretch|align-content: stretch;|

### Start
Use <code>content-start</code> to pack rows in a container against the start of the cross axis:
```
<div class="grid h-56 grid-cols-3 content-start gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Center
Use <code>content-center</code> to pack rows in a container in the center of the cross axis:
```
<div class="grid h-56 grid-cols-3 content-center gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### End
Use <code>content-end</code> to pack rows in a container against the end of the cross axis:
```
<div class="grid h-56 grid-cols-3 content-end gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Space between
Use <code>content-between</code> to distribute rows in a container such that there is an equal amount of space between each line:
```
<div class="grid h-56 grid-cols-3 content-between gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Space around
Use <code>content-around</code> to distribute rows in a container such that there is an equal amount of space around each line:
```
<div class="grid h-56 grid-cols-3 content-around gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Space evenly
Use <code>content-evenly</code> to distribute rows in a container such 
that there is an equal amount of space around each item, but also accounting for 
the doubling of space you would normally see between each item when using <code>content-around</code>:
```
<div class="grid h-56 grid-cols-3 content-evenly gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Stretch
Use <code>content-stretch</code> to allow content items to fill the available space along the container’s cross axis:
```
<div class="grid h-56 grid-cols-3 content-stretch gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

### Normal
Use <code>content-normal</code> to pack content items in their 
default position as if no <code>align-content</code> value was set:
```
<div class="grid h-56 grid-cols-3 content-normal gap-4 ...">
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
</div>
```

## Ref
- [align content](https://tailwindcss.com/docs/align-content)
- [Responsive design](https://tailwindcss.com/docs/align-content#responsive-design)
