---
layout: ../../layouts/MarkdownPostLayout.astro
title: "nav - tailwindcss"
description: "nav"
date: 2025-03-12
author: "tdtc"
---

- tailwindcss
```
    <nav class="items-center content-between py-3 px-4 shadow">
        <div class="container mx-auto sm:px-4 gap-4 flex items-center">
            <a class="inline-block pt-1 pb-1 mr-4 text-lg whitespace-no-wrap" href="/">Veic_web_ASP</a>

            <div>
                <label>Label1</label>
            </div>
            <div>
                <label>Label2</label>
            </div>

        </div>
    </nav>
```

- bootstrap
> v4.6.2
```
<nav class="navbar navbar-expand-sm navbar-toggleable-sm navbar-light bg-white border-bottom box-shadow mb-3">
    <div class="container">
        <a class="navbar-brand" href="/">Veic_web_ASP</a>
    </div>
</nav>
```

### tailwindcss
- navbar
```
relative flex flex-wrap items-center content-between py-3 px-4
```
- navbar-brand
```
inline-block pt-1 pb-1 mr-4 text-lg whitespace-no-wrap
```
- navbar-nav
```
flex flex-wrap list-reset pl-0 mb-0
```
- navbar-text
```
inline-block pt-2 pb-2
```
- navbar-dark
```
text-white
```
- navbar-light
```
text-black
```
- navbar-collapse
```
flex-grow items-center
```
- navbar-expand
```
flex-no-wrap content-start
```
- navbar-toggler
> navbar-expand-*
```
py-1 px-2 text-md leading-normal bg-transparent border border-transparent rounded
```

## Ref
- [to v4](https://tailwindcss.com/docs/upgrade-guide)
- [to v3](https://v3.tailwindcss.com/docs/upgrade-guide)
- [to v2](https://v2.tailwindcss.com/docs/upgrading-to-v2)
- [to v1](https://v1.tailwindcss.com/docs/upgrading-to-v1)
- [v0.1](https://github.com/awssat/tailwindo/blob/master/src/Framework/BootstrapFramework.php)
- [Navigation - v1](https://v1.tailwindcss.com/components/navigation)
- [font weight](https://tailwindcss.com/docs/font-weight)
- [font size](https://tailwindcss.com/docs/font-size)
- [Navigation - v3](https://nouvelle-techno.fr/articles/creer-une-barre-de-navigation-avec-tailwind-css)
