---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Customizing Bootstrap with SASS for Beginners"
description: "Option B: Include parts of Bootstrap"
date: 2025-04-14
author: "tdtc"
---


- [v4.6.2](https://github.com/twbs/bootstrap/releases/tag/v4.6.2) 支持 [Internet Explorer 11](https://github.com/twbs/bootstrap/blob/v4.6.2/.browserslistrc)
```
git clone -b v4.6.2 --single-branch https://github.com/twbs/bootstrap.git
```

### scss
```
//custom.scss

@import "../bootstrap/scss/functions";
@import "../bootstrap/scss/variables";
@import "../bootstrap/scss/mixins";

@import "../bootstrap/scss/buttons";
//@import "../bootstrap/scss/nav";
```
### install sass
- node-sass
```
npm install -g node-sass
```
- [dart-sass](https://github.com/chatscope/chat-ui-kit-react/issues/156)
```
npm install -g sass@1.77.6
```

### Gen
- dart-sass
```
sass custom.scss custom.css
```
- node-sass
```
node-sass custom.scss custom.css
```


## Ref
- [Customizing Bootstrap with SASS for Beginners](https://devndijon.hashnode.dev/customizing-bootstrap-with-sass-for-beginners)
