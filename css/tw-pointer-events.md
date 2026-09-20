---
layout: ../../layouts/MarkdownPostLayout.astro
title: "pointer events"
description: "Utilities for controlling whether an element responds to pointer events."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|pointer-events-auto|pointer-events: auto;|
|pointer-events-none|pointer-events: none;|

### Ignoring pointer events
Use the <code>pointer-events-none</code> utility to make an element ignore pointer events, 
like <code>:hover</code> and <code>click</code> events:
```
<div class="relative ...">
  <div class="pointer-events-auto absolute ...">
    <svg class="absolute h-5 w-5 text-gray-400">
      <!-- ... -->
    </svg>
  </div>
  <input type="text" placeholder="Search" class="..." />
</div>
<div class="relative ...">
  <div class="pointer-events-none absolute ...">
    <svg class="absolute h-5 w-5 text-gray-400">
      <!-- ... -->
    </svg>
  </div>
  <input type="text" placeholder="Search" class="..." />
</div>
```
The pointer events will still trigger on child elements and pass-through to elements that are "beneath" the target.


## Ref
- [pointer events](https://tailwindcss.com/docs/pointer-events)
