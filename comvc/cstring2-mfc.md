---
layout: ../../layouts/MarkdownPostLayout.astro
title: "The CString Class - 2"
description: "char and CString"
date: 2025-12-03
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The first thing you have to understand about a CString is that it is a special C++ object which contains three values: 
- a pointer to a buffer, 
- a count of the valid characters in the buffer, 
- a buffer length. 

The count of the number of characters can be any size from 0 up to the maximum length of the buffer minus one (for the NUL byte). 
The character count and buffer length are cleverly hidden.

### Converting between char * (TCHAR *) and CString
```
CString graycat = CString(_T("Gray")) + _T("Cat");
```

### char * (TCHAR *) to CString
> *Note that CStringA and CStringW are not available in VS6, only in VS2002+ versions!

```
TCHAR * p = _T("Gray");
CString s(p);
p = _T("Cat");
s += p;
```

## CString to char */TCHAR * 
- I: Casting to LPCTSTR
- II: Using GetBuffer
- III: Interfacing to a control

### Casting to LPCTSTR
The operator LPCTSTR (or more specifically, the operator (const TCHAR *), is overloaded for CString. 
The definition of the operator is to return the address of the buffer. 
Thus, if you need a string pointer to the CString you can do something like
```
CString s("GrayCat");

LPCTSTR p =  s;
```

Most kernel APIs want LPCTSTR parameters. 
Because the (LPCTSTR) operator is defined for CString, the compiler will automatically invoke the conversion. 
Given a definition of the form
```
WINAPI BOOL SomeAPI(LPCTSTR);
```
This can be called by doing
```
CString s = _T("Some string value");
if(SomeAPI(s)) {
    // some code here
}
```

### Using GetBuffer
A special method is available for a CString if you need to modify it. 
This is the operation GetBuffer. What this does is return to you a pointer to the buffer which is considered writeable. 
If you are only going to change characters or shorten the string, you are now free to do so:
```
CString s(_T("File.ext"));

LPTSTR p = s.GetBuffer();

LPTSTR dot = strchr(p, '.'); // OK, should have used s.Find...

if(p != NULL)

    *p = _T('\0');

s.ReleaseBuffer();
```
This is the first and simplest use of GetBuffer. 
You don't supply an argument, so the default of 0 is used, which means "give me a pointer to the string; 
I promise to not extend the string". When you call ReleaseBuffer, the actual length of the string is recomputed and stored in the CString. 
Within the scope of a GetBuffer/ReleaseBuffer sequene, and I emphasize this: 
You Must Not, Ever, Use Any Method Of CString on the CString whose buffer you have! 
The reason for this is that the integrity of the CString object is not guaranteed until the ReleaseBuffer is called. 
Study the code below:
```
CString s(...);

LPTSTR p = s.GetBuffer();

//... lots of things happen via the pointer p

int n = s.GetLength(); // BAD!!!!! PROBABLY WILL GIVE WRONG ANSWER!!!

s.TrimRight();         // BAD!!!!! NO GUARANTEE IT WILL WORK!!!!

s.ReleaseBuffer();     // Things are now OK

int m = s.GetLength(); // This is guaranteed to be correct

s.TrimRight();         // Will work correctly
```

### Interfacing to a control
A very common operation is to pass a CString value in to a control, for example, a CTreeCtrl. 
While MFC provides a number of convenient overloads for the operation, but in the most general situation you use the "raw" form of the update, 
and therefore you need to store a pointer to a string in the TVITEM which is included within the TVINSERTITEMSTRUCT:
```
TVINSERTITEMSTRUCT tvi;

CString s;

// ... assign something to s

tvi.item.pszText = s; // Compiler yells at you here

// ... other stuff

HTREEITEM ti = c_MyTree.InsertItem(&tvi);
```
Now why did the compiler complain? It looks like a perfectly good assignment! 
But in fact if you look at the structure, you will see that the member is declared in the TVITEM structure as shown below:
```
LPTSTR pszText;
int cchTextMax;
```
Therefore, the assignment is not assigning to an LPCTSTR and the compiler has no idea how to cast the right hand side of the assignment to an LPTSTR.
OK, you say, I can deal with that, and you write
```
tvi.item.pszText = (LPCTSTR)s; // compiler still complains!
```

Why not just declare the member as an LPCTSTR? Because the structure is used both for reading and writing to the control. 
When you are writing to the control, 
the text pointer is actually treated as an LPCTSTR but when you are reading from the control you need a writeable string. 
The structure cannot distinguish its use for input from its use for output.

Therefore, you will often find in my code something that looks like
```
tvi.item.pszText = (LPTSTR)(LPCTSTR)s;
```
This casts the CString to an LPCTSTR, thus giving me that address of the string, which I then force to be an LPTSTR so I can assign it. 
Note that this is valid only if you are using the value as data to a Set or Insert style method! 
You cannot do this when you are trying to retrieve data!

You need a slightly different method when you are trying to retrieve data, such as the value stored in a control. 
For example, for a CTreeCtrl using the GetItem method. Here, I want to get the text of the item. I know that the text is no more than MY_LIMIT in size. 
Therefore, I can write something like 
```
TVITEM tvi;

// ... assorted initialization of other fields of tvi

tvi.pszText = s.GetBuffer(MY_LIMIT);

tvi.cchTextMax = MY_LIMIT;

c_MyTree.GetItem(&tvi);

s.ReleaseBuffer();
```
Note that the code above works for any type of Set method also, 
but is not needed because for a Set-type method (including Insert) you are not writing the string. 
But when you are writing the CString you need to make sure the buffer is writeable. 
That's what the GetBuffer does. Again, note that once you have done the GetBuffer call, 
you must not do anything else to the CString until the ReleaseBuffer call. 

## Ref
- [CString Management](http://www.flounder.com/cstring.htm)
