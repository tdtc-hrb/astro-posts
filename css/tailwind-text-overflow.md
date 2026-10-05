---
layout: ../../layouts/MarkdownPostLayout.astro
title: "text overflow"
description: "Utilities for controlling how the text of an element overflows."
date: 2025-04-09
author: "tdtc"
---
|Class|Styles|
|-|-|
|text-ellipsis|text-overflow: ellipsis;|
|text-clip|text-overflow: clip;|

#### truncate
```
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

### Truncating text
Use the <code>truncate</code> utility to prevent text from wrapping and truncate overflowing text with an ellipsis (…) if needed:
```
<p class="truncate">The longest word in any of the major...</p>
```

### Adding an ellipsis
Use the <code>text-ellipsis</code> utility to truncate overflowing text with an ellipsis (…) if needed:
```
<p class="overflow-hidden text-ellipsis">The longest word in any of the major...</p>
```

### Clipping text
Use the <code>text-clip</code> utility to truncate the text at the limit of the content area:
```
<p class="overflow-hidden text-clip">The longest word in any of the major...</p>
```
This is the default browser behavior.


## Ref
- [text overflow](https://tailwindcss.com/docs/text-overflow)
- [Responsive design](https://tailwindcss.com/docs/text-overflow#responsive-design)
