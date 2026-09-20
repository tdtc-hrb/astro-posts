---
layout: ../../layouts/MarkdownPostLayout.astro
title: "user select"
description: "Utilities for controlling the position of an element's background image."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|select-none|user-select: none;|
|select-text|user-select: text;|
|select-all|user-select: all;|
|select-auto|user-select: auto;|

### Disabling text selection
Use the <code>select-none</code> utility to prevent selecting text in an element and its children:
```
<div class="select-none ...">The quick brown fox jumps over the lazy dog.</div>
```

### Allowing text selection
Use the <code>select-text</code> utility to allow selecting text in an element and its children:
```
<div class="select-text ...">The quick brown fox jumps over the lazy dog.</div>
```

### Selecting all text in one click
Use the <code>select-all</code> utility to automatically select all the text in an element when a user clicks:
```
<div class="select-all ...">The quick brown fox jumps over the lazy dog.</div>
```

### Using auto select behavior
Use the <code>select-auto</code> utility to use the default browser behavior for selecting text:
```
<div class="select-auto ...">The quick brown fox jumps over the lazy dog.</div>
```

## Ref
- [user select](https://tailwindcss.com/docs/user-select)
- [Responsive design](https://tailwindcss.com/docs/user-select#responsive-design)
