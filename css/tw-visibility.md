---
layout: ../../layouts/MarkdownPostLayout.astro
title: "visibility"
description: "Utilities for controlling the visibility of an element."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|visible|visibility: visible;|
|invisible|visibility: hidden;|
|collapse|visibility: collapse;|

### Making elements invisible
Use the <code>invisible</code> utility to hide an element, 
but still maintain its place in the document, affecting the layout of other elements:
```
<div class="grid grid-cols-3 gap-4">
  <div>01</div>
  <div class="invisible ...">02</div>
  <div>03</div>
</div>
```

### Collapsing elements
Use the <code>collapse</code> utility to hide table rows, row groups, columns, 
and column groups as if they were set to <code>display: none</code>, but without impacting the size of other rows and columns:
```
<table>
  <thead>
    <tr>
      <th>Invoice #</th>
      <th>Client</th>
      <th>Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>#100</td>
      <td>Pendant Publishing</td>
      <td>$2,000.00</td>
    </tr>
    <tr class="collapse">
      <td>#101</td>
      <td>Kruger Industrial Smoothing</td>
      <td>$545.00</td>
    </tr>
    <tr>
      <td>#102</td>
      <td>J. Peterman</td>
      <td>$10,000.25</td>
    </tr>
  </tbody>
</table>
```
This makes it possible to dynamically toggle rows and columns without affecting the table layout.

### Making elements visible
Use the <code>visible</code> utility to make an element visible:
```
<div class="grid grid-cols-3 gap-4">
  <div>01</div>
  <div class="visible ...">02</div>
  <div>03</div>
</div>
```
This is mostly useful for undoing the <code>invisible</code> utility at different screen sizes.


## Ref
- [visibility](https://tailwindcss.com/docs/visibility)
- [Responsive design](https://tailwindcss.com/docs/visibility#responsive-design)
