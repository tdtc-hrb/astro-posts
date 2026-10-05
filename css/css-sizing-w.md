---
layout: ../../layouts/MarkdownPostLayout.astro
title: "宽 - area"
description: "默认为元素"
date: 2025-04-11
author: "tdtc"
---
![css edge](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model/boxmodel.png)

- default
```
<Content>
```
- custom
```
Border
```

## tailwind
- Fixed
- often used
- Responsive-design defined values

### Fixed value
|Class|Styles|
|-|-|
|w-auto|width: auto;|
|w-px|width: 1px;|
|w-full|width: 100%;|

### Frequently used values
|Class|Styles|
|-|-|
|`w-<number>`|`width: calc(var(--spacing) * <number>);`|
|`w-[<value>]`|`width: <value>;`|

```
<div class="w-10 bg-red-200">w-10</div>
<div class="w-[60px] bg-blue-300">w-60px</div>
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
- [CSS basic box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model)
- [width - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)
- [width - tw](https://tailwindcss.com/docs/width)
