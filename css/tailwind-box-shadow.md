---
layout: ../../layouts/MarkdownPostLayout.astro
title: "box shadow"
description: "Utilities for controlling the box shadow of an element."
date: 2025-04-18
author: "tdtc"
---
所有以
```
shadow:
```
开头都是box阴影

### Basic example
Use utilities like <code>shadow-sm</code> and <code>shadow-lg</code> to apply different sized outer box shadows to an element:
```
<div class="shadow-md ..."></div>
<div class="shadow-lg ..."></div>
<div class="shadow-xl ..."></div>
```

### Setting the shadow color
Use utilities like <code>shadow-indigo-500</code> and <code>shadow-cyan-500/50</code> to change the color of a box shadow:
```
<button class="bg-cyan-500 shadow-lg shadow-cyan-500/50 ...">Subscribe</button>
<button class="bg-blue-500 shadow-lg shadow-blue-500/50 ...">Subscribe</button>
<button class="bg-indigo-500 shadow-lg shadow-indigo-500/50 ...">Subscribe</button>
```
### Adding an inset shadow
Use utilities like <code>inset-shadow-xs</code> and <code>inset-shadow-sm</code> to apply an inset box shadow to an element:
```
<div class="inset-shadow-2xs ..."></div>
<div class="inset-shadow-xs ..."></div>
<div class="inset-shadow-sm ..."></div>
```
These utilities can be useful for things like form controls or wells.

### Setting the inset shadow color
Use utilities like <code>inset-shadow-indigo-500</code> and <code>inset-shadow-cyan-500/50</code> to change the color of an inset box shadow:
```
<div class="inset-shadow-sm inset-shadow-indigo-500 ..."></div>
<div class="inset-shadow-sm inset-shadow-indigo-500/50 ..."></div>
```

### Adding a ring
Use <code>ring</code> or <code>ring-<number></code> utilities 
like <code>ring-2</code> and <code>ring-4</code> to apply a solid box-shadow to an element:
```
<button class="ring ...">Subscribe</button>
<button class="ring-2 ...">Subscribe</button>
<button class="ring-4 ...">Subscribe</button>
```
By default rings match the currentColor of the element they are applied to.

### Setting the ring color
Use utilities like <code>ring-indigo-500</code> and <code>ring-cyan-500/50</code> to change the color of a ring:
```
<button class="ring-2 ring-blue-500 ...">Subscribe</button>
<button class="ring-2 ring-blue-500/50 ...">Subscribe</button>
```
By default rings have an opacity of 100% but you can adjust this using the opacity modifier.

### Adding an inset ring
Use <code>inset-ring</code> or <code>inset-ring-<number></code> utilities 
like <code>inset-ring-2</code> and <code>inset-ring-4</code> to apply a solid inset box-shadow to an element:
```
<button class="inset-ring ...">Subscribe</button>
<button class="inset-ring-2 ...">Subscribe</button>
<button class="inset-ring-4 ...">Subscribe</button>
```
By default inset rings match the currentColor of the element they are applied to.

### Setting the inset ring color
Use utilities like <code>inset-ring-indigo-500</code> and <code>inset-ring-cyan-500/50</code> to change the color of an inset ring:
```
<button class="inset-ring-2 inset-ring-blue-500 ...">Subscribe</button>
<button class="inset-ring-2 inset-ring-blue-500/50 ...">Subscribe</button>
```
By default inset rings have an opacity of 100% but you can adjust this using the opacity modifier.

### Removing a box shadow
Use the <code>shadow-none</code>, <code>inset-shadow-none</code>,<code>ring-0</code>, and 
<code>inset-ring-0</code> utilities to remove an existing box shadow from an element:
```
<div class="shadow-none ..."></div>
```

### Using a custom value
Use utilities like <code>shadow-[<value>]</code>,<code>inset-shadow-[<value>]</code>,
<code>ring-[<value>]</code>, and <code>inset-ring-[<value>]</code> to set the box shadow based on a completely custom value:
```
<div class="shadow-[0_35px_35px_rgba(0,0,0,0.25)] ...">
  <!-- ... -->
</div>
```
for example:
- page-link:focus
> v4.6.2
```
box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
```
tw:
```
<button class="shadow-[0_0px_0px_4px_rgba(0,123,255,0.25)]">tailwind</button>
```

## Ref
- [box shadow](https://tailwindcss.com/docs/box-shadow)
- [Responsive design](https://tailwindcss.com/docs/box-shadow#responsive-design)
- [Box shadow - generator](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_backgrounds_and_borders/Box-shadow_generator)
