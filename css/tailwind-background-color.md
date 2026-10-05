---
layout: ../../layouts/MarkdownPostLayout.astro
title: "background color"
description: "Utilities for controlling an element's background color."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|bg-inherit|background-color: inherit;|
|bg-current|background-color: currentColor;|
|bg-transparent|background-color: transparent;|
|bg-black|background-color: var(--color-black); /* #000 */|
|bg-white|background-color: var(--color-white); /* #fff */|
|`bg-(<custom-property>)`|`background-color: var(<custom-property>);`|
|`bg-[<value>]`|`background-color: <value>;`|

#### other color
see [colors](https://tdtc-hrb.github.io/css-tws/posts/tailwind-colors)

### Basic example
Use utilities like <code>bg-white</code>, <code>bg-indigo-500</code> and <code>bg-transparent</code> to 
control the background color of an element:
```
<button class="bg-blue-500 ...">Button A</button>
<button class="bg-cyan-500 ...">Button B</button>
<button class="bg-pink-500 ...">Button C</button>
```

### Changing the opacity
Use the color opacity modifier to control the opacity of an element's background color:
```
<button class="bg-sky-500/100 ..."></button>
<button class="bg-sky-500/75 ..."></button>
<button class="bg-sky-500/50 ..."></button>
```

### Using a custom value
Use the <code>bg-[<value>]</code> syntax to set the background color based on a completely custom value:
```
<div class="bg-[#50d71e] ...">
  <!-- ... -->
</div>
```

### Applying on hover
Prefix a <code>background-color</code> utility with a variant like <code>hover:*</code> to 
only apply the utility in that state:
```
<button class="bg-indigo-500 hover:bg-fuchsia-500 ...">Save changes</button>
```

## Ref
- [background color](https://tailwindcss.com/docs/background-color)
- [Responsive design](https://tailwindcss.com/docs/background-color#responsive-design)
