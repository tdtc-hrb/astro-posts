---
layout: ../../layouts/MarkdownPostLayout.astro
title: "ES6 展开运算符"
description: "spreed operator(...)"
date: 2020-04-10
author: "tdtc"
---

# Multiple return values
```js
const configStore = () => {
  const sagaMiddleware = createSagaMiddleware()
  return {
    ...createStore(rootReducer, applyMiddleware(sagaMiddleware)),
    runSaga: sagaMiddleware.run,
  }
}
```

# Reference
- [Spread syntax](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
