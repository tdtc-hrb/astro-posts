---
layout: ../../layouts/MarkdownPostLayout.astro
title: "An+Bth"
description: "nth-child, nth-of-type"
date: 2025-06-05
author: "tdtc"
---

[nth-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child) selects its items from any group of elements.    
[nth-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-of-type) selects its items from a specified type of element.
![](https://codesweetly.com/_astro/nth-child-vs-nth-of-type-in-css-codesweetly.Dm6tWhHi_1nwhvj.webp)

- :nth-child() selects items from a general group of elements.    
For instance, selecting a <p> node from a mixed group that includes <h1>, <div>, and <section>.
- :nth-of-type() selects items from a specified group of elements.    
For instance, selecting a <p> node from a group of <p> siblings.

#### [nth - An+Bth](https://drafts.csswg.org/selectors/#the-nth-child-pseudo)
```
The :nth-child(An+B [of S]? ) pseudo-class notation represents elements that are 
among An+Bth elements from the list composed of their inclusive siblings that match the selector list S, 
which is a <complex-real-selector-list>. If S is omitted, it defaults to *|*.
```

### [child vs type](https://codesweetly.com/css-nth-of-type-selector/try-it-sdk-js-txtema)
- style
```
p:nth-child(3) {
  background:blue;
}
p:nth-of-type(3) {
  color: DeepPink;
}
```
- html
```
<h1>First heading 1 element</h1>
<p>First paragraph element</p>
<p>Second paragraph element</p>
<h2>First heading 2 element</h2>
<p>Third paragraph element</p>
<h3>First heading 3 element</h3>
<p>Fourth paragraph element</p>
<p>Fifth paragraph element</p>
```

## Ref
- [nth-child() vs nth-of-type()](https://codesweetly.com/css-nth-of-type-selector)
