---
layout: ../../layouts/MarkdownPostLayout.astro
title: "tab - tailwindcss"
description: "tab"
date: 2025-04-06
author: "tdtc"
---

### pure css
- css
```
input[type="radio"] {
  display: none;
  position: absolute;
}
input[type="radio"] + .mytabs > label {
  display: inline-block;
  float: left;
  width: 33%;
}
input[type="radio"] + .mytabs > div {
  display: none;
  position: absolute;
  top: 65px;
  width: 100%;
}
input[type="radio"]:checked + .mytabs > .tab-pane {
  display: block;
}
input[type="radio"]:checked + .mytabs > label {
  background-color: #B1CF6F;
}
```
- html
```
<div class="tab-content">
  <input type="radio" name="tabs" id="tab1" checked>
  <div class="mytabs">
    <label for="tab1">one</label>
    <div class="tab-pane">
      <p>All my content for the first tab goes here.</p>
    </div>
  </div>
  <input type="radio" name="tabs" id="tab2">
  <div class="mytabs">
    <label for="tab2">two</label>
    <div class="tab-pane">
      <p>this is two</p>
    </div>
  </div>
</div>
```

## Hybrid css
- js
```
    function toggleTabs(id1, id2) {
        const elementCurrent = document.getElementById(id1);
        const element2 = document.getElementById(id2)
        console.log(elementCurrent);

        if (elementCurrent.classList != "block")
        {
            elementCurrent.classList.remove('tw:hidden');
            element2.classList.add("tw:hidden");
        }

    }
```
- html
```
<nav class="tw:tabs tw:tabs-bordered" role="tablist">
  <button class="tw:tab tw:active-tab:tab-active tw:active" onclick="toggleTabs('tabs1', 'tabs2')" data-tab="tabs1">
    Home
  </button>
  <button class="tw:tab tw:active-tab:tab-active" onclick="toggleTabs('tabs2', 'tabs1')" data-tab="tabs2">
    Profile
  </button>
</nav>

<div class="tw:mt-3">
  <div id="tabs1" class="tw:block">
    <p>Welcome to the Home tab!</p>
  </div>
  <div id="tabs2" class="tw:hidden">
    <p>This is your Profile tab.</p>
  </div>
</div>
```


### [flyonui](https://flyonui.com/docs/getting-started/quick-start/)
- install
```
npm i -D flyonui@latest
```
- config
> site2.css
```
@plugin "flyonui";
@import "../../node_modules/flyonui/variants.css" prefix(tw);
```
- Include FlyonUI JavaScript in HTML for JS components
```
<script src="path/to/flyonui/dist/tabs.js"></script>
```

#### deploy
copy "flyonui" to "wwwroot/lib"


## Ref
- [inline styles](https://tailwindcss.com/docs/styling-with-utility-classes#when-to-use-inline-styles)
- [How can I make tabs with only CSS?](https://stackoverflow.com/questions/25943488/how-can-i-make-tabs-with-only-css)
- [tabs - fly](https://flyonui.com/docs/navigations/tabs-pills/)
- [jq](https://jqueryui.com/tabs/)
