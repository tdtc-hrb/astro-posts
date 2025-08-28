---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text decoration line"
description: "Utilities for controlling the decoration of text."
date: 2025-03-29
author: "tdtc"
---
|Class|Styles|
|-|-|
|underline|text-decoration-line: underline;|
|overline|text-decoration-line: overline;|
|line-through|text-decoration-line: line-through;|
|no-underline|text-decoration-line: none;|

### Underling text
Use the <code>underline</code> utility to add an underline to the text of an element:
```
<p class="underline">The quick brown fox...</p>
```

### Adding an overline to text
Use the <code>overline</code> utility to add an overline to the text of an element:
```
<p class="overline">The quick brown fox...</p>
```

### Adding a line through text
Use the <code>line-through</code> utility to add a line through the text of an element:
```
<p class="line-through">The quick brown fox...</p>
```

### Removing a line from text
Use the <code>no-underline</code> utility to remove a line from the text of an element:
```
<p class="no-underline">The quick brown fox...</p>
```

### Applying on hover
Prefix a <code>text-decoration-line</code> utility with a variant like <code>hover:*</code> to 
only apply the utility in that state:
```
<p>The <a href="..." class="no-underline hover:underline ...">quick brown fox</a> jumps over the lazy dog.</p>
```

## Ref
- [text decoration line](https://tailwindcss.com/docs/text-decoration-line)
- [Responsive design](https://tailwindcss.com/docs/text-decoration-line#responsive-design)
