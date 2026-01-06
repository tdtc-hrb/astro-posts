---
layout: ../../layouts/MarkdownPostLayout.astro
title: "tailwindcss outline"
description: "Outline can be of any random shape as it tries to wrap around content of the element."
date: 2025-04-15
author: "tdtc"
---
  tw中充斥了太多的outline!

- border 和 outline    
[outline 不占据空间，绘制于元素内容周围。](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline#border_%E5%92%8C_outline)

![Difference in sibling element position](https://res.cloudinary.com/dkdpf5puv/image/upload/f_auto,c_limit,w_750,q_auto/v1654257705/images/border-vs-outline/border-vs-outline-effect-on-layout.png)

![Difference in style of different sides](https://res.cloudinary.com/dkdpf5puv/image/upload/f_auto,c_limit,w_750,q_auto/v1654262774/images/border-vs-outline/Border-vs-outline-different-styles-per-side.png)


### The right posture
Outline can be of any random shape as it tries to wrap around content of the element. 

In below code playground, you can see how the outline is rendered with random shape when applied on multiline text.
- html
```
<div class="text-wrapper">
    This is test content <span class="highlight">to see how outline is shown when the content is wrapped</span> on multiple lines.
</div>
```
- css
```
.text-wrapper {
  width: 200px;
}

.highlight {
  outline: 1px solid #ff77ab;
}
```

## Ref
- [outline - mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline)
- [Border vs Outline - 5 Key Differences](https://www.codewithshripal.com/articles/css/5-key-differences-between-border-and-outline)
 -[outline-width](https://tailwindcss.com/docs/outline-width)
- [outline-color](https://tailwindcss.com/docs/outline-color)
- [outline-style](https://tailwindcss.com/docs/outline-style)
- [outline-offset](https://tailwindcss.com/docs/outline-offset)
