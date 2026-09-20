---
layout: ../../layouts/MarkdownPostLayout.astro
title: "resize"
description: "Utilities for controlling how an element can be resized."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|resize-none|resize: none;|
|resize|resize: both;|
|resize-y|resize: vertical;|
|resize-x|resize: horizontal;|

### Resizing in all directions
Use <code>resize</code> to make an element horizontally and vertically resizable:
```
<textarea class="resize rounded-md ..."></textarea>
```

### Resizing vertically
Use <code>resize-y</code> to make an element vertically resizable:
```
<textarea class="resize-y rounded-md ..."></textarea>
```

### Resizing horizontally
Use <code>resize-x</code> to make an element horizontally resizable:
```
<textarea class="resize-x rounded-md ..."></textarea>
```

### Prevent resizing
Use <code>resize-none</code> to prevent an element from being resizable:
```
<textarea class="resize-none rounded-md"></textarea>
```

## Ref
- [resize](https://tailwindcss.com/docs/resize)
- [Responsive design](https://tailwindcss.com/docs/resize#responsive-design)
