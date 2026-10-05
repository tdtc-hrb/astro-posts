---
layout: ../../layouts/MarkdownPostLayout.astro
title: "宽 - min"
description: "默认为元素"
date: 2025-04-16
author: "tdtc"
---
Note:    
当 min-width 大于 max-width 或 width 时，元素的宽度将被设置为 min-width 的值。

## tailwind
- Fixed
- often used
- Responsive-design defined values

### Fixed value
|Class|Styles|
|-|-|
|min-w-px|min-width: 1px;|

### Frequently used values
|Class|Styles|
|-|-|
|`min-w-<number>`|`min-width: calc(var(--spacing) * <number>);`|
|`min-w-<fraction>`|`min-width: calc(<fraction> * 100%);`|

```
<div class="min-w-20 bg-red-200">min-w-20</div>
<div class="min-w-1/3 bg-blue-300">min-w-1/3</div>
```

### Responsive-design defined values
```
3xs, 2xs, xs, sm, md, lg
```
- xl
```
xl, 2xl, 3xl, 4xl, 5xl, 6xl, 7xl
```

## Ref
- [min width - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-width)
- [min width - tw](https://v3.tailwindcss.com/docs/max-width)
