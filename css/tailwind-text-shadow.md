---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text shadow"
description: "Utilities for controlling the shadow of a text element."
date: 2025-04-06
author: "tdtc"
---
April 3, 2025

Tailwind CSS v4.1: Text shadows, masks, and tons more

I wasn't sure it would ever happen but we did it — we released a version of Tailwind CSS that includes text-shadow utilities.


|Class|Styles|
|-|-|
|text-shadow-2xs|text-shadow: var(--text-shadow-2xs);||
|text-shadow-xs|text-shadow: var(--text-shadow-xs);||
|text-shadow-sm|text-shadow: var(--text-shadow-sm);||
|text-shadow-md|text-shadow: var(--text-shadow-md);||
|text-shadow-lg|text-shadow: var(--text-shadow-lg);||
|text-shadow-none|text-shadow: none;|
|`text-shadow-(<custom-property>)`|`text-shadow: var(<custom-property>);`|
|`text-shadow-(color:<custom-property>)`|`--tw-shadow-color var(<custom-property>);`|
|`text-shadow-[<value>]`|`text-shadow: <value>;`|
|text-shadow-inherit|--tw-shadow-color inherit;|
|text-shadow-current|--tw-shadow-color currentColor;|
|text-shadow-transparent|--tw-shadow-color transparent;|


### Basic example
Use utilities like <code>text-shadow-sm</code> and <code>shadow-lg</code> to apply different sized text shadows to a text element:
```
<p class="text-shadow-2xs ...">The quick brown fox...</p>
<p class="text-shadow-xs ...">The quick brown fox...</p>
<p class="text-shadow-sm ...">The quick brown fox...</p>
<p class="text-shadow-md ...">The quick brown fox...</p>
<p class="text-shadow-lg ...">The quick brown fox...</p>
```

### Changing the opacity
Use the opacity modifier to adjust the opacity of the text shadow:
```
<p class="text-shadow-lg ...">The quick brown fox...</p>
<p class="text-shadow-lg/20 ...">The quick brown fox...</p>
<p class="text-shadow-lg/30 ...">The quick brown fox...</p>
```
The default text shadow opacities are quite low (20% or less), 
so increasing the opacity (to like 50%) will make the text shadows more pronounced.

### Setting the shadow color
Use utilities like <code>text-shadow-indigo-500</code> and <code>text-shadow-cyan-500/50</code> to change the color of a text shadow:
```
<button class="text-sky-950 text-shadow-2xs text-shadow-sky-300 ...">Book a demo</button>
<button class="text-gray-950 dark:text-white dark:text-shadow-2xs ...">See pricing</button>
```
By default colored shadows have an opacity of 100% but you can adjust this using the opacity modifier.

### Removing a text shadow
Use the <code>text-shadow-none</code> utility to remove an existing text shadow from an element:
```
<p class="text-shadow-lg dark:text-shadow-none">
  <!-- ... -->
</p>
```

### Using a custom value
Use the <code>text-shadow-[<value>]</code> syntax to set the text shadow based on a completely custom value:
```
<p class="text-shadow-[0_35px_35px_rgb(0_0_0_/_0.25)] ...">
  Lorem ipsum dolor sit amet...
</p>
```

## Ref
- [text shadow](https://tailwindcss.com/docs/text-shadow)
- [Responsive design](https://tailwindcss.com/docs/text-shadow#responsive-design)
- [Tailwind CSS v4.1: Text shadows](https://tailwindcss.com/blog/tailwindcss-v4-1)
