---
layout: ../../layouts/MarkdownPostLayout.astro
title: "宽 - custom"
description: "默认为元素"
date: 2025-04-15
author: "tdtc"
---
Note:    
max-width 会覆盖 width 的设置，但 min-width 的设置会覆盖 max-width。

## tailwind
- Fixed
- often used
- Responsive-design defined values

### Fixed value
|Class|Styles|
|-|-|
|max-w-0|max-width: 0px;|
|max-w-px|max-width: 1px;|
|max-w-none|max-width: none;|

### Frequently used values
|Class|Styles|
|-|-|
|`max-w-<number>`|`max-width: calc(var(--spacing) * <number>);`|
|`max-w-<fraction>`|`max-width: calc(<fraction> * 100%);`|

```
<div class="max-w-20 bg-red-200">max-w-20</div>
<div class="max-w-1/3 bg-blue-300">max-w-1/3</div>
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
- [max width - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-width)
- [max width - tw](https://v3.tailwindcss.com/docs/max-width)
