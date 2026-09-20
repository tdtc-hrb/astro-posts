---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text transform"
description: "Utilities for controlling the capitalization of text."
date: 2025-04-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|uppercase|text-transform: uppercase;|
|lowercase|text-transform: lowercase;|
|capitalize|text-transform: capitalize;|
|normal-case|text-transform: none;|


### Uppercasing text
Use the <code>uppercase</code> utility to uppercase the text of an element:
```
<p class="uppercase">The quick brown fox ...</p>
```

### Lowercasing text
Use the <code>lowercase</code> utility to lowercase the text of an element:
```
<p class="lowercase">The quick brown fox ...</p>
```

### Capitalizing text
Use the <code>capitalize</code> utility to capitalize text of an element:
```
<p class="capitalize">The quick brown fox ...</p>
```

### Resetting text casing
Use the <code>normal-case</code> utility to preserve the original 
text casing of an element—typically used to reset capitalization at different breakpoints:
```
<p class="normal-case">The quick brown fox ...</p>
```

## Ref
- [text transform](https://tailwindcss.com/docs/text-transform)
- [Responsive design](https://tailwindcss.com/docs/text-transform#responsive-design)
