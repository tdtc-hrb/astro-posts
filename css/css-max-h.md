---
layout: ../../layouts/MarkdownPostLayout.astro
title: "高 - custom"
description: "默认为元素"
date: 2025-04-15
author: "tdtc"
---
Note:    
max-height 会覆盖 height，而 min-height 会覆盖 max-height。

## tailwind
- Fixed
- often used

### Fixed value
|Class|Styles|
|-|-|
|max-h-none|max-height: none;|

### Frequently used values
|Class|Styles|
|-|-|
|`max-h-<number>`|`max-height: calc(var(--spacing) * <number>);`|
|`max-h-<fraction>`|`max-height: calc(<fraction> * 100%);`|

```
<div class="max-h-10 bg-red-200">max-h-10</div>
<div class="max-h-1/3 bg-blue-300">max-h-1/3</div>
```

## Ref
- [max height - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-height)
- [max height - tw](https://tailwindcss.com/docs/max-height)
