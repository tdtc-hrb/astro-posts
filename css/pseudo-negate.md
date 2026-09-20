---
layout: ../../layouts/MarkdownPostLayout.astro
title: "除此之外"
description: "Usually works together with other state classes;"
date: 2025-04-12
author: "tdtc"
---

zh-CN: 绝大部分配合其他的状态类

en-US: "not" usually works with other status classes;

- Examples are from Bootstrap [v4.6.2](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
> Frequent use: first;
> Number of occurrences: 210

### card
```
  .card-group > .card:not(:last-child) {
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
  }
```

## Ref
- [not - pseudo classes](https://www.w3schools.com/cssref/sel_not.php)
- [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
