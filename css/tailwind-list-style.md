---
layout: ../../layouts/MarkdownPostLayout.astro
title: "list-style-type"
description: "Utilities for controlling the marker style of a list."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|list-disc|list-style-type: disc;|
|list-decimal|list-style-type: decimal;|
|list-none|list-style-type: none;|
|`list-(<custom-property>)`|`list-style-type: var(<custom-property>);`|
|`list-[<value>]`|`list-style-type: <value>;`|
|`list-(<custom-property>)`|`list-style-type: var(<custom-property>);`|
|`list-[<value>]`|`list-style-type: <value>;`|

#### [list-reset](https://v1.tailwindcss.com/docs/upgrading-to-v1#8-remove-any-usage-of-list-reset)
Please use "none" to replace:
```
list-none
```

### Basic example
Use utilities like <code>list-disc</code> and <code>list-decimal</code> to control the style of the markers in a list:
```
<ul class="list-disc">
  <li>Now this is a story all about how, my life got flipped-turned upside down</li>
  <!-- ... -->
</ul>
<ol class="list-decimal">
  <li>Now this is a story all about how, my life got flipped-turned upside down</li>
  <!-- ... -->
</ol>
<ul class="list-none">
  <li>Now this is a story all about how, my life got flipped-turned upside down</li>
  <!-- ... -->
</ul>
```

### Using a custom value
Use the <code>list-[<value>]</code> syntax to set the marker based on a completely custom value:
```
<ol class="list-[upper-roman] ...">
  <!-- ... -->
</ol>
```

## Ref
- [style of a list](https://tailwindcss.com/docs/list-style-type)
- [Responsive design](https://tailwindcss.com/docs/list-style-type#responsive-design)
