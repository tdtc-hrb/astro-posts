---
layout: ../../layouts/MarkdownPostLayout.astro
title: "grid template columns"
description: "Utilities for specifying the columns in a grid layout."
date: 2025-03-29
author: "tdtc"
---

|Class|Styles|
|-|-|
|`grid-cols-<number>`|`grid-template-columns: repeat(<number>, minmax(0, 1fr));`|
|grid-cols-none|grid-template-columns: none;|
|grid-cols-subgrid|grid-template-columns: subgrid;|
|`grid-cols-[<value>]`|`grid-template-columns: <value>;`|
|`grid-cols-(<custom-property>)`|`grid-template-columns: var(<custom-property>);`|


### Specifying the grid columns
Use <code>grid-cols-<number></code> utilities like <code>grid-cols-2</code> 
and <code>grid-cols-4</code> to create grids with n equally sized columns:
```
<div class="grid grid-cols-4 gap-4">
  <div>01</div>
  <!-- ... -->
  <div>09</div>
</div>
```

### Implementing a subgrid
Use the <code>grid-cols-subgrid</code> utility to adopt the column tracks defined by the item's parent:
```
<div class="grid grid-cols-4 gap-4">
  <div>01</div>
  <!-- ... -->
  <div>05</div>
  <div class="col-span-3 grid grid-cols-subgrid gap-4">
    <div class="col-start-2">06</div>
  </div>
</div>
```

### Using a custom value
Use the <code>grid-cols-[<value>]</code> syntax to set the columns based on a completely custom value:
```
<div class="grid-cols-[200px_minmax(900px,_1fr)_100px] ...">
  <!-- ... -->
</div>
```

## Ref
- [grid template columns](https://tailwindcss.com/docs/grid-template-columns)
- [Responsive design](https://tailwindcss.com/docs/grid-template-columns#responsive-design)
