---
layout: ../../layouts/MarkdownPostLayout.astro
title: "tailwindcss upgrade"
description: "v0.1, v1, v2, v3 to v4"
date: 2025-04-09
author: "tdtc"
---

### [prefix](https://stackoverflow.com/a/79411170)
- v4
```
myprefix:text-red-500
myprefix:hover:text-red-500
```
- v3
```
myprefix-text-red-500
hover:myprefix-text-red-500
```


## utilities
- [Renamed utilities - v4](https://tailwindcss.com/docs/upgrade-guide#renamed-utilities):

|v3|v4|
|-|-|
|shadow-sm|shadow-xs|
|shadow|shadow-sm|
|drop-shadow-sm|drop-shadow-xs|
|drop-shadow|drop-shadow-sm|
|blur-sm|blur-xs|
|blur|blur-sm|
|backdrop-blur-sm|backdrop-blur-xs|
|backdrop-blur|backdrop-blur-sm|
|rounded-sm|rounded-xs|
|rounded|rounded-sm|
|outline-none|outline-hidden|
|ring|ring-3|

- [class-name-changes - v3](https://v3.tailwindcss.com/docs/upgrade-guide#class-name-changes):

|old|new|
|-|-|
|overflow-clip|text-clip|
|overflow-ellipsis|text-ellipsis|
|flex-grow-0|grow-0|
|flex-shrink|shrink|

### [flex-grow](https://tailwindcss.com/docs/upgrade-guide#removed-deprecated-utilities)
- v4
```
grow-*
```
- v3
```
flex-grow-*
```

### [flex no wrap](https://v2.tailwindcss.com/docs/upgrading-to-v2#update-renamed-utility-classes)
- v2+
```
flex-nowrap
```
- v1
```
flex-no-wrap
```

### [flex no shrink](https://v1.tailwindcss.com/docs/upgrading-to-v1#11-replace-flex-no-grow-shrink-with-flex-grow-shrink-0)
- v4
```
shrink-0
```
- v1
```
flex-shrink-0
```
- v0.1
```
flex-no-shrink
```

### whitespace
- v2+
```
whitespace-nowrap
```
- v1
```
whitespace-no-wrap
```

### [rounded](https://tailwindcss.com/docs/upgrade-guide#renamed-utilities)
- v4
```
rounded-sm
```
- v3
```
rounded
```

### list none
- v1+
```
list-none
```
- v0.1
```
list-reset
```

### line height
- v4
```
leading-[1.5]
```
- v3
```
leading-normal line-height: 1.5;
```

#### leading tight
- v4
```
leading-[1.25]
```
- v3
```
leading-tight
```

### [aspect ratio - v4](https://tailwindcss.com/docs/aspect-ratio)
- [BootstrapFramework.php](https://github.com/awssat/tailwindo)
```
            //https://getbootstrap.com/docs/4.6/utilities/embed/
            'embed-responsive'       => 'relative block w-full p-0 overflow-hidden',
            'embed-responsive-item'  => 'absolute top-0 bottom-0 left-0 w-full h-full border-0',
            'embed-responsive-21by9' => 'aspect-21/9',
            'embed-responsive-16by9' => 'aspect-16/9',
            'embed-responsive-4by3'  => 'aspect-4/3',
            'embed-responsive-1by1'  => 'aspect-square',
```

#### v2 and v3
- [plugins - v2](https://v2.tailwindcss.com/docs/plugins#aspect-ratio)
- [plugins - v3](https://v3.tailwindcss.com/docs/plugins#aspect-ratio)

### position
- absolute
- relative
- fixed
- static
#### sticky
- v1+
```
position: sticky;
```
- v0.1
```
none
```

### [scrolling touch](https://v2.tailwindcss.com/docs/upgrading-to-v2#the-scrolling-touch-and-scrolling-auto-utilities-have-been-removed)
we’ve removed these two utilities from v2.0.
- scrolling-touch
- scrolling-auto

### Class name changes - v2
[Update renamed utility classes](https://v2.tailwindcss.com/docs/upgrading-to-v2#update-renamed-utility-classes) :
|old|new|
|-|-|
|whitespace-no-wrap|whitespace-nowrap|
|flex-no-wrap|flex-nowrap|
|col-gap-{n}|gap-x-{n}|
|row-gap-{n}|gap-y-{n}|

- [Support for IE 11 has been dropped - v2](https://v2.tailwindcss.com/docs/upgrading-to-v2#support-for-ie-11-has-been-dropped)

#### [Replace shadow-outline and shadow-xs with ring utilities](https://v2.tailwindcss.com/docs/upgrading-to-v2#replace-shadow-outline-and-shadow-xs-with-ring-utilities)
|old|new|
|-|-|
|focus:shadow-outline|focus:ring|
|shadow-xs|ring-1 ring-black ring-opacity-5|

#### [Replace clearfix with flow-root](https://v2.tailwindcss.com/docs/upgrading-to-v2#replace-clearfix-with-flow-root)
|old|new|
|-|-|
|clearfix|flow-root|

#### [Update font-weight class names for 100 and 200 weights](https://v2.tailwindcss.com/docs/upgrading-to-v2#update-font-weight-class-names-for-100-and-200-weights)
|Font weight|old|new|
|-|-|-|
|100|font-hairline|font-thin|
|200|font-thin|font-extralight|



## [bs2tw](https://github.com/awssat/tailwindo/blob/master/src/Framework/BootstrapFramework.php)

### text

#### initialism
- bs
```
  font-size: 90%;
  text-transform: uppercase;
```
- tw
```
text-xs
uppercase
```


## Ref
- [Upgrading from v0.x to v1.0](https://v1.tailwindcss.com/docs/upgrading-to-v1)
- [Migrating from Bootstrap to Tailwind](https://johnzanussi.com/posts/bootstrap-to-tailwind-migration)
