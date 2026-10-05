---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ring - shadow"
description: "Rings implemented using box-shadow"
date: 2025-04-15
author: "tdtc"
---


### [focus ring](https://getbootstrap.com/docs/5.3/utilities/shadows)
> v5.3
```
.focus-ring:focus {
  outline: 0;
  box-shadow: var(--bs-focus-ring-x, 0) var(--bs-focus-ring-y, 0) var(--bs-focus-ring-blur, 0) var(--bs-focus-ring-width) var(--bs-focus-ring-color);
}
```

### ring and inset-ring - tw
|Class|Style|
|-|-|
|ring|--tw-ring-shadow: 0 0 0 1px;
|`ring-<number>`|`--tw-ring-shadow: 0 0 0 <number>px;`|
|`ring-(<custom-property>)`|`--tw-ring-shadow: 0 0 0 var(<custom-property>);`|
|`ring-[<value>]`|`--tw-ring-shadow: 0 0 0 <value>;`|
|ring-inherit|--tw-ring-color: inherit;|
|ring-current|--tw-ring-color: currentColor;|
|ring-transparent|--tw-ring-color: transparent;|
|inset-ring|--tw-inset-ring-shadow: inset 0 0 0 1px|
|`inset-ring-<number>`|`--tw-inset-ring-shadow: inset 0 0 0 <number>px|
|`inset-ring-(<custom-property>)`|`--tw-inset-ring-shadow: inset 0 0 0 var(<custom-property>);`|
|`inset-ring-[<value>]`|`--tw-inset-ring-shadow: inset 0 0 0 <value>;`
|inset-ring-inherit|--tw-inset-ring-color: inherit;|
|inset-ring-current|--tw-inset-ring-color: currentColor;|
|inset-ring-transparent|--tw-inset-ring-color: transparent;|


- [focus ring - bs](https://getbootstrap.com/docs/5.3/helpers/focus-ring)
- [box shadow - tws](https://tdtc-hrb.github.io/css-tws/posts/tailwind-box-shadow)
