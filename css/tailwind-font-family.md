---
layout: ../../layouts/MarkdownPostLayout.astro
title: "font family"
description: "Utilities for controlling the font family of an element."
date: 2025-04-12
author: "tdtc"
---

|Class|Styles|
|-|-|
|font-sans|font-family: var(--font-sans); /* ui-sans-serif, system-ui, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji' */|
|font-serif|font-family: var(--font-serif); /* ui-serif, Georgia, Cambria, 'Times New Roman', Times, serif */|
|font-mono|font-family: var(--font-mono); /* ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New', monospace */|
|`font-(family-name:<custom-property>)`|`font-family: var(<custom-property>);`|
|`font-[<value>]`|`font-family: <value>;`|

### Basic example
Use utilities like <code>font-sans</code> and <code>font-mono</code> to set the font family of an element:
```
<p class="font-sans ...">The quick brown fox ...</p>
<p class="font-serif ...">The quick brown fox ...</p>
<p class="font-mono ...">The quick brown fox ...</p>
```

### Using a custom value
Use the <code>font-[<value>]</code> syntax to set the font family based on a completely custom value:
```
<p class="font-[Open_Sans] ...">
  Lorem ipsum dolor sit amet...
</p>
```

## Ref
- [font family](https://tailwindcss.com/docs/font-family)
- [Responsive design](https://tailwindcss.com/docs/font-family#responsive-design)
