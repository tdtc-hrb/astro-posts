---
layout: ../../layouts/MarkdownPostLayout.astro
title: "COleDataObject - OLE in MFC"
description: "simple wrapper for IDataObject"
date: 2025-12-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
COleDataObject is usually used on the receiving end of a data transfer. While the COleDataObject class actually 
implements IDataObject, COleDataObject is merely a wrapper around an existing IDataObject pointer. Listing 12-2 
shows the definition of COleDataObject from the file AFXOLE.H.

Listing 12-2. The COleDataObject class
```
/*============================================================================*/
// COleDataObject -- simple wrapper for IDataObject

class COleDataObject
{
// Constructors
public:
	COleDataObject();

// Operations
	void Attach(LPDATAOBJECT lpDataObject, BOOL bAutoRelease = TRUE);
	LPDATAOBJECT Detach();  // detach and get ownership of m_lpDataObject
	void Release(); // detach and Release ownership of m_lpDataObject
	BOOL AttachClipboard(); // attach to current clipboard object

// Attributes
	void BeginEnumFormats();
	BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
	CFile* GetFileData(CLIPFORMAT cfFormat, LPFORMATETC lpFormatEtc = NULL);
	HGLOBAL GetGlobalData(CLIPFORMAT cfFormat, LPFORMATETC lpFormatEtc = NULL);
	BOOL GetData(CLIPFORMAT cfFormat, LPSTGMEDIUM lpStgMedium,
		LPFORMATETC lpFormatEtc = NULL);
	BOOL IsDataAvailable(CLIPFORMAT cfFormat, LPFORMATETC lpFormatEtc = NULL);

// Implementation
public:
	LPDATAOBJECT m_lpDataObject;
	LPENUMFORMATETC m_lpEnumerator;
	~COleDataObject();

	// advanced use and implementation
	LPDATAOBJECT GetIDataObject(BOOL bAddRef);
	void EnsureClipboardObject();
	BOOL m_bClipboard;      // TRUE if represents the Win32 clipboard

protected:
	BOOL m_bAutoRelease;    // TRUE if destructor should call Release

private:
	// Disable the copy constructor and assignment by default so you will get
	//   compiler errors instead of unexpected behaviour if you pass objects
	//   by value or assign objects.
	COleDataObject(const COleDataObject&);  // no implementation
	void operator=(const COleDataObject&);  // no implementation
};
```
    Here's a rundown of the most important COleDataObject functions: Attach(), AttachClipboard(), 
BeginEnumFormats/GetNextFormat(), and the GetData...() functions.

### Attach() and Detach()
Recall that COleDataObject is merely a wrapper for an existing IDataObject pointer. Notice that COleDataObject 
maintains an IDataObject member, called m_lpDataObject. Like other MFC classes that wrap native things such as 
handles, COleDataObject has a function for attching an existing interface pointer to the class. That function 
is called Attach(). Attach() takes two parameters: a pointer to an IDataObject interface and a flag indicating 
whether or not the interface pointer should be released when the COleDataObject object is destroyed. 
COleDataObject::Attach() releases m_lpDataObject (if it is valid and if m_bAutoRelease is TRUE), then sets the 
m_lpDataObject and the m_bAutoRelease members to the new values provided by parameters.
    There's also a complementary function called Detach() that sets m_lpDataObject to NULL. COleDataObject::Release() 
releases the IDataObject pointer --- if m_bAutoRelease is set to TRUE.

### AttachClipboard() and EnsureClipboardData()
The documentation provided by Microsoft indicates that if you want to retrieve data from the Clipboard, 
you should call COleDataObject::AttachClipboard(). Yes, AttachClipboard() is the member you should call. 
However, AttachClipboard() simply sets COleDataObject's m_bClipboard flag to TRUE. The real action occurs 
in COleDataObject::EnsureClipboardData().
  EnsureClipboardData() is a wrapper for the API function OleGetClipboard(). If the m_bClipboard flag(the one 
set by AttachClipboard()) is TRUE, then OleGetClipboard() pulls down a copy of the OLE Clipboard's IDataObject 
pointer and wraps the pointer using friendly MFC class member function provided by COleDataObject.
  MFC accesses the Clipboard this way as an optimization. You'll see why when examining COleDataObject::IsDataAvailable().

### Determining Available Data
COleDataObject has a function called IsDataAvailable() that takes a CLIPFORMAT and a FORMATETC as its parameters. 
IsDataAvailable() checks the m_bClipboard flag. If the flag is FALSE, then IsDataAvailable() calls the IDataObject 
interface's QueryGetData() to find out if the data is available in the given format.
    If m_bClipboard is TRUE, then there's probably data on the Clipboard (that is, the user has called AttachClipboard()). 
IsDataAvailable simple defers to the standard Windows API functions ::IsClipboardFormatAvailable(), which is often more 
efficient and reliable than calling IDataObject::QueryGetData().
    Notice that IsDataAvailable() takes a CLIPFORMAT and a FORMATETC structure. However, if the consumer has called 
AttachClipboard(), then IsDataAvailable() calls the Win32 API that accepts only a CLIPFORMAT as a parameter. What if the 
consumer is requesting data using a FORMATETC structure? The Win32 function doesn't know how to deal with a FORMATETC structure 
either. The OLE API ignores everything but the clipformat! Maybe when the Windows API is implemented on top of OLE instead 
of the other way around, this will change.

### Enumerating Formats
Recall that IDataObject has a function called EnumFormatEtc(). EnumFormatEtc() returns a pointer to an interface that enumerates 
the Clipboard formats. COleDataObject::BeginEnumFormats() starts the enumeration by retrieving the enumeration interface pointer 
from the underlying IDataObject interface. To retrieve the actual formats, clients call COleDataObject::GetNextFormat(). 
GetNextFormat() uses the enumerator passed back during the call to COleDataObject::BeginEnumFormats(), calling the enumerator's 
Next() function.

### Retrieving the Data
GetData() calls EnsureClipboardData() to get the IDataObject off the Clipboard, then defers the IDataObject pointer's GetData() 
to retrieve the data.
    COleDataObject's other GetData...() variants are GetGlobalData and GetFileData(). They work the same way as GetData(), 
except GetGlobalData() retrieves a global memory handle and GetFileData() retrieves a file handle.
    As you can see, MFC's IDataObject classes(COleDataSource and COleDataObject) wrap Clipboard data transfers very well. 
They also do a great job implementing OLE drag-and-drop. In fact, doing drag-and-drop is very similar and only takes a little 
bit more work to implement.

## Ref
- COleDataObject - Excerpt from "MFC Internals"
