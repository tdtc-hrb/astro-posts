---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Responsive design"
description: "Using responsive utility variants to build adaptive user interfaces."
date: 2023-03-18
author: "tdtc"
---

|Breakpoint prefix|Minimum width|CSS|
|-|-|-|
|sm|40rem (640px)|@media (width >= 40rem) { ... }|
|md|48rem (768px)|@media (width >= 48rem) { ... }|
|lg|64rem (1024px)|@media (width >= 64rem) { ... }|
|xl|80rem (1280px)|@media (width >= 80rem) { ... }|
|2xl|96rem (1536px)|@media (width >= 96rem) { ... }|

## container
|bootstrap|Tailwind|
|-|-|
|width: 100%;|w-full|
|--bs-gutter-x: 1.5rem; <br> padding-right: calc(var(--bs-gutter-x) * .5); <br> padding-left: calc(var(--bs-gutter-x) * .5);|px-3|
|margin-right: auto; <br> margin-left: auto;|mx-auto|

### Putting it all together
|bootstrap|Tailwind|
|-|-|
|container|w-full px-3 mx-auto sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl xxl:max-w-xxl|
|container-sm|w-full px-3 mx-auto sm:max-w-sm md:max-w-md lg:max-w-lg xl:max-w-xl xxl:max-w-xxl|
|container-md|w-full px-3 mx-auto md:max-w-md lg:max-w-lg xl:max-w-xl xxl:max-w-xxl|
|container-lg|w-full px-3 mx-auto lg:max-w-lg xl:max-w-xl xxl:max-w-xxl|
|container-xl|w-full px-3 mx-auto xl:max-w-xl xxl:max-w-xxl|
|container-xxl|w-full px-3 mx-auto xxl:max-w-xxl|
|container-fluid|w-full px-3 mx-auto|

### About at container
'@container' is a [w3c standard](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_queries):
```
container-type: inline-size;
```


## Ref
- [Responsive design](https://tailwindcss.com/docs/responsive-design)
- [Tailwind container meet bootstrap ones?](https://github.com/tailwindlabs/tailwindcss/discussions/9140)
- [container - example](https://play.tailwindcss.com/L52JvxVCMF)
