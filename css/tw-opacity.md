---
layout: ../../layouts/MarkdownPostLayout.astro
title: "opacity"
description: "Utilities for controlling the opacity of an element."
date: 2025-04-12
author: "tdtc"
---

|Class|Styles|
|-|-|
|`opacity-<number>`|`opacity: <number>%;`|
|`opacity-(<custom-property>)`|`opacity: var(<custom-property>);`|
|`opacity-[<value>]`|`opacity: <value>;`|

### Basic example
Use <code>opacity-<number></code> utilities like <code>opacity-25</code> 
and <code>opacity-100</code> to set the opacity of an element:
```
<button class="bg-indigo-500 opacity-100 ..."></button>
<button class="bg-indigo-500 opacity-75 ..."></button>
<button class="bg-indigo-500 opacity-50 ..."></button>
<button class="bg-indigo-500 opacity-25 ..."></button>
```

### Applying conditionally
Prefix an <code>opacity</code> utility with a variant like <code>disabled:*</code> to only apply the utility in that state:
```
<input class="opacity-100 disabled:opacity-75 ..." type="text" />
```
Learn more about using variants in the [variants documentation](https://tailwindcss.com/docs/hover-focus-and-other-states).

### Using a custom value
Use the <code>opacity-[<value>]</code> syntax to set the opacity based on a completely custom value:
```
<button class="opacity-[.67] ...">
  <!-- ... -->
</button>
```

## Ref
- [opacity](https://tailwindcss.com/docs/opacity)
- [Responsive design](https://tailwindcss.com/docs/opacity#responsive-design)
