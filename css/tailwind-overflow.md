---
layout: ../../layouts/MarkdownPostLayout.astro
title: "overflow"
description: "Utilities for controlling how an element handles content that is too large for the container."
date: 2025-04-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|overflow-auto|overflow: auto;|
|overflow-hidden|overflow: hidden;|
|overflow-clip|overflow: clip;|
|overflow-visible|overflow: visible;|
|overflow-scroll|overflow: scroll;|

#### overflow-x and overflow-y
- auto
- hidden
- clip
- visible
- scroll

for example:
```
overflow-x-auto
```

### Showing content that overflows
Use the <code>overflow-visible</code> utility to prevent content within an element from being clipped:
```
<div class="overflow-visible ...">
  <!-- ... -->
</div>
```
Note that any content that overflows the bounds of the element will then be visible.

### Hiding content that overflows
Use the <code>overflow-hidden</code> utility to clip any content within an element that overflows the bounds of that element:
```
<div class="overflow-hidden ...">
  <!-- ... -->
</div>
```

### Scrolling if needed
Use the <code>overflow-auto</code> utility to add scrollbars to 
an element in the event that its content overflows the bounds of that element:
```
<div class="overflow-auto ...">
  <!-- ... -->
</div>
```
Unlike <code>overflow-scroll</code>, which always shows scrollbars, 
this utility will only show them if scrolling is necessary.

### Scrolling horizontally if needed
Use the <code>overflow-x-auto</code> utility to allow horizontal scrolling if needed:
```
<div class="overflow-x-auto ...">
  <!-- ... -->
</div>
```

### Scrolling vertically if needed
Use the <code>overflow-y-auto</code> utility to allow vertical scrolling if needed:
```
<div class="h-32 overflow-y-auto ...">
  <!-- ... -->
</div>
```

### Scrolling horizontally always
Use the <code>overflow-x-scroll</code> utility to allow 
horizontal scrolling and always show scrollbars unless always-visible 
scrollbars are disabled by the operating system:
```
<div class="overflow-x-scroll ...">
  <!-- ... -->
</div>
```

### Scrolling vertically always
Use the <code>overflow-y-scroll</code> utility to allow 
vertical scrolling and always show scrollbars unless always-visible 
scrollbars are disabled by the operating system:
```
<div class="overflow-y-scroll ...">
  <!-- ... -->
</div>
```

### Scrolling in all directions
Use the <code>overflow-scroll</code> utility to add scrollbars to an element:
```
<div class="overflow-scroll ...">
  <!-- ... -->
</div>
```
Unlike <code>overflow-auto</code>, which only shows scrollbars if they are necessary, 
this utility always shows them. Note that some operating systems (like macOS) 
hide unnecessary scrollbars regardless of this setting.

## Ref
- [overflow](https://tailwindcss.com/docs/overflow)
- [Responsive design](https://tailwindcss.com/docs/overflow#responsive-design)
