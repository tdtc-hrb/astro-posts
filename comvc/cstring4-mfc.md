---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The CString Class - 4"
description: "Loading STRINGTABLE values"
date: 2025-12-03
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
You need to change the language settings!

### Language set
Open resource view;

Click "String Table" and change the language attribute:
```
Chinese (Simplified, PRC)
```

![string table - p.r.c](https://github.com/tdtc-hrb/csdn/raw/master/images/stringtable-myexplorer.png)

### Loading STRINGTABLE value
```
void CTextView::AssertValid() const
{
    CEditView::AssertValid();

    CString fmt;

    fmt.LoadString(IDS_STRING1);
    GetEditCtrl().SetWindowText(fmt);
}
```

## Ref
- [CString Management](http://www.flounder.com/cstring.htm)
