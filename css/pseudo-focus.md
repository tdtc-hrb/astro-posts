---
layout: ../../layouts/MarkdownPostLayout.astro
title: "聚焦"
description: "It is generally triggered when the user clicks or taps on an element or selects it with the keyboard's Tab key."
date: 2025-04-18
author: "tdtc"
---

- Examples are from Bootstrap [v4.6.2](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
> Frequent use: second;
> Number of occurrences: 175

### pagination
```
.page-link:focus {
  z-index: 3;
  outline: 0;
  box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
}
```
- tw
```
focus:z-3 focus:outline-0 focus:shadow-[0_0px_0px_4px_rgba(0,123,255,0.25)]
```

### focus-visible
```
button:focus:not(:focus-visible) {
  outline: 0;
}
```


## Ref
- [focus](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus)
- [focus-visible](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible)
- [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
