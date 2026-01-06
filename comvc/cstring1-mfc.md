---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The CString Class - 1"
description: "CStrings greatly simplifies string manipulation in MFC."
date: 2025-12-03
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
You used a CString object in the previous section, and there’s more to it than you have seen so far. 
The CString class provides a convenient and easy-to-use mechanism for handling strings that you can use just about anywhere a string is required. 
To be more precise, you can use a CString object in place of strings of type ```const TCHAR*```, or of type <i>LPCTSTR</i>, 
which is a type that comes up in Windows API functions. 
If you are using the DDX mechanism for strings, then you must use CString, otherwise DDX won’t work.

### String Basics
- Windows Types
- CString types

#### Windows Types
|name|Description|
|-|-|
|TCHAR |An 8-bit or 16-bit character.  If the UNICODE preprocessor symbol is defined, this compiles to a wchar_t type; if the UNICODE preprocessor symbol is undefined, this compiles to a char type.  This is the preferred way to declare a character variable.
|LPTSTR </br>PTSTR |A pointer to an 8-bit or 16-bit character string.  If the UNICODE preprocessor symbol is defined, this compiles to wchar_t *; if the UNICODE preprocessor symbol is undefined, this compiles to char *.  This is the preferred way of declare a pointer to a string.|
|LPCTSTR <br>PCTSTR |A pointer to a constant 8-bit or 16-bit character string.  If the UNICODE preprocessor symbol is defined, this compiles to const wchar_t *; if the UNICODE preprocessor symbol is undefined, this compiles to const char *.  This is the preferred way to declare a const pointer to a string.  Note that most APIs want LPCTSTR arguments, and a CString can always be used in such a context.|
|_T('x') |A character literal.  If the UNICODE preprocessor symbol is defined, this compiles as L'x', a 16-bit character value; if the UNICODE preprocessor symbol is undefined, this compiles as 'x', an 8-bit character value. This is the preferred way to declare a character constant.|
|_T("abc") |A string literal.  If the UNICODE preprocessor symbol is defined, this compiles as L"abc", a wide-character string terminated with a wide-character NUL; if the UNICODE preprocessor symbol is undefined, this compiles as "abc", an 8-bit string literal terminated with an 8-bit NUL character.  This is the preferred way to declare a string constant.|

#### CString types
|name|Description|
|-|-|
|CString |A string data type.  If the UNICODE preprocessor symbol is defined, this compiles as a type that holds 16-bit wide characters, terminated with a 16-bit NUL (CStringW); if the UNICODE preprocessor symbol is undefined, this compiles as a type that holds 8-bit characters, terminated with an 8-bit NUL (CStringA).|
|CStringA |A string data type.  Independent of the setting of the UNICODE preprocessor symbol, this always represents a sequence of 8-bit characters terminated with an 8-bit NUL.|
|CStringW |A string data type.  Independent of the setting of the UNICODE preprocessor symbol, this always represents a sequence of 16-bit characters terminated with a 16-bit NUL.|
|CStringT |Essentially, an alias for CString.|

### Formatting (including integer-to-CString)
Use of formatting is the most common way of converting from non-string data types to a CString, 
for example, converting an integer to a CString:
```
CString s;
s.Format(_T("%d"), total);
```
### Converting a CString to an integer
The simplest way to convert a CString to an integer value is to use one of the standard string-to-integer conversion routines.

While generally you will suspect that _atoi is a good choice, it is rarely the right choice. 
If you play to be Unicode-ready, you should call the function _ttoi, which compiles into _atoi in ANSI code and _wtoi in Unicode code. 
You can also consider using _tcstoul (for unsigned conversion to any radix, such as 2, 8, 10 or 16) or _tcstol (for signed conversion to any radix). 
For example, here are some examples:
```
CString hex = _T("FAB");
CString decimal = _T("4011");
ASSERT(_tcstoul(hex, 0, 16) == _ttoi(decimal));
```
### Converting a CString to a double
but the required Unicode version did not appear until the VS2005 library. 
This means that <i>_ttof</i> does not exist below VS2005.
```
// ConsoleApplication1.cpp : Defines the entry point for the console application.
//

#include "stdafx.h"

#include <stdio.h>

int _tmain(int argc, _TCHAR* argv[])
{
    if ( argc > 0) 
    {
        double value = _ttof(argv[1]);
 
        printf("output: %e\n", value);
    }

    return 0;
}
```
### Converting a CString of hex digits to an integer
This is a frequent question, because everyone who asks it seems to miss that atoi (and therefore _ttoi) only works on decimal digits 0..9.

The answer is strtoul, wcstoul, or better still, _tcstoul.
```
ULONG strtoul(LPCSTR ptr, LPSTR * endptr, int base)
ULONG wcstoul(LPCWSTR ptr, LPWSTR * endptr, int base)
ULONG _tcstoul(LPCTSTR ptr, LPTSTR * endptr, int base)
```
These functions expect an input string of the form
```
[whitespace] [{+ | ?}] [0 [{ x | X }]] [digits]
```
where whitespace is space or tab characters, and is ignored.  The base value can be any value from 2 through 36, or 0. 
If the base is between 2 and 36, then the string is interpreted according to base. 
But if base is 0, then special rules come into play. If the first digit is 0 and the character which follows it is not 'x' or 'X', 
then the number is interpreted as if base were specified as 8. 
If the first digit is 0 and the character which follows is 'x' or 'X', 
then the '0x' or '0X' is ignored as input and the remainder of the number is interpreted as if base had been 16. 
Otherwise, it is interpreted as if base were 10.

## Ref
- [The CString Class - Beginning Visual C++ 2013](https://www.oreilly.com/library/view/ivor-hortons-beginning/9781118845776)
- [CString Management](http://www.flounder.com/cstring.htm)
- [Convert a string to double](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/atof-atof-l-wtof-wtof-l?view=msvc-170)
