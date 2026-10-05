---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text decoration thickness"
description: "Utilities for controlling the thickness of text decorations."
date: 2025-04-12
author: "tdtc"
---

|Class|Styles|
|-|-|
|`decoration-<number>`|`text-decoration-thickness: <number>px;`|
|decoration-from-font|text-decoration-thickness: from-font;|
|decoration-auto|text-decoration-thickness: auto;|
|`decoration-(<custom-property>)`|`text-decoration-thickness: var(<custom-property>);`|
|`decoration-[<value>]`|`text-decoration-thickness: <value>;`|


### Basic example
Use <code>decoration-<number></code> utilities like <code>decoration-2</code> 
and <code>decoration-4</code> to change the text decoration thickness of an element:
```
<p class="underline decoration-1">The quick brown fox...</p>
<p class="underline decoration-2">The quick brown fox...</p>
<p class="underline decoration-4">The quick brown fox...</p>
```

### Using a custom value
Use the <code>decoration-[<value>]</code> syntax to set the text decoration thickness based on a completely custom value:
```
<p class="decoration-[0.25rem] ...">
  Lorem ipsum dolor sit amet...
</p>
```


## Ref
- [text decoration thickness](https://tailwindcss.com/docs/text-decoration-thickness)
- [Responsive design](https://tailwindcss.com/docs/text-decoration-thickness#responsive-design)
