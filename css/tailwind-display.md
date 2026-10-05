---
layout: ../../layouts/MarkdownPostLayout.astro
title: "display"
description: "Utilities for controlling the display box type of an element."
date: 2025-04-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|inline|display: inline;|
|block|display: block;|
|inline-block|display: inline-block;|
|hidden|display: none;|

常用值:
- Block and Inline
- Hidden

特殊值:
- Screen-reader only
```
position: absolute;
width: 1px;
height: 1px;
padding: 0;
margin: -1px;
overflow: hidden;
clip: rect(0, 0, 0, 0);
white-space: nowrap;
border-width: 0;
```
- not-sr-only
```
position: static;
width: auto;
height: auto;
padding: 0;
margin: 0;
overflow: visible;
clip: auto;
white-space: normal;
```


### Block and Inline
Use the <code>inline</code>, <code>inline-block</code>, and <code>block</code> 
utilities to control the flow of text and elements:
```
<p>
  When controlling the flow of text, using the CSS property <span class="inline">display: inline</span> will cause the
  text inside the element to wrap normally.
</p>
<p>
  While using the property <span class="inline-block">display: inline-block</span> will wrap the element to prevent the
  text inside from extending beyond its parent.
</p>
<p>
  Lastly, using the property <span class="block">display: block</span> will put the element on its own line and fill its
  parent.
</p>
```

### Hidden
Use the <code>hidden</code> utility to remove an element from the document:
```
<div class="flex ...">
  <div class="hidden ...">01</div>
  <div>02</div>
  <div>03</div>
</div>
```

### Screen-reader only
Use <code>sr-only</code> to hide an element visually without hiding it from screen readers:
```
<a href="#">
  <svg><!-- ... --></svg>
  <span class="sr-only">Settings</span>
</a>
```
Use <code>not-sr-only</code> to undo <code>sr-only</code>, making an element visible to sighted users as well as screen readers:
```
<a href="#">
  <svg><!-- ... --></svg>
  <span class="sr-only sm:not-sr-only">Settings</span>
</a>
```

## Ref
- [display - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
- [display](https://tailwindcss.com/docs/display)
- [Responsive design](https://tailwindcss.com/docs/display#responsive-design)
