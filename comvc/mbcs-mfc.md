---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The MBCS libraries were deprecated in Visual Studio 2013 and Visual Studio 2015"
description: "Removing MBCS deprecated warning in VS2013/VS2015"
date: 2025-11-27
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
hint info:
```
1>C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC\atlmfc\include\afx.h(38): error C2220: warning treated as error - no 'object' file generated
1>C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC\atlmfc\include\afx.h(38): warning C4996: 'MBCS_Support_Deprecated_In_MFC': MBCS support in MFC is deprecated and may be removed in a future version of MFC.
1>C:\Program Files (x86)\Microsoft Visual Studio 12.0\VC\atlmfc\include\afx.h(33) : see declaration of 'MBCS_Support_Deprecated_In_MFC'
```

### Why is MBCS needed?
Some languages, for example, Japanese and Chinese, have large character sets. 
To support programming for these markets, 
the MFC enables two different approaches to handling large character sets:

- Unicode, <i>wchar_t</i> based wide-characters, and strings encoded as UTF-16.
- Multibyte Character Sets (MBCS), <i>char</i> based single or double-byte characters and strings encoded in a locale-specific character set.

### Triggering reason
Project Properties -> General
```
Character Set: Use Multi-Byte Character Set
```
Referenced from "[Error preprocessor directives when building](https://stackoverflow.com/a/20706970)".

### Solution
```
Project Properties -> C\C++ > Preprocessor -> Preprocessor Definition
```
add:
```
NO_WARN_MBCS_MFC_DEPRECATION
```

## Ref
- [Unicode and Multibyte Character Set (MBCS) Support](https://learn.microsoft.com/en-us/cpp/atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support)
- [Removing MBCS deprecated warning in VS 2013](https://cppcodetips.wordpress.com/tag/removing-mbcs-deprecated-warning-in-vs-2013)
- [MFC support for MBCS deprecated in Visual Studio 2013](https://devblogs.microsoft.com/cppblog/mfc-support-for-mbcs-deprecated-in-visual-studio-2013)
