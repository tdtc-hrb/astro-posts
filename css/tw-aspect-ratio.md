---
layout: ../../layouts/MarkdownPostLayout.astro
title: "aspect-ratio"
description: "Utilities for controlling the aspect ratio of an element."
date: 2025-04-16
author: "tdtc"
---

|Class|Styles|
|-|-|
|`aspect-<ratio>`|`aspect-ratio: <ratio>;`|
|aspect-square|aspect-ratio: 1 / 1;|
|aspect-video|aspect-ratio: var(--aspect-ratio-video); /* 16 / 9 */|
|aspect-auto|aspect-ratio: auto;|
|`aspect-(<custom-property>)`|`aspect-ratio: var(<custom-property>);`|
|`aspect-[<value>]`|`aspect-ratio: <value>;`|

### Basic example
Use <code>aspect-<ratio></code> utilities like <code>aspect-3/2</code> to give an element a specific aspect ratio:
```
<img class="aspect-3/2 object-cover ..." src="/img/villas.jpg" />
```

### Using a video aspect ratio
Use the <code>aspect-video</code> utility to give a video element a 16 / 9 aspect ratio:
```
<iframe class="aspect-video ..." src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe>
```

### Using a custom value
Use the <code>aspect-[<value>]</code> syntax to set the aspect ratio based on a completely custom value:
```
<img class="aspect-[calc(4*3+1)/3] ..." src="/img/villas.jpg" />
```

## Ref
- [aspect-ratio](https://tailwindcss.com/docs/aspect-ratio)
- [Responsive design](https://tailwindcss.com/docs/aspect-ratio#responsive-design)
