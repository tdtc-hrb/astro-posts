---
layout: ../../layouts/MarkdownPostLayout.astro
title: "appearance"
description: "Utilities for suppressing native form control styling."
date: 2025-04-10
author: "tdtc"
---

|Class|Styles|
|-|-|
|appearance-none|appearance: none;|
|appearance-auto|appearance: auto;|

### Removing default appearance
Use <code>appearance-none</code> to reset any browser specific styling on an element:
```
<select>
  <option>Yes</option>
  <option>No</option>
  <option>Maybe</option>
</select>
<div class="grid">
  <select class="col-start-1 row-start-1 appearance-none bg-gray-50 dark:bg-gray-800 ...">
    <option>Yes</option>
    <option>No</option>
    <option>Maybe</option>
  </select>
  <svg class="pointer-events-none col-start-1 row-start-1 ...">
    <!-- ... -->
  </svg>
</div>
```

### Restoring default appearance
Use <code>appearance-auto</code> to restore the default browser specific styling on an element:
```
<label>
  <div>
    <input type="checkbox" class="appearance-none forced-colors:appearance-auto ..." />
    <svg class="invisible peer-checked:visible forced-colors:hidden ...">
      <!-- ... -->
    </svg>
  </div>
  Falls back to default appearance
</label>
<label>
  <div>
    <input type="checkbox" class="appearance-none ..." />
    <svg class="invisible peer-checked:visible ...">
      <!-- ... -->
    </svg>
  </div>
  Keeps custom appearance
</label>
```
This is useful for reverting to the standard browser controls in certain accessibility modes.


## Ref
- [appearance](https://tailwindcss.com/docs/appearance)
- [Responsive design](https://tailwindcss.com/docs/appearance#responsive-design)
