---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Dark mode"
description: "Using variants to style your site in dark mode."
date: 2025-03-06
author: "tdtc"
---

所有以
```
dark:
```
开头都是Dark模式

```
<div class="bg-white dark:bg-gray-800 rounded-lg px-6 py-8 ring shadow-xl ring-gray-900/5">
  <div>
    <span class="inline-flex items-center justify-center rounded-md bg-indigo-500 p-2 shadow-lg">
      <svg class="h-6 w-6 stroke-white" ...>
        <!-- ... -->
      </svg>
    </span>
  </div>
  <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight ">Writes upside-down</h3>
  <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm ">
    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.
  </p>
</div>
```

## Ref
- [Dark mode](https://tailwindcss.com/docs/dark-mode)
