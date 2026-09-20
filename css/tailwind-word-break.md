---
layout: ../../layouts/MarkdownPostLayout.astro
title: "word break"
description: "Utilities for controlling word breaks in an element."
date: 2025-04-09
author: "tdtc"
---

|Class|Styles|
|-|-|
|break-normal|word-break: normal;|
|break-all|word-break: break-all;|
|break-keep|word-break: keep-all;|


### Normal
Use the <code>break-normal</code> utility to only add line breaks at normal word break points:
```
<p class="break-normal">The longest word in any of the major...</p>
```

### Break All
Use the <code>break-all</code> utility to add line breaks whenever necessary, without trying to preserve whole words:
```
<p class="break-all">The longest word in any of the major...</p>
```

### Break Keep
Use the <code>break-keep</code> utility to prevent line breaks from being applied to Chinese/Japanese/Korean (CJK) text:
```
<p class="break-keep">抗衡不屈不挠...</p>
```
For non-CJK text the <code>break-keep</code> utility has the same behavior as the <code>break-normal</code> utility.

## Ref
- [word break](https://tailwindcss.com/docs/word-break)
- [Responsive design](https://tailwindcss.com/docs/word-break#responsive-design)
