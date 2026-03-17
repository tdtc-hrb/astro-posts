---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Beware of xxx_cast"
description: "Add or remove tool buttons and menus; Add dialog boxes;"
date: 2025-11-16
author: xiaobin
tags: ["C++"]
---
The default version uses MSVC >=1930, which is Visual Studio 2022.

- [static_cast conversion](https://en.cppreference.com/w/cpp/language/static_cast.html)
> Non-enforce
- [reinterpret_cast conversion](https://en.cppreference.com/w/cpp/language/reinterpret_cast.html)
> Enforce

### MSVC
In MSVC, XXX_cast (C++ standard) is still under continuous improvement.
#### UINT_PTR
- WPARAM
```
typedef UINT_PTR            WPARAM;
```
- for example
```
SendMessage(WM_ICONERASEBKGND, reinterpret_cast<WPARAM>(dc.GetSafeHdc()), 0);
```

#### Handle
```
// The system calls this function to obtain the cursor to display while the user drags
//  the minimized window.
HCURSOR CBaseDemoDlg::OnQueryDragIcon()
{
	return static_cast<HCURSOR>(m_hIcon);
}
```

## Ref
- [Why this reinterpret_cast fails in Visual Studio 2017~2019?](https://stackoverflow.com/questions/49060809/why-this-reinterpret-cast-fails-in-visual-studio)
- [When should static_cast, dynamic_cast, const_cast, and reinterpret_cast be used?](https://stackoverflow.com/a/332086)
