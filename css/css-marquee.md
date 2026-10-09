---
layout: ../../layouts/MarkdownPostLayout.astro
title: "marquee class"
description: "替代 marquee 元素 - HTML"
date: 2026-10-09
author: "tdtc"
---
When using Tailwind v4, if you want the styles pre-generated so you can just write animate-marquee as a class, 
we need to include the keyframe within the @theme config.
## input file
site2.css:
```
@theme {
  --animate-marquee1: marquee1 15s linear infinite;
  --animate-marquee2: marquee2 15s linear infinite;
  
  @keyframes marquee1 {
        0% {
          transform: translateX(0%);
        }
        100% {
          transform: translateX(-100%);
        }
    }
    @keyframes marquee2 {
        0% {
          transform: translateX(100%);
        }
        100% {
          transform: translateX(0%);
        }
    }

}
```
### output
```
npx @tailwindcss/cli -i ./wwwroot/css/site2.css -o ./wwwroot/css/site2tw.css --optimize
```
also see [tailwind-integrated](../tailwind-integrated)

## Ref
- [Defining animation keyframes - format](https://tailwindcss.com/docs/theme#defining-animation-keyframes)
- [Default theme variable reference- multiple keys](https://tailwindcss.com/docs/theme#default-theme-variable-reference)
- [Creating a Marquee with Tailwind CSS - v4](https://jackwhiting.co.uk/posts/creating-a-marquee-with-tailwind-css-v4)
