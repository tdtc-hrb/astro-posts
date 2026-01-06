---
layout: ../../layouts/MarkdownPostLayout.astro
title: "CSS animations"
description: "animation"
date: 2025-06-04
author: "tdtc"
---
- Properties
- Transform
- Keyframes

## [Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/animation#constituent_properties)
```
/* @keyframes duration | easing-function | delay |
iteration-count | direction | fill-mode | play-state | name */
animation: 3s ease-in 1s 2 reverse both paused slide-in;
```

### basic
```
/* @keyframes duration | easing-function | delay | name */
animation: 3s linear 1s slide-in;
```
- [name](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-name)
- [duration](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-duration)
- [easing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function)

for example:
```
animation: myanimation 20s linear infinite;
```

## [transform function](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function)
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>KeyFrames</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
  	<div class="marquee">
		<p>Hello CSS</p>
	</div>

  </body>

</html>
```
### Translation (moving)
- [x-axis](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateX)
- [y-axis](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateY)

## CSS Keyframes
- Keyframe using percentages
- Keyframe using from-to keywords

### Keyframe using percentages
```
        @keyframes scroll-left {
            0% {
                transform: translateX(100%);
            }
            100% {
                transform: translateX(-100%);
            }
        }
```
### Keyframe using from-to keywords
```
@keyframes my-scroll {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

- style.css
```
.marquee {
	height: 50px;
	overflow: hidden;
	position: relative;
	background: #fefefe;
	color: #333;
	border: 1px solid #4a4a4a;
}

.marquee p {
/* animation properties */
animation-name: my-scroll;
animation-duration: 5s;
animation-iteration-count: infinite;
animation-timing-function: linear;
	position: absolute;
	width: 100%;
	height: 100%;
	margin: 0;
	line-height: 50px;
	text-align: center;
}

@keyframes my-scroll {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}

```

## Ref
- [The Complete CSS Animations Tutorial](https://www.lambdatest.com/blog/css-animations-tutorial)
- [Animate elements on scroll with Scroll-driven animations](https://developer.chrome.com/docs/css-ui/scroll-driven-animations)
