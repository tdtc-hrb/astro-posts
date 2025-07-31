---
layout: ../../layouts/MarkdownPostLayout.astro
title: "使用Astro在github上写blog"
description: "添加分页、blog article、deprecated feature"
date: 2025-05-29
author: "tdtc"
---
Also see [使用hugo在gitee上写blog](https://www.cnblogs.com/xiaobin-hlj80/p/12651114.html)

## pagination
- [ampmonteiro](https://github.com/ampmonteiro/astro-tutorial-blog-pagination)

### Step 1
拷贝blog(src/pages/blog)中的文件:
- pages的page目录
```
[page].astro
```
- pages目录
```
index.astro
```
### Step 2
修改index.astro:
- Original
```
import BlogPost from '../../components/BlogPost.astro';
import BaseLayout from '../../layouts/BaseLayout.astro';
```
- now
```
import BlogPost from '../components/BlogPost.astro';
import BaseLayout from '../layouts/BaseLayout.astro';
```

### Step 3
astro.config.mjs
- [site](https://docs.astro.build/en/guides/deploy/github)
```
site: "https://tdtc-hrb.github.io",
base: "ops-win",
```

#### hard-coded URLs
- `[page].astro`
```
<a href="/blog">First</a>
```
Replace with 
```
<a href={baseUrl} >First</a>
```
- index.astro
```
  <a href="/blog/2">Next</a>
```
Replace with 
```
<a href={baseUrl + '/page/2'} >First</a>
```

## blog article
- Required
- option
### Required
- layout
- title
- date

### option
- description
- author
- image
- tags
### row limit
- `[page].astro`
```
return paginate(all, { pageSize: 8 });
```
- index.astro
```
const allPosts = (Object.values(import.meta.glob('../../pages/posts/*.md', { eager: true }))).slice(
  0,
  8
);
```

## deprecated feature
- Astro.glob
### [astroglob](https://docs.astro.build/en/guides/upgrade-to/v5/#deprecated-astroglob)
- index.astro    
Use 
```
await Astro.glob('../../pages/posts/*.md');
```
instead of
```
Object.values(import.meta.glob('../pages/posts/*.md', { eager: true }))
```

- `[page].astro`    
Use 
```
await Astro.glob('../../pages/posts/*.md');
```
instead of
```
Object.values(import.meta.glob('../../pages/posts/*.md', { eager: true }));
```

## Run
- install
```
npm install
```
- build
```
npm run build
```
- preview
```
npm run preview
```
