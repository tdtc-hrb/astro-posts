---
layout: ../../layouts/MarkdownPostLayout.astro
title: "viewport"
description: "To recap, the viewport is basically the part of the document that is currently visible."
date: 2025-04-16
author: "tdtc"
---
- top
```
Document
Layout Viewport
Visual Viewport
```

## tailwind
- dv
```
dynamic viewport
```
- lv
```
large viewport
```
- sv
```
small viewport
```

### width
|Class|Style|
|-|-|
|w-dvw|width: 100dvw;|
|w-dvh|width: 100dvh;|
|w-lvw|width: 100lvw;|
|w-lvh|width: 100lvh;|
|w-svw|width: 100svw;|
|w-svh|width: 100svh;|

- often used

|Class|Style|
|-|-|
|w-screen|width: 100vw;|

#### width - max
|Class|Style|
|-|-|
|max-w-dvw|max-width: 100dvw;|
|max-w-dvh|max-width: 100dvh;|
|max-w-lvw|max-width: 100lvw;|
|max-w-lvh|max-width: 100lvh;|
|max-w-svw|max-width: 100svw;|
|max-w-svh|max-width: 100svh;|

- often used

|Class|Style|
|-|-|
|max-w-screen|max-width: 100vw;

#### width - min
|Class|Style|
|-|-|
|min-w-dvw|min-width: 100dvw;|
|min-w-dvh|min-width: 100dvh;|
|min-w-lvw|min-width: 100lvw;|
|min-w-lvh|min-width: 100lvh;|
|min-w-svw|min-width: 100svw;|
|min-w-svh|min-width: 100svh;|

- often used

|Class|Style|
|-|-|
|min-w-screen|min-width: 100vw;|


### height
|Class|Style|
|-|-|
|h-dvh|height: 100dvh;|
|h-dvw|height: 100dvw;|
|h-lvh|height: 100lvh;|
|h-lvw|height: 100lvw;|
|h-svh|height: 100svh;|
|h-svw|height: 100svw;|

- often used

|Class|Style|
|-|-|
|h-screen|height: 100vh;|

#### height - max
|Class|Style|
|-|-|
|max-h-dvh|max-height: 100dvh;|
|max-h-dvw|max-height: 100dvw;|
|max-h-lvh|max-height: 100lvh;|
|max-h-lvw|max-height: 100lvw;|
|max-h-svh|max-height: 100svh;|
|max-h-svw|max-height: 100svw;|

- often used

|Class|Style|
|-|-|
|max-h-screen|max-height: 100vh;|

#### height - min
|Class|Style|
|-|-|
|min-h-dvh|min-height: 100dvh;|
|min-h-dvw|min-height: 100dvw;|
|min-h-lvh|min-height: 100lvh;|
|min-h-lvw|min-height: 100lvw;|
|min-h-svw|min-height: 100svw;|
|min-h-svh|min-height: 100svh;|

- often used

|Class|Style|
|-|-|
|min-h-screen|min-height: 100vh;|


## Ref
- [CSSOM View Module](https://drafts.csswg.org/cssom-view/)
- [viewport - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/CSSOM_view/Viewport_concepts)
- [Matching dynamic viewport](https://tailwindcss.com/docs/height#matching-dynamic-viewport)
- [Matching large viewport](https://tailwindcss.com/docs/height#matching-large-viewport)
- [Matching small viewport](https://tailwindcss.com/docs/height#matching-small-viewport)
