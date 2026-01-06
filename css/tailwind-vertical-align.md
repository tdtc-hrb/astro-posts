---
layout: ../../layouts/MarkdownPostLayout.astro
title: "vertical align"
description: "Utilities for controlling the vertical alignment of an inline or table-cell box."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|align-baseline|vertical-align: baseline;|
|align-top|vertical-align: top;|
|align-middle|vertical-align: middle;|
|align-bottom|vertical-align: bottom;|
|align-text-top|vertical-align: text-top;|
|align-text-bottom|vertical-align: text-bottom;|
|align-sub|vertical-align: sub;|
|align-super|vertical-align: super;|
|`align-(<custom-property>)`|`vertical-align: var(<custom-property>);`|
|`align-[<value>]`|`vertical-align: <value>;`|

### Aligning to baseline
Use the <code>align-baseline</code> utility to align the baseline of an element with the baseline of its parent:
```
<span class="inline-block align-baseline">The quick brown fox...</span>
```

### Aligning to top
Use the <code>align-top</code> utility to align the top of an element and its descendants with the top of the entire line:
```
<span class="inline-block align-top">The quick brown fox...</span>
```

### Aligning to middle
Use the <code>align-middle</code> utility to align the middle of 
an element with the baseline plus half the x-height of the parent:
```
<span class="inline-block align-middle">The quick brown fox...</span>
```

### Aligning to bottom
Use the <code>align-bottom</code> utility to align the bottom of 
an element and its descendants with the bottom of the entire line:
```
<span class="inline-block align-bottom">The quick brown fox...</span>
```

### Aligning to parent top
Use the <code>align-text-top</code> utility to align the top of 
an element with the top of the parent element's font:
```
<span class="inline-block align-text-top">The quick brown fox...</span>
```

### Aligning to parent bottom
Use the <code>align-text-bottom</code> utility to align the bottom of 
an element with the bottom of the parent element's font:
```
<span class="inline-block align-text-bottom">The quick brown fox...</span>
```

### Using a custom value
Use the <code>align-[<value>]</code> syntax to set the vertical alignment based on a completely custom value:
```
<span class="align-[4px] ...">
  <!-- ... -->
</span>
```

## Ref
- [vertical align](https://tailwindcss.com/docs/vertical-align)
- [Responsive design](https://tailwindcss.com/docs/vertical-align#responsive-design)
- [Upgrading from v0.x to v1.0](https://v1.tailwindcss.com/docs/upgrading-to-v1)
