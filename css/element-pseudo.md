---
layout: ../../layouts/MarkdownPostLayout.astro
title: "胶水 元素"
description: "before, after"
date: 2025-04-12
author: "tdtc"
---

zh-CN: 胶水 元素 可以 使用在 元素 上，也可以使用在 类（以及状态类）

en-US: Glue(or Adhesive) elements can be used on elements or on classes (including state classes).

- [无障碍考虑](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::before#%E6%97%A0%E9%9A%9C%E7%A2%8D%E8%80%83%E8%99%91):    
不鼓励使用 胶水 元素 添加内容，因为屏幕阅读器无法可靠地访问它。

- Examples are from Bootstrap [v4.6.2](https://getbootstrap.com/docs/4.6/getting-started/introduction/)


### before
- breadcrumb
```
.breadcrumb-item + .breadcrumb-item::before {
  float: left;
  padding-right: 0.5rem;
  color: #6c757d;
  content: "/";
}
```

### after
```
.dropdown-toggle::after {
  display: inline-block;
  margin-left: 0.255em;
  vertical-align: 0.255em;
  content: "";
  border-top: 0.3em solid;
  border-right: 0.3em solid transparent;
  border-bottom: 0;
  border-left: 0.3em solid transparent;
}
```


## Ref
- [before](https://developer.mozilla.org/en-US/docs/Web/CSS/::before)
- [after](https://developer.mozilla.org/en-US/docs/Web/CSS/::after)
- [Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
