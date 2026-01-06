---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text color"
description: "Utilities for controlling the text color of an element."
date: 2025-03-28
author: "tdtc"
---
|Class|Styles|
|-|-|
|text-inherit|color: inherit;|
|text-current|color: currentColor;|
|text-transparent|color: transparent;|
|text-black|color: var(--color-black); /* #000 */|
|text-white|color: var(--color-white); /* #fff */|
|`text-(<custom-property>)`|`color: var(<custom-property>);`|
|`text-[<value>]`|`color: <value>;`|

#### intensity
see [colors](https://tdtc-hrb.github.io/css-tws/posts/tailwind-colors)

### Basic example
Use utilities like <code>text-blue-600</code> and <code>text-sky-400</code> to control the text color of an element:
```
<p class="text-blue-600 dark:text-sky-400">The quick brown fox...</p>
```

### Changing the opacity
Use the color opacity modifier to control the text color opacity of an element:
```
<p class="text-blue-600/100 dark:text-sky-400/100">The quick brown fox...</p>
<p class="text-blue-600/75 dark:text-sky-400/75">The quick brown fox...</p>
<p class="text-blue-600/50 dark:text-sky-400/50">The quick brown fox...</p>
<p class="text-blue-600/25 dark:text-sky-400/25">The quick brown fox...</p>
```

### Using a custom value
Use the <code>text-[<value>]</code> syntax to set the text color based on a completely custom value:
```
<p class="text-[#50d71e] ...">
  <!-- ... -->
</p>
```

## Ref
- [text color](https://tailwindcss.com/docs/color)
- [Responsive design](https://tailwindcss.com/docs/color#responsive-design)
