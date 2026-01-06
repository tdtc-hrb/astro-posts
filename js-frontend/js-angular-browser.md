---
layout: ../../layouts/MarkdownPostLayout.astro
title: "platform-browser"
description: "platform-browser vs. platform-browser-dynamic"
date: 2025-05-29
author: "tdtc"
---

[browser vs browser-dynamic](https://stackoverflow.com/a/40338777)
```
The difference between platform-browser-dynamic and platform-browser is the way your Angular app will be compiled.

Using the dynamic platform makes Angular send the just-in-time compiler to the front-end along with your application. 
Which means your application is being compiled client-side.

On the other hand, using platform-browser leads to an ahead-of-time pre-compiled version of your application being sent to the browser. 
Which usually means a significantly smaller package is sent to the browser.
```

- v19
```
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule, {
  ngZoneEventCoalescing: true,
})
  .catch(err => console.error(err));
```
- v20
```
import { platformBrowser } from '@angular/platform-browser';
import { AppModule } from './app/app-module';

platformBrowser().bootstrapModule(AppModule, {
  ngZoneEventCoalescing: true,
})
  .catch(err => console.error(err));
```

### [Explanation](http://niisar.blogspot.com/2016/11/platform-browser-vs-platform-browser.html)
-  @angular/platform-browser
1. It contains code shared for browser execution (DOM thread, WebWorker)
2. Ahead-of-Time pre-compiled version of application being sent to the browser. 
Which usually means a significantly smaller package being sent to the browser.

- @angular/platform-browser-dynamic
1. It contains the client side code that processes templates (bindings, components, ...) and reflective dependency injection.
2. Uses Just-in-Time compiler and make's application compile on client-side.

When the offline template compiler is used, platform-browser-dynamic isn't necessary because all reflective access 
and metadata are converted to generated code. 
