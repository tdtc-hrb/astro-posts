---
layout: ../../layouts/MarkdownPostLayout.astro
title: "高 - min"
description: "默认为元素"
date: 2025-04-16
author: "tdtc"
---
Note:    
当 min-height 大于 max-height 或 height 时，元素的高度会设置为 min-height 的值。

## tailwind
- Fixed
- often used

### Fixed value
|Class|Styles|
|-|-|
|min-h-px|min-height: 1px;|

### Frequently used values
|Class|Styles|
|-|-|
|`min-h-<number>`|`min-height: calc(var(--spacing) * <number>);`|
|`min-h-<fraction>`|`min-height: calc(<fraction> * 100%);`|

```
<div class="min-h-10 bg-red-200">min-h-10</div>
<div class="min-h-1/3 bg-blue-300">min-h-1/3</div>
```

## Ref
- [min height - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-height)
- [min height - tw](https://tailwindcss.com/docs/min-height)
