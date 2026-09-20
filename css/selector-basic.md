---
layout: ../../layouts/MarkdownPostLayout.astro
title: "CSS选择器"
description: "关系选择器, 选择器"
date: 2025-04-19
author: "tdtc"
---


# [Combinators](https://www.w3schools.com/cssref/css_ref_combinators.php)
- Child combinator
- Descendant combinator
- Next-sibling combinator
- Subsequent-sibling combinator

### [子元素](https://www.w3school.com.cn/css/css_selector_child.asp)
当前元素的下一级元素。
```css
element1 > element2 {
  css declarations;
} 
```
- [tailwind](https://tailwindcss.com/docs/hover-focus-and-other-states#styling-direct-children)
```
*
```
equ
```
>
```
### [后代元素](https://www.w3school.com.cn/css/css_selector_descendant.asp)
当前元素（ol）下的所有li元素。
```xml
ol li
```
- [tailwind](https://tailwindcss.com/docs/hover-focus-and-other-states#styling-all-descendants)
```
**
```
equ
```
space key
```

### [接续兄弟元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Next-sibling_combinator)
```
element1 + element2 {
  css declarations;
} 
```

### [后续兄弟元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Subsequent-sibling_combinator)
```
element1 ~ element2 {
  css declarations;
} 
```

# [Selectors](https://www.w3schools.com/cssref/css_selectors.php)
| Selector type | CSS | 说明 |
|-|-|-|
| Tag name | p {}|对整个网页中标签有效 |
| ID   | #some-id {} | 对网页中指定id有效 |
| Class | .some-class {} | 对网页中相同类名有效 |

## [CSS Attribute Selectors](https://www.w3schools.com/cssref/sel_attribute.php)
- [“^” 开头匹配](https://www.w3school.com.cn/cssref/selector_attr_begin.asp)

- [“$” 结尾匹配](https://www.w3school.com.cn/cssref/selector_attr_end.asp)

- ["*" 包含匹配](https://www.w3school.com.cn/cssref/selector_attr_contain.asp)

- [value 匹配](https://www.w3schools.com/cssref/sel_attribute_value.php)

### value 匹配
```
[attribute = value] {
  css declarations;
} 
```
