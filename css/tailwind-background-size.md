---
layout: ../../layouts/MarkdownPostLayout.astro
title: "background size"
description: "Utilities for controlling the background size of an element's background image."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|bg-auto|background-size: auto;|
|bg-cover|background-size: cover;|
|bg-contain|background-size: contain;|
|`bg-size-(<custom-property>)`|`background-size: var(<custom-property>);`|
|`bg-size-[<value>]`|`background-size: <value>;`|

### Filling the container
Use the <code>bg-cover</code> utility to scale the background image until it fills the background layer, cropping the image if needed:
```
<div class="bg-[url(/img/mountains.jpg)] bg-cover bg-center"></div>
```

### Filling without cropping
Use the <code>bg-contain</code> utility to scale the background image to the outer edges without cropping or stretching:
```
<div class="bg-[url(/img/mountains.jpg)] bg-contain bg-center"></div>
```

### Using the default size
Use the <code>bg-auto</code> utility to display the background image at its default size:
```
<div class="bg-[url(/img/mountains.jpg)] bg-auto bg-center bg-no-repeat"></div>
```

### Using a custom value
Use the <code>bg-size-[<value>]</code> syntax to set the background size based on a completely custom value:
```
<div class="bg-size-[auto_100px] ...">
  <!-- ... -->
</div>
```

## Ref
- [background-size](https://tailwindcss.com/docs/background-size)
- [Responsive design](https://tailwindcss.com/docs/background-size#responsive-design)
