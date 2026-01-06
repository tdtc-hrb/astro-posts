---
layout: ../../layouts/MarkdownPostLayout.astro
title: "border radius"
description: "Utilities for controlling the border radius of an element."
date: 2025-04-12
author: "tdtc"
---
|Class|Styles|
|-|-|
|rounded-xs|border-radius: var(--radius-xs); /* 0.125rem (2px) */|
|rounded-sm|border-radius: var(--radius-sm); /* 0.25rem (4px) */|
|rounded-md|border-radius: var(--radius-md); /* 0.375rem (6px) */|
|rounded-lg|border-radius: var(--radius-lg); /* 0.5rem (8px) */|
|rounded-xl|border-radius: var(--radius-xl); /* 0.75rem (12px) */|
|rounded-2xl|border-radius: var(--radius-2xl); /* 1rem (16px) */|
|rounded-3xl|border-radius: var(--radius-3xl); /* 1.5rem (24px) */|
|rounded-4xl|border-radius: var(--radius-4xl); /* 2rem (32px) */|
|rounded-none|border-radius: 0;|
|rounded-full|border-radius: calc(infinity * 1px);|
|`rounded-(<custom-property>)`|`border-radius: var(<custom-property>);`|
|`rounded-[<value>]`|`border-radius: <value>;`|

#### direction
- t, r, b, l,
> top, right, bottom, left

for example:
```
rounded-b-xs
```

- tl, tr, br, bl
> top-left, top-right, bottom-right, bottom-left

for example: 
```
rounded-tl-sm
```

#### Dimension Point
- s
> start-start and end-start

for example:
```
rounded-s-md
```

- e
> start-end and end-end

for example: 
```
rounded-e-lg
```

- ss
> start-start

for example:
```
rounded-ss-xl
```

- se
> start-end

for example: 
```
rounded-se-2xl
```

- ee
> end-end

for example: 
```
rounded-ee-3xl
```

- es
> end-start

for example: 
```
rounded-es-4xl
```


### Basic example
Use utilities like <code>rounded-sm</code> and <code>rounded-md</code> to apply different border radius sizes to an element:
```
<div class="rounded-sm ..."></div>
<div class="rounded-md ..."></div>
<div class="rounded-lg ..."></div>
<div class="rounded-xl ..."></div>
```

### Rounding sides separately
Use utilities like <code>rounded-t-md</code> and <code>rounded-r-lg</code> to only round one side of an element:
```
<div class="rounded-t-lg ..."></div>
<div class="rounded-r-lg ..."></div>
<div class="rounded-b-lg ..."></div>
<div class="rounded-l-lg ..."></div>
```

### Rounding corners separately
Use utilities like <code>rounded-tr-md</code> and <code>rounded-tl-lg</code> utilities to only round one corner of an element:
```
<div class="rounded-tl-lg ..."></div>
<div class="rounded-tr-lg ..."></div>
<div class="rounded-br-lg ..."></div>
<div class="rounded-bl-lg ..."></div>
```

### Using logical properties
Use utilities like <code>rounded-s-md</code> and <code>rounded-se-xl</code> to set 
the border radius using logical properties, which map to the appropriate corners based on the text direction:
```
<div dir="ltr">
  <div class="rounded-s-lg ..."></div>
</div>
<div dir="rtl">
  <div class="rounded-s-lg ..."></div>
</div>
```

Here are all the available border radius logical property utilities and 
their physical property equivalents in both LTR(Left-to-right) and RTL(Right-to-left) modes.

|Class|Left-to-right|Right-to-left|
|-|-|-|
|rounded-s-*|rounded-l-*|rounded-r-*|
|rounded-e-*|rounded-r-*|rounded-l-*|
|rounded-ss-*|rounded-tl-*|rounded-tr-*|
|rounded-se-*|rounded-tr-*|rounded-tl-*|
|rounded-es-*|rounded-bl-*|rounded-br-*|
|rounded-ee-*|rounded-br-*|rounded-bl-*|

For more control, you can also use the [LTR and RTL modifiers](https://tailwindcss.com/docs/hover-focus-and-other-states#rtl-support) to 
conditionally apply specific styles depending on the current text direction.

### Creating pill buttons
Use the <code>rounded-full</code> utility to create pill buttons:
```
<button class="rounded-full ...">Save Changes</button>
```

### Removing the border radius
Use the <code>rounded-none</code> utility to remove an existing border radius from an element:
```
<button class="rounded-none ...">Save Changes</button>
```

### Using a custom value
Use the <code>rounded-[<value>]</code> syntax to set the border radius based on a completely custom value:
```
<div class="rounded-[2vw] ...">
  <!-- ... -->
</div>
```

## Ref
- [border radius](https://tailwindcss.com/docs/border-radius)
- [Responsive design](https://tailwindcss.com/docs/border-radius#responsive-design)
