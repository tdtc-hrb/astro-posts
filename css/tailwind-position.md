---
layout: ../../layouts/MarkdownPostLayout.astro
title: "position"
description: "Utilities for controlling how an element is positioned in the document."
date: 2025-04-08
author: "tdtc"
---
|Class|Styles|
|-|-|
|static|position: static;|
|fixed|position: fixed;|
|absolute|position: absolute;|
|relative|position: relative;|
|sticky|position: sticky;|

### Statically positioning elements
Use the <code>static</code> utility to position an element according to the normal flow of the document:
```
<div class="static ...">
  <p>Static parent</p>
  <div class="absolute bottom-0 left-0 ...">
    <p>Absolute child</p>
  </div>
</div>
```
With statically positioned elements, any [offsets](https://tailwindcss.com/docs/top-right-bottom-left) 
will be ignored and the element will not act as a position reference for absolutely positioned children.

### Relatively positioning elements
Use the <code>relative</code> utility to position an element according to the normal flow of the document:
```
<div class="relative ...">
  <p>Relative parent</p>
  <div class="absolute bottom-0 left-0 ...">
    <p>Absolute child</p>
  </div>
</div>
```
With relatively position elements, any [offsets](https://tailwindcss.com/docs/top-right-bottom-left) 
are calculated relative to the element's normal position and the element 
will act as a position reference for absolutely positioned children.

### Absolutely positioning elements
Use the <code>absolute</code> utility to position an element outside of the normal flow of the document, 
causing neighboring elements to act as if the element doesn't exist:
```
<div class="static ...">
  <!-- Static parent -->
  <div class="static ..."><p>Static child</p></div>
  <div class="inline-block ..."><p>Static sibling</p></div>
  <!-- Static parent -->
  <div class="absolute ..."><p>Absolute child</p></div>
  <div class="inline-block ..."><p>Static sibling</p></div>
</div>
```
With absolutely positioned elements, any [offsets](https://tailwindcss.com/docs/top-right-bottom-left) 
are calculated relative to the nearest parent that has a position other than <code>static</code>, 
and the element will act as a position reference for other absolutely positioned children.

### Fixed positioning elements
Use the <code>fixed</code> utility to position an element relative to the browser window:
```
<div class="relative">
  <div class="fixed top-0 right-0 left-0">Contacts</div>
  <div>
    <div>
      <img src="/img/andrew.jpg" />
      <strong>Andrew Alfred</strong>
    </div>
    <div>
      <img src="/img/debra.jpg" />
      <strong>Debra Houston</strong>
    </div>
    <!-- ... -->
  </div>
</div>
```
With fixed positioned elements, any [offsets](https://tailwindcss.com/docs/top-right-bottom-left) 
are calculated relative to the viewport and the element will act as a position reference for absolutely positioned children.

### Sticky positioning elements
Use the <code>sticky</code> utility to position an element as <code>relative</code> until it 
crosses a specified threshold, then treat it as <code>fixed</code> until its parent is off screen:
```
<div>
  <div>
    <div class="sticky top-0 ...">A</div>
    <div>
      <div>
        <img src="/img/andrew.jpg" />
        <strong>Andrew Alfred</strong>
      </div>
      <div>
        <img src="/img/aisha.jpg" />
        <strong>Aisha Houston</strong>
      </div>
      <!-- ... -->
    </div>
  </div>
  <div>
    <div class="sticky top-0">B</div>
    <div>
      <div>
        <img src="/img/bob.jpg" />
        <strong>Bob Alfred</strong>
      </div>
      <!-- ... -->
    </div>
  </div>
  <!-- ... -->
</div>
```
With sticky positioned elements, any [offsets](https://tailwindcss.com/docs/top-right-bottom-left) 
are calculated relative to the element's normal position and the element 
will act as a position reference for absolutely positioned children.

## Ref
- [position](https://tailwindcss.com/docs/position)
- [Responsive design](https://tailwindcss.com/docs/position#responsive-design)
