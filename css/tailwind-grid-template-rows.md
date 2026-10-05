---
layout: ../../layouts/MarkdownPostLayout.astro
title: "grid template rows"
description: "Utilities for specifying the rows in a grid layout."
date: 2025-03-29
author: "tdtc"
---

|Class|Styles|
|-|-|
|`grid-rows-<number>`|`grid-template-rows: repeat(<number>, minmax(0, 1fr));`|
|grid-rows-none|grid-template-rows: none;|
|grid-rows-subgrid|grid-template-rows: subgrid;|
|`grid-rows-[<value>]`|`grid-template-rows: <value>;`|
|`grid-rows-(<custom-property>)`|`grid-template-rows: var(<custom-property>);`|


### Specifying the grid rows
Use <code>grid-rows-<number></code> utilities like <code>grid-rows-2</code> 
and <code>grid-rows-4</code> to create grids with n equally sized rows:
```
<div class="grid grid-flow-col grid-rows-4 gap-4">
  <div>01</div>
  <!-- ... -->
  <div>09</div>
</div>
```

### Implementing a subgrid
Use the <code>grid-rows-subgrid</code> utility to adopt the row tracks defined by the item's parent:
```
<div class="grid grid-flow-col grid-rows-4 gap-4">
  <div>01</div>
  <!-- ... -->
  <div>05</div>
  <div class="row-span-3 grid grid-rows-subgrid gap-4">
    <div class="row-start-2">06</div>
  </div>
  <div>07</div>
  <!-- ... -->
  <div>10</div>
</div>
```

### Using a custom value
Use the <code>grid-rows-[<value>]</code> syntax to set the rows based on a completely custom value:
```
<div class="grid-rows-[200px_minmax(900px,1fr)_100px] ...">
  <!-- ... -->
</div>
```

## Ref
- [grid template rows](https://tailwindcss.com/docs/grid-template-rows)
- [Responsive design](https://tailwindcss.com/docs/grid-template-rows#responsive-design)
