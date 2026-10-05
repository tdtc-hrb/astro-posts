---
layout: ../../layouts/MarkdownPostLayout.astro
title: "font size"
description: "Utilities for controlling the font size of an element."
date: 2025-03-13
author: "tdtc"
---
Class|Styles
|-|-|
|text-xs|font-size: var(--text-xs); /* 0.75rem (12px) */ <br>line-height: var(--text-xs--line-height); /* calc(1 / 0.75) */|
|text-sm|font-size: var(--text-sm); /* 0.875rem (14px) */ <br> line-height: var(--text-sm--line-height); /* calc(1.25 / 0.875) */|
|text-base|font-size: var(--text-base); /* 1rem (16px) */ <br> line-height: var(--text-base--line-height); /* calc(1.5 / 1) */|
|text-lg|font-size: var(--text-lg); /* 1.125rem (18px) */ <br> line-height: var(--text-lg--line-height); /* calc(1.75 / 1.125) */|
|text-xl|font-size: var(--text-xl); /* 1.25rem (20px) */ <br> line-height: var(--text-xl--line-height); /* calc(1.75 / 1.25) */|
|text-2xl|font-size: var(--text-2xl); /* 1.5rem (24px) */ <br> line-height: var(--text-2xl--line-height); /* calc(2 / 1.5) */|
|text-3xl|font-size: var(--text-3xl); /* 1.875rem (30px) */ <br> line-height: var(--text-3xl--line-height); /* calc(2.25 / 1.875) */|
|text-4xl|font-size: var(--text-4xl); /* 2.25rem (36px) */ <br> line-height: var(--text-4xl--line-height); /* calc(2.5 / 2.25) */|
|text-5xl|font-size: var(--text-5xl); /* 3rem (48px) */ <br> line-height: var(--text-5xl--line-height); /* 1 */|
|text-6xl|font-size: var(--text-6xl); /* 3.75rem (60px) */ <br> line-height: var(--text-6xl--line-height); /* 1 */|
|text-7xl|font-size: var(--text-7xl); /* 4.5rem (72px) */ <br> line-height: var(--text-7xl--line-height); /* 1 */|
|text-8xl|font-size: var(--text-8xl); /* 6rem (96px) */ <br> line-height: var(--text-8xl--line-height); /* 1 */|
|text-9xl|font-size: var(--text-9xl); /* 8rem (128px) */ <br> line-height: var(--text-9xl--line-height); /* 1 */|
|`text-(length:<custom-property>)`|`font-size: var(<custom-property>);`|
|`text-[<value>]`|`font-size: <value>;`|

### Basic example
Use utilities like <code>text-sm</code> and <code>text-lg</code> to set the font size of an element:
```
<p class="text-sm ...">The quick brown fox ...</p>
<p class="text-base ...">The quick brown fox ...</p>
<p class="text-lg ...">The quick brown fox ...</p>
<p class="text-xl ...">The quick brown fox ...</p>
<p class="text-2xl ...">The quick brown fox ...</p>
```

### Setting the line-height
Use utilities like <code>text-sm/6</code> and <code>text-lg/7</code> to set the font size and line-height of an element at the same time:
```
<p class="text-sm/6 ...">So I started to walk into the water...</p>
<p class="text-sm/7 ...">So I started to walk into the water...</p>
<p class="text-sm/8 ...">So I started to walk into the water...</p>
```

### Using a custom value
Use the <code>text-[<value>]</code> syntax to set the font size based on a completely custom value:
```
<p class="text-[14px] ...">
  <!-- ... -->
</p>
```

## Ref
- [font size](https://tailwindcss.com/docs/font-size)
- [Responsive design](https://tailwindcss.com/docs/font-size#responsive-design)
