---
layout: ../../layouts/MarkdownPostLayout.astro
title: "white space"
description: "Utilities for controlling an element's white-space property."
date: 2025-04-04
author: "tdtc"
---
|Class|Styles|
|-|-|
|whitespace-normal|white-space: normal;|
|whitespace-nowrap|white-space: nowrap;|
|whitespace-pre|white-space: pre;|
|whitespace-pre-line|white-space: pre-line;|
|whitespace-pre-wrap|white-space: pre-wrap;|
|whitespace-break-spaces|white-space: break-spaces;|

### Normal
Use the <code>whitespace-normal</code> utility to cause text to wrap normally within an element. 
Newlines and spaces will be collapsed:
```
<p class="whitespace-normal">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

### No Wrap
Use the <code>whitespace-nowrap</code> utility to prevent text from wrapping within an element. 
Newlines and spaces will be collapsed:
```
<p class="overflow-auto whitespace-nowrap">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

### Pre
Use the <code>whitespace-pre</code> utility to preserve newlines and spaces within an element. 
Text will not be wrapped:
```
<p class="overflow-auto whitespace-pre">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

### Pre Line
Use the <code>whitespace-pre-line</code> utility to preserve newlines but not spaces within an element. 
Text will be wrapped normally:
```
<p class="whitespace-pre-line">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

### Pre Wrap
Use the <code>whitespace-pre-wrap</code> utility to preserve newlines and spaces within an element. 
Text will be wrapped normally:
```
<p class="whitespace-pre-wrap">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

### Break Spaces
Use the <code>whitespace-break-spaces</code> utility to preserve newlines and spaces within an element. 
White space at the end of lines will not hang, but will wrap to the next line:
```
<p class="whitespace-break-spaces">Hey everyone!
It's almost 2022       and we still don't know if there             are aliens living among us, or do we? Maybe the person writing this is an alien.
You will never know.</p>
```

## Ref
- [white space](https://tailwindcss.com/docs/white-space)
- [Responsive design](https://tailwindcss.com/docs/white-space#responsive-design)
