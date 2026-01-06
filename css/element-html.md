---
layout: ../../layouts/MarkdownPostLayout.astro
title: "已弃用 - html"
description: "This feature is no longer recommended."
date: 2025-03-12
author: "tdtc"
---
Deprecated: This feature is no longer recommended. 
Though some browsers might still support it, 
it may have already been removed from the relevant web standards, 
may be in the process of being dropped, or may only be kept for compatibility purposes. 
Avoid using it, and update existing code if possible; 
see the compatibility table at the bottom of this page to guide your decision. 
Be aware that this feature may cease to work at any time.

- Frequently used elements
- Frame and other
- Object related elements

## Frequently used elements
下面的元素使用CSS替代:
- [font](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/font)
- [The Centered Text element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/center)
- [The Bigger Text element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/big)
- [The Marquee element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/marquee)
> 文本的滚动
- [The Non-Breaking Text element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nobr)

### nobr
Instead, use the CSS property white-space like this:
```
<span style="white-space: nowrap;">Long line with no breaks</span>
```

### [The Plain Text element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/plaintext)
使用下面的元素替代:
- pre
- code

### [strikethrough](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strike)
- 推荐使用
```
<del>这个是删除线</del>
```
- 原来使用s
```
<s>This a strikethrough (horizontal line) over text.</s>
```

## [Object](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)
- [The Object Parameter element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/param)    
Note: Use the <code><object></code> element with a data attribute to set the URL of an external resource.
- [The Embed Fallback element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noembed)    
Note: Use <code><object></code> instead, with fallback content between the opening and closing tags of the element.

## Frame and other
- [frame](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/frame)
- [frameset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/frameset)
- [The Frame Fallback element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noframes)

other:
- [The Ruby Base element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rb)
- [The Ruby Text Container element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rtc)
- [acronym](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/acronym)
- [The Directory element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dir)
- [The Teletype Text element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tt)
- [xmp](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/xmp)
