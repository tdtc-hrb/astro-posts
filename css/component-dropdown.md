---
layout: ../../layouts/MarkdownPostLayout.astro
title: "dropdown - tailwindcss"
description: "dropdown"
date: 2025-04-05
author: "tdtc"
---

- bootstrap
> v4.6.2
```
        <li class="dropdown">
            <a  href="#">About</a>
            <div class="dropdown-menu">
                <a class="dropdown-item" href="https://localhost:5001/About/profile">profile</a>
                <a class="dropdown-item" href="https://localhost:5001/About/innovations">innovations</a>
                <a class="dropdown-item" href="https://localhost:5001/About/qualifications">qualifications</a>
            </div>
        </li>
```
- tailwindcss
```
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <script src="https://unpkg.com/@tailwindcss/browser@4"></script>
</head>
<body>
<li class="relative">
    <div class="flex-col" style="cursor:pointer">
        <a class="inline-flex items-center px-4 py-2" href="#" onclick="toggleDropdown()">
            About1
        </a>
        <svg class="w-5 h-5 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" stroke="currentColor" onclick="toggleDropdown()">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 10l5 5 5-5H7z"/>
        </svg>
    </div>
    <div class="absolute left-0 z-50 float-left hidden py-2 mt-1 text-base bg-white border border-gray-300 rounded group-hover:block">
        <a class="block py-1 px-6 font-normal text-gray-900 whitespace-nowrap border-0 hover:bg-gray-200" href="https://localhost:5001/About/profile">profile</a>
        <a class="block py-1 px-6 font-normal text-gray-900 whitespace-nowrap border-0 hover:bg-gray-200" href="https://localhost:5001/About/innovations">innovations</a>
        <a class="block py-1 px-6 font-normal text-gray-900 whitespace-nowrap border-0 hover:bg-gray-200" href="https://localhost:5001/About/qualifications">qualifications</a>
    </div>
</li>

<script>
    function toggleDown(element) {
        // Prevent exception: captured element is svg
        if (element.nodeName != 'svg')
            element.classList.toggle('hidden');
    }

    function toggleDropdown() {
        const parentElement = event.target.parentNode.parentNode;
        const element = parentElement.children[1];

        console.log(element.nodeName);
        toggleDown(element);
        
        setTimeout(() => {
            toggleDown(element);
        }, 2000);
    }
</script>

</body>
</html>
```

### w-full
在特定的环境下会出现溢出的情况    
[Background length overflow on hover](https://play.tailwindcss.com/Hqp9d5Ersu)

删除即可解决

### dropdown - v0.1
- dropdown-item
```
block w-full py-1 px-6 font-normal text-gray-900 whitespace-nowrap border-0
```
- dropdown-menu
```
absolute left-0 z-50 float-left hidden list-none py-2 mt-1 text-base bg-white border border-gray-300 rounded-sm
```

## Ref
- [to v4](https://tailwindcss.com/docs/upgrade-guide)
- [to v3](https://v3.tailwindcss.com/docs/upgrade-guide)
- [to v2](https://v2.tailwindcss.com/docs/upgrading-to-v2)
- [to v1](https://v1.tailwindcss.com/docs/upgrading-to-v1)
- [v0.1](https://github.com/awssat/tailwindo/blob/master/src/Framework/BootstrapFramework.php)
- [items-center](https://tailwindcss.com/docs/align-items#center)
- [Element: classList property](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
- [How TO - Clickable Dropdown](https://www.w3schools.com/howto/howto_js_dropdown.asp)
