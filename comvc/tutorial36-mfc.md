---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The CString Class - 3"
description: "COM and CString"
date: 2025-12-07
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

### CString to BSTR
When programming with ActiveX, you will sometimes need a value represented as a type BSTR. 
A BSTR is a counted string, a wide-character (Unicode) string on Intel platforms and can contain embedded NUL characters. 

You can convert at CString to a BSTR by calling the CString method AllocSysString: 
```
CString s;
s = ... ; // whatever
BSTR b = s.AllocSysString();
```
 The pointer b points to a newly-allocated BSTR object which is a copy of the CString, including the terminal NUL character. 
 This may now be passed to whatever interface you are calling that requires a BSTR. 
 Normally, a BSTR is disposed of by the component receiving it. If you should need to dispose of a BSTR, you must use the call 
```
::SysFreeString(b);
```
to free the string.

The story is that the decision of how to represent strings sent to ActiveX controls resulted in some serious turf wars within Microsoft. 
The Visual Basic people won, and the string type BSTR (acronym for "Basic String") was the result. 

### BSTR to CString
Since a BSTR is a counted Unicode string, you can use standard conversions to make an 8-bit CString. 
Actually, this is built-in; there are special constructors for converting ANSI strings to Unicode and vice-versa. 
You can also get BSTRs as results in a VARIANT type, which is a type returned by various COM and Automation calls.

For example, if you do, in an ANSI application, 
```
BSTR b;
b = ...; // whatever
CString s(b == NULL ? L"" : b)
```
works just fine for a single-string BSTR, 
because there is a special constructor that takes an LPCWSTR (which is what a BSTR is) and converts it to an ANSI string. 
The special test is required because a BSTR could be NULL, 
and the constructors Don't Play Well with NULL inputs (thanks to Brian Ross for pointing this out!). 
This also only works for a BSTR that contains only a single string terminated with a NUL; 
you have to do more work to convert strings that contain multiple NUL characters. 
Note that embedded NUL characters generally don't work well in CStrings and generally should be avoided.

Remember, according to the rules of C/C++, if you have an LPWSTR it will match a parameter type of LPCWSTR (it doesn't work the other way!).

In UNICODE mode, this is just the constructor 
```
CString::CString(LPCTSTR);
```
As indicated above, in ANSI mode there is a special constructor for
```
CString::CString(LPCWSTR);
```
this calls an internal function to convert the Unicode string to an ANSI string. 
(In Unicode mode there is a special constructor that takes an LPCSTR, a pointer to an 8-bit ANSI string, and widens it to a Unicode string!). 
Again, note the limitation imposed by the need to test for a BSTR value which is NULL.

There is an additional problem as pointed out above: BSTRs can contain embedded NUL characters; 
CString constructors can only handle single NUL characters in a string. 
This means that CStrings will compute the wrong length for a string which contains embedded NUL bytes. 
You need to handle this yourself. If you look at the constructors in strcore.cpp, 
you will see that they all do an lstrlen or equivalent to compute the length. 

Note that the conversion from Unicode to ANSI uses the ::WideCharToMultiByte conversion with specific arguments that you may not like. 
If you want a different conversion than the default, you have to write your own. 
If you are compiling as UNICODE, then it is a simple assignment:
```
CString convert(BSTR b)
   {
    if(b == NULL)
        return CString(_T(""));
    CString s(b); // in UNICODE mode
    return s;
   }
```
If you are in ANSI mode, you need to convert the string in a more complex fashion. 
This will accomplish it. Note that this code uses the same argument values to ::WideCharToMultiByte that the implicit constructor for CString uses, 
so you would use this technique only if you wanted to change these parameters to do the conversion in some other fashion, 
for example, specifying a different default character, a different set of flags, etc. 
```
CString convert(BSTR b)
   {
    CString s;
    if(b == NULL)
       return s; // empty for NULL BSTR
#ifdef UNICODE
    s = b;
#else
    LPSTR p = s.GetBuffer(SysStringLen(b) + 1); 
    ::WideCharToMultiByte(CP_ACP,            // ANSI Code Page
                          0,                 // no flags
                          b,                 // source widechar string
                          -1,                // assume NUL-terminated
                          p,                 // target buffer
                          SysStringLen(b)+1, // target buffer length
                          NULL,              // use system default char
                          NULL);             // don't care if default used
    s.ReleaseBuffer();
#endif
    return s;
   }
```
Note that I do not worry about what happens if the BSTR contains Unicode characters that do not map to the 8-bit character set, 
because I specify NULL as the last two parameters. This is the sort of thing you might want to change. 

### VARIANT to CString
A VARIANT is a generic parameter/return type in COM programming. 
You can write methods that return a type VARIANT, 
and which type the function returns may (and often does) depend on the input parameters to your method (for example, 
in Automation, depending on which method you call, 
IDispatch::Invoke may return (via one of its parameters) a VARIANT which holds a BYTE, a WORD, an float, a double, a date, a BSTR, 
and about three dozen other types (see the specifications of the VARIANT structure in the MSDN). 
In the example below, it is assumed that the type is known to be a variant of type BSTR, 
which means that the value is found in the string referenced by bstrVal. 
This takes advantage of the fact that there is a constructor which, in an ANSI application, 
will convert a value referenced by an LPCWCHAR to a CString (see BSTR-to-CString). 
In Unicode mode, this turns out to be the normal CString constructor. 
See the caveats about the default ::WideCharToMultibyte conversion and whether or not you find these acceptable (mostly, you will).
```
VARIANT vaData;

vaData = m_com.YourMethodHere();
ASSERT(vaData.vt == VT_BSTR);

CString strData(vaData.bstrVal);

Note that you could also make a more generic conversion routine that looked at the vt field. In this case, you might consider something like:

CString VariantToString(VARIANT * va)
   {
    CString s;
    switch(va->vt)
      { /* vt */
       case VT_BSTR:
          return CString(vaData->bstrVal);
       case VT_BSTR | VT_BYREF:
          return CString(*vaData->pbstrVal);
       case VT_I4:
          s.Format(_T("%d"), va->lVal);
          return s;
       case VT_I4 | VT_BYREF:
          s.Format(_T("%d"), *va->plVal);
       case VT_R8:
          s.Format(_T("%f"), va->dblVal);
          return s;
       ... remaining cases left as an Exercise For The Reader
       default:
          ASSERT(FALSE); // unknown VARIANT type (this ASSERT is optional)
          return CString("");
      } /* vt */
   }
```

### The ATL String Support Macros
- [Arjay](https://forums.codeguru.com/showthread.php?348238-atlconv-h-header-error!!!&p=1189478#post1189478)    
You need to use the ```USES_CONVERSION``` macro before using the convert functions.

#### [Generic Conversion Macros](https://learn.microsoft.com/en-us/cpp/mfc/tn059-using-mfc-mbcs-unicode-conversion-macros?view=msvc-170#generic-conversion-macros)
```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

#### [example](https://stackoverflow.com/a/8050301)
```
#include <atlbase.h>
#include <iostream>

int _tmain(int argc, _TCHAR* argv[])
{
	USES_CONVERSION;

	char szText[] = "Hello, world";
	LPCWSTR w = A2W(szText);
	std::wcout << w << std::endl;
	return 0;
}
```

## Ref
- [CString Management](http://www.flounder.com/cstring.htm)
