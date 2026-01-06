---
layout: ../../layouts/MarkdownPostLayout.astro
title: "svg - html"
description: "Scalable Vector Graphics"
date: 2025-03-14
author: "tdtc"
---

Width and height are set in CSS.

## viewBox
Syntax:
```
viewBox = "min-x min-y width height"
```
Attribute Values:
- min-x: It is used to set the horizontal axis. It is used to make the SVG move on a horizontal axis (i.e Left and Right).
- min-y: It is used to set the vertical axis. It is used to make the SVG move on a vertical axis (i.e Up and Down).
- width: It is used to set the width of viewbox.
- height: It is used to set the height of viewbox.

## path
- d
> Required. A set of commands which define the path.

### postion
Note: All of the commands above can also be expressed in lower case. 
Upper case means absolutely positioned, lower case means relatively positioned.

- M = moveto (move from one point to another point)
- L = lineto (create a line)
- H = horizontal lineto (create a horizontal line)
- V = vertical lineto (create a vertical line)
- C = curveto (create a curve)
- S = smooth curveto (create a smooth curve)
- Q = quadratic Bézier curve (create a quadratic Bézier curve)
- T = smooth quadratic Bézier curveto (create a smooth quadratic Bézier curve)
- A = elliptical Arc (create a elliptical arc)
- Z = closepath (close the path)

## Ref
- [path](https://www.w3schools.com/graphics/svg_path.asp)
- [viewBox](https://www.geeksforgeeks.org/svg-viewbox-attribute/)
- [hero - icons](https://github.com/tailwindlabs/heroicons)
- [Working with SVG Icons](https://v1.tailwindcss.com/course/working-with-svg-icons)
