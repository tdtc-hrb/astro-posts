---
layout: ../../layouts/MarkdownPostLayout.astro
title: "breadcrumb - tailwindcss"
description: "breadcrumb"
date: 2025-04-07
author: "tdtc"
---

- bootstrap
```
<ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="https://localhost:5001/menu3">news</a></li>
    <li class="breadcrumb-item"><a href="https://localhost:5001/Company/news">company news</a></li>
    <li class="breadcrumb-item active">
        body
    </li>
</ol>
```
- Tailwind
```
  <ol class="flex flex-wrap list-none pt-3 pb-3 py-4 px-4 mb-4 rounded items-center">
    <li class="inline-block px-2 py-2"><a href="#" class="no-underline text-indigo">Home</a></li>
    <li><svg width="20" height="20" viewBox="0 0 20 20">
<path d="M8.21967 5.21967C8.51256 4.92678 8.98744 4.92678 9.28033 5.21967L13.5303 9.46967C13.8232 9.76256 13.8232 10.2374 13.5303 10.5303L9.28033 14.7803C8.98744 15.0732 8.51256 15.0732 8.21967 14.7803C7.92678 14.4874 7.92678 14.0126 8.21967 13.7197L11.9393 10L8.21967 6.28033C7.92678 5.98744 7.92678 5.51256 8.21967 5.21967Z" />
</svg></li>
    <li class="inline-block px-2 py-2"><a href="#" class="no-underline text-indigo">Library</a></li>
    <li><svg width="20" height="20" viewBox="0 0 20 20">
<path d="M8.21967 5.21967C8.51256 4.92678 8.98744 4.92678 9.28033 5.21967L13.5303 9.46967C13.8232 9.76256 13.8232 10.2374 13.5303 10.5303L9.28033 14.7803C8.98744 15.0732 8.51256 15.0732 8.21967 14.7803C7.92678 14.4874 7.92678 14.0126 8.21967 13.7197L11.9393 10L8.21967 6.28033C7.92678 5.98744 7.92678 5.51256 8.21967 5.21967Z" />
</svg></li>
    <li class="inline-block px-2 py-2 text-gray-700/50">Data</li>
  </ol>
```

### tailwindcss
- breadcrumb
```
flex flex-wrap list-none pt-3 pb-3 py-4 px-4 mb-4 rounded
```
- svg align
```
items-center
```

#### [list-reset](https://v1.tailwindcss.com/docs/upgrading-to-v1#8-remove-any-usage-of-list-reset)
Please use "none" to replace:
```
list-none
```

#### breadcrumb item
```
inline-block px-2 py-2
```
- last
```
inline-block px-2 py-2 text-gray-700/50
```

### bootstrap - v4.6.2
```
.breadcrumb {
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  padding: 0.75rem 1rem;
  margin-bottom: 1rem;
  list-style: none;
  background-color: #e9ecef;
  border-radius: 0.25rem;
}

.breadcrumb-item + .breadcrumb-item::before {
  float: left;
  padding-right: 0.5rem;
  color: #6c757d;
  content: "/";
}
```

## Ref
- [to v4](https://tailwindcss.com/docs/upgrade-guide)
- [to v3](https://v3.tailwindcss.com/docs/upgrade-guide)
- [to v2](https://v2.tailwindcss.com/docs/upgrading-to-v2)
- [to v1](https://v1.tailwindcss.com/docs/upgrading-to-v1)
- [v0.1](https://github.com/awssat/tailwindo/blob/master/src/Framework/BootstrapFramework.php)
- [online edit](https://play.tailwindcss.com/)
- [Tailwind CSS Breadcrumb - tailwindo](https://github.com/awssat/tailwindo/blob/master/src/Framework/BootstrapFramework.php#L557)
