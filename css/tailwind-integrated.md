---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Integrated tailwindccs"
description: "Using tailwind in an integrated way"
date: 2023-03-11
author: "tdtc"
---
- install
```
cd veic-web_asp
npm init -y
npm install tailwindcss @tailwindcss/cli
```
## gen
- v4(new)
```
npx @tailwindcss/cli -i ./wwwroot/css/site2.css -o ./wwwroot/css/site2tw.css --optimize
```
- v3(legacy)
```
npx @tailwindcss/cli -i ./wwwroot/css/site2-legacy.css -o ./wwwroot/css/site3tw.css --optimize
```
About input file:
- Rename site.css to site2.css or site2-legacy.css;
- Add: legacy or new at the beginning of the file.

### new
- site2.css:
```
@layer theme, base, components, utilities;

@import "tailwindcss/theme.css" layer(theme) prefix(tw);
@import "tailwindcss/utilities.css" prefix(tw);
```

### legacy
- gen config file
```
cd gen-config-dir
npm install -D tailwindcss@3 postcss autoprefixer

npx tailwindcss init -p
```
tailwind.config.js:
```
module.exports = {
    content: ["./**/*.html"],
    prefix: "tw",
    important: true,
    corePlugins: {
        preflight: false,
    }
}
```
- site2-legacy.css:
```
@config "../../tailwind.config.js";
@layer theme, base, components, utilities;

@import "tailwindcss/theme.css" layer(theme);
@import "tailwindcss/utilities.css";
```

## Ref
- [tailwind cli - v4](https://tailwindcss.com/docs/installation/tailwind-cli)
- [load config - v4](https://tailwindcss.com/docs/upgrade-guide#using-a-javascript-config-file)
- [tailwindcss - v3](https://v3.tailwindcss.com/docs/installation/using-postcss)
- [Using CLI(cmd) instead of tailwindcss(cmd)](https://tailwindcss.com/docs/upgrade-guide#using-tailwind-cli)
- [prefix - v4](https://tailwindcss.com/docs/styling-with-utility-classes#using-the-prefix-option)
- [Use Tailwind v4 and Bootrstap 5 together -v4](https://github.com/tailwindlabs/tailwindcss/discussions/15755#discussioncomment-11932934):
- [Can use both Tailwind css and Bootstrap 4 at the same time? - v3](https://stackoverflow.com/a/74199891)
