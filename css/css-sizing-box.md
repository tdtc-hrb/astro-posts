---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Content and Border - 开关"
description: "content-box 是默认值"
date: 2025-04-11
author: "tdtc"
---
![css edge](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model/boxmodel.png)

对 w and h 计算方式的选择:
- content-box
```
只计算元素
```
- border-box
```
包含border and padding
```

### Content box
- w
```
width = width of the content
```
- h
```
height = height of the content
```

### Border box
- w
```
width = border + padding + width of the content
```
- h
```
height = border + padding + height of the content
```

## Ref
- [CSS basic box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model)
- [box sizing - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing)
- [box sizing - tw](https://tailwindcss.com/docs/box-sizing)
