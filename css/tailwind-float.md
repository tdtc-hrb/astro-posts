---
layout: ../../layouts/MarkdownPostLayout.astro
title: "float"
description: "Utilities for controlling the wrapping of content around an element."
date: 2025-04-05
author: "tdtc"
---
|Class|Styles|
|-|-|
|float-right|float: right;|
|float-left|float: left;|
|float-start|float: inline-start;|
|float-end|float: inline-end;|
|float-none|float: none;|

### Floating elements to the right
Use the <code>float-right</code> utility to float an element to the right of its container:
```
<article>
  <img class="float-right ..." src="/img/mountains.jpg" />
  <p>Maybe we can live without libraries, people like you and me. ...</p>
</article>
```

### Floating elements to the left
Use the <code>float-left</code> utility to float an element to the left of its container:
```
<article>
  <img class="float-left ..." src="/img/mountains.jpg" />
  <p>Maybe we can live without libraries, people like you and me. ...</p>
</article>
```

### Using logical properties
Use the <code>float-start</code> and <code>float-end</code> utilities, 
which use [logical properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties/Basic_concepts) to map to either the left or right side based on the text direction:
```
<article>
  <img class="float-start ..." src="/img/mountains.jpg" />
  <p>Maybe we can live without libraries, people like you and me. ...</p>
</article>
<article dir="rtl">
  <img class="float-start ..." src="/img/mountains.jpg" />
  <p>... ربما يمكننا العيش بدون مكتبات، أشخاص مثلي ومثلك. ربما. بالتأكيد</p>
</article>
```

### Disabling a float
Use the <code>float-none</code> utility to reset any floats that are applied to an element:
```
<article>
  <img class="float-none ..." src="/img/mountains.jpg" />
  <p>Maybe we can live without libraries, people like you and me. ...</p>
</article>
```


## Ref
- [float](https://tailwindcss.com/docs/float)
- [Responsive design](https://tailwindcss.com/docs/float#responsive-design)
