---
layout: ../../layouts/MarkdownPostLayout.astro
title: "空的子元素或content"
description: "Comments, processing instructions, and CSS content do not affect whether an element is considered empty."
date: 2025-04-12
author: "tdtc"
---


### [w3schools Example](https://www.w3schools.com/cssref/tryit.php?filename=trycss_sel_empty)
```
<style>
.box {
  background-color: lightgreen;
  height: 90px;
  width: 90px;
}

.box:empty {
  background-color: red;
}
</style>


<h1>Demo of :empty</h1>

<div class="box"></div><br>
<div class="box">I will be lightgreen.</div><br>
<div class="box"><!-- I will be salmon --></div><br>
<div class="box"> <!-- I will be lightgreen --> </div>
```

## Ref
- [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
