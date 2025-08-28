---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Migrating from v19 to v20"
description: "File name changes, animations"
date: 2025-05-29
author: "tdtc"
---

### File name
|v19|v20|
|-|-|
|app.module.ts|app-module.ts|
|app.component.ts|app.ts|
|app.component.html|app.html|
|app.component.css|app.css|

### [animations](https://angular.dev/guide/animations/migration)
> IMPORTANT: The Angular team recommends using native CSS for animations instead of the Animations package for all new code. 
> Use this guide to understand existing code built with the Animations Package. 
> See Migrating away from Angular's Animations package to learn how you can start using pure CSS animations in your apps.

The [animation](https://github.com/angular/angular/commit/fc5d187da5e8895d60caa35b7b59e234998eddf0) has been removed in [v20.0/v19.2](https://angular.dev/guide/animations).
