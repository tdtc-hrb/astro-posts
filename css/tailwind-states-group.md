---
layout: ../../layouts/MarkdownPostLayout.astro
title: "group 状态"
description: "Using tailwind css for hover and focus on group"
date: 2025-03-13
author: "tdtc"
---

When you need to style an element based on the state of some parent element, 
mark the parent with the <cod>group</code> class, and use <code>group-*</code> variants 
like <code>group-hover</code> to style the target element:

Hover over the card to see both text elements change color
```
<a href="#" class="group ...">
  <div>
    <svg class="stroke-sky-500 group-hover:stroke-white ..." fill="none" viewBox="0 0 24 24">
      <!-- ... -->
    </svg>
    <h3 class="text-gray-900 group-hover:text-white ...">New project</h3>
  </div>
  <p class="text-gray-500 group-hover:text-white ...">Create a new project from a variety of starting templates.</p>
</a>
```
This pattern works with every pseudo-class variant, 
for example <code>group-focus</code>, <code>group-active</code>, or even <code>group-odd</code>.

### Differentiating nested groups
When nesting groups, you can style something based on the state of a specific parent group 
by giving that parent a unique group name using a <code>group/{name}</code> class, 
and including that name in variants using classes like <code>group-hover/{name}</code>:
```
<ul role="list">
  {#each people as person}
    <li class="group/item ...">
      <!-- ... -->
      <a class="group/edit invisible group-hover/item:visible ..." href="tel:{person.phone}">
        <span class="group-hover/edit:text-gray-700 ...">Call</span>
        <svg class="group-hover/edit:translate-x-0.5 group-hover/edit:text-gray-500 ..."><!-- ... --></svg>
      </a>
    </li>
  {/each}
</ul>
```
Groups can be named however you like and don’t need to be configured in any way — just name your groups 
directly in your markup and Tailwind will automatically generate the necessary CSS.

### Arbitrary groups
You can create one-off <code>group-*</code> variants on the fly by providing your own 
selector as an [arbitrary value](https://tailwindcss.com/docs/adding-custom-styles#using-arbitrary-values) between square brackets:
```
<div class="group is-published">
  <div class="hidden group-[.is-published]:block">
    Published
  </div>
</div>
```
For more control, you can use the <code>&</code> character to mark where <code>.group</code> should end 
up in the final selector relative to the selector you are passing in:
```
<div class="group">
  <div class="group-[:nth-of-type(3)_&]:block">
    <!-- ... -->
  </div>
</div>
```

### Implicit groups
The <code>in-*</code> variant works similarly to <code>group</code> except you don't need to add <code>group</code> to the parent element:
- orig
```
<div tabindex="0" class="group">
  <div class="opacity-50 group-focus:opacity-100">
    <!-- ... -->
  </div>
</div>
```
- now
```
<div tabindex="0">
  <div class="opacity-50 in-focus:opacity-100">
    <!-- ... -->
  </div>
</div>
```
The <code>in-*</code> variant responds to state changes in any parent, 
so if you want more fine-grained control you'll need to use <code>group</code> instead.


## Ref
- [Styling based on parent state](https://tailwindcss.com/docs/hover-focus-and-other-states#styling-based-on-parent-state)
