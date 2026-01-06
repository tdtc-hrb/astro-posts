---
layout: ../../layouts/MarkdownPostLayout.astro
title: "JS的lambda表达式"
date: 2020-04-10
author: "tdtc"
---

# Before rewriting
```js
function selectedReddit(state = 'user/8', action){
  switch (action.type) {
    case SELECT_REDDIT:
      return action.reddit
    default:
      return state
  }
}
```

# After rewriting

```js
const selectedReddit = (state = 'user/8', action) => {
  switch (action.type) {
    case SELECT_REDDIT:
      return action.reddit
    default:
      return state
  }
}
```

# 参考    
[《Arrow functions》](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
