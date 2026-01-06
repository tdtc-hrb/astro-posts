---
layout: ../../layouts/MarkdownPostLayout.astro
title: "group"
description: "btn, input, card, list"
date: 2025-04-19
author: "tdtc"
---

- Examples are from Bootstrap [v4.6.2](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
> Number of occurrences: 33-36


### first-child
```
.card > .list-group:first-child {
  border-top-width: 0;
  border-top-left-radius: calc(0.25rem - 1px);
  border-top-right-radius: calc(0.25rem - 1px);
}
```
- tw
```
*:first:border-t-1
*:first:rounded-tl-xs
*:first:rounded-tr-xs
```
### last-child
```
.card > .list-group:last-child {
  border-bottom-width: 0;
  border-bottom-right-radius: calc(0.25rem - 1px);
  border-bottom-left-radius: calc(0.25rem - 1px);
}
```
- tw
```
*:last:border-t-1
*:last:rounded-tr-xs
*:last:rounded-tl-xs
```

## Ref
- [first child - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-child)
- [last child - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-child)
- [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
