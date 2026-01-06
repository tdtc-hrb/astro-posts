---
layout: ../../layouts/MarkdownPostLayout.astro
title: "marquee class"
description: "替代 marquee 元素 - HTML"
date: 2025-03-12
author: "tdtc"
---

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
also see [tailwind-integrated](https://tdtc-hrb.github.io/css-tws/posts/tailwind-integrated/)

注意：使用v4的cli现在解析v2的配置文件(tailwind.config.js)有问题!

## CSS without frameworks
```
        .marquee {
            height: 50px;
            overflow: hidden;
            position: relative;
            background: #fefefe;
            color: #333;
            border: 1px solid #4a4a4a;
        }
        
        .marquee p {
            position: absolute;
            width: 100%;
            height: 100%;
            margin: 0;
            line-height: 50px;
            text-align: center;
            -moz-transform: translateX(100%);
            -webkit-transform: translateX(100%);
            transform: translateX(100%);
            -moz-animation: scroll-left 2s linear infinite;
            -webkit-animation: scroll-left 2s linear infinite;
            animation: scroll-left 20s linear infinite;
        }
        
        @-moz-keyframes scroll-left {
            0% {
                -moz-transform: translateX(100%);
            }
            100% {
                -moz-transform: translateX(-100%);
            }
        }
        
        @-webkit-keyframes scroll-left {
            0% {
                -webkit-transform: translateX(100%);
            }
            100% {
                -webkit-transform: translateX(-100%);
            }
        }
        
        @keyframes scroll-left {
            0% {
                -moz-transform: translateX(100%);
                -webkit-transform: translateX(100%);
                transform: translateX(100%);
            }
            100% {
                -moz-transform: translateX(-100%);
                -webkit-transform: translateX(-100%);
                transform: translateX(-100%);
            }
        }
```

## Ref
- [Defining animation keyframes - format](https://tailwindcss.com/docs/theme#defining-animation-keyframes)
- [Default theme variable reference- multiple keys](https://tailwindcss.com/docs/theme#default-theme-variable-reference)
- [Creating a Marquee with Tailwind CSS - v2](https://jackwhiting.co.uk/posts/creating-a-marquee-with-tailwind-css)
