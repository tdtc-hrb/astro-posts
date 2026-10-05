---
layout: ../../layouts/MarkdownPostLayout.astro
title: "高 - area"
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

### Fixed value
|Class|Styles|
|-|-|
|h-auto|height: auto;|
|h-px|height: 1px;|
|h-full|height: 100%;|

### Frequently used values
|Class|Styles|
|-|-|
|`h-<number>`|`height: calc(var(--spacing) * <number>);`|
|`h-[<value>]`|`height: <value>;`|

```
<div class="h-10 bg-red-200">h-10</div>
<div class="h-[30px] bg-blue-300">h-30px</div>
```

## Ref
- [CSS basic box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model)
- [height - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)
- [height - tw](https://tailwindcss.com/docs/height)
