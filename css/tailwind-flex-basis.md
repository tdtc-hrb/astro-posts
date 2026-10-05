---
layout: ../../layouts/MarkdownPostLayout.astro
title: "flex basis"
description: "Utilities for controlling the initial size of flex items."
date: 2025-03-05
author: "tdtc"
---
|Class|Styles|
|-|-|
|`basis-<number>`|`flex-basis: calc(var(--spacing) * <number>);`|
|`basis-<fraction>`|`flex-basis: calc(<fraction> * 100%);`|
|basis-full|flex-basis: 100%;|
|basis-auto|flex-basis: auto;|
|basis-3xs|flex-basis: var(--container-3xs); /* 16rem (256px) */|
|basis-2xs|flex-basis: var(--container-2xs); /* 18rem (288px) */|
|basis-xs|flex-basis: var(--container-xs); /* 20rem (320px) */|
|basis-sm|flex-basis: var(--container-sm); /* 24rem (384px) */|
|basis-md|flex-basis: var(--container-md); /* 28rem (448px) */|
|basis-lg|flex-basis: var(--container-lg); /* 32rem (512px) */|
|basis-xl|flex-basis: var(--container-xl); /* 36rem (576px) */|
|basis-2xl|flex-basis: var(--container-2xl); /* 42rem (672px) */|
|basis-3xl|flex-basis: var(--container-3xl); /* 48rem (768px) */|
|basis-4xl|flex-basis: var(--container-4xl); /* 56rem (896px) */|
|basis-5xl|flex-basis: var(--container-5xl); /* 64rem (1024px) */|
|basis-6xl|flex-basis: var(--container-6xl); /* 72rem (1152px) */|
|basis-7xl|flex-basis: var(--container-7xl); /* 80rem (1280px) */|
|`basis-(<custom-property>)`|`flex-basis: var(<custom-property>);`|
|`basis-[<value>]`|`flex-basis: <value>;`|

## flex-basis
- Using the spacing scale
- Using the container scale
- Using percentages
- Using a custom value

### Using the spacing scale
Use <code>basis-<number></code> utilities like <code>basis-64</code> and <code>basis-128</code> to set 
the initial size of flex items based on the spacing scale:
```
<div class="flex flex-row">
  <div class="basis-64">01</div>
  <div class="basis-64">02</div>
  <div class="basis-128">03</div>
</div>
```
### Using the container scale
Use utilities like <code>basis-xs</code> and <code>basis-sm</code> to set the initial size of flex items based on the container scale:
```
<div class="flex flex-row">
  <div class="basis-3xs">01</div>
  <div class="basis-2xs">02</div>
  <div class="basis-xs">03</div>
  <div class="basis-sm">04</div>
</div>
```
### Using percentages
Use <code>basis-<fraction></code> utilities like <code>basis-1/2</code> and <code>basis-2/3</code> to set the initial size of flex items:
```
<div class="flex flex-row">
  <div class="basis-1/3">01</div>
  <div class="basis-2/3">02</div>
</div>
```
### Using a custom value
Use the <code>basis-[<value>]</code> syntax to set the basis based on a completely custom value:
```
<div class="basis-[30vw] ...">
  <!-- ... -->
</div>
```

## Ref
- [flex basis](https://tailwindcss.com/docs/flex-basis)
- [Responsive design](https://tailwindcss.com/docs/flex-basis#responsive-design)
