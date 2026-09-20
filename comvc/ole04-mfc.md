---
layout: ../../layouts/MarkdownPostLayout.astro
title: "COleDataSource - OLE in MFC"
description: "wrapper for implementing IDataObject(works similar to how data is provided on the clipboard)"
date: 2025-12-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Listing 12-1 shows the definition of COleDataSource from AFXOLE.H:

Listing 12-1. The COleDataSource class
```
/*============================================================================*/
// COleDataSource -- wrapper for implementing IDataObject
//  (works similar to how data is provided on the clipboard)

struct AFX_DATACACHE_ENTRY;
class COleDropSource;

class COleDataSource : public CCmdTarget
{
// Constructors
public:
	COleDataSource();

// Operations
	void Empty();   // empty cache (similar to ::EmptyClipboard)

	// CacheData & DelayRenderData operations similar to ::SetClipboardData
	void CacheGlobalData(CLIPFORMAT cfFormat, HGLOBAL hGlobal,
		LPFORMATETC lpFormatEtc = NULL);    // for HGLOBAL based data
	void DelayRenderFileData(CLIPFORMAT cfFormat,
		LPFORMATETC lpFormatEtc = NULL);    // for CFile* based delayed render

	// Clipboard and Drag/Drop access
	DROPEFFECT DoDragDrop(
		DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
		LPCRECT lpRectStartDrag = NULL,
		COleDropSource* pDropSource = NULL);
	void SetClipboard();
	static void PASCAL FlushClipboard();
	static COleDataSource* PASCAL GetClipboardOwner();

	// Advanced: STGMEDIUM based cached data
	void CacheData(CLIPFORMAT cfFormat, LPSTGMEDIUM lpStgMedium,
		LPFORMATETC lpFormatEtc = NULL);    // for LPSTGMEDIUM based data
	// Advanced: STGMEDIUM or HGLOBAL based delayed render
	void DelayRenderData(CLIPFORMAT cfFormat, LPFORMATETC lpFormatEtc = NULL);

	// Advanced: support for SetData in COleServerItem
	//  (not generally useful for clipboard or drag/drop operations)
	void DelaySetData(CLIPFORMAT cfFormat, LPFORMATETC lpFormatEtc = NULL);

// Overidables
	virtual BOOL OnRenderGlobalData(LPFORMATETC lpFormatEtc, HGLOBAL* phGlobal);
	virtual BOOL OnRenderFileData(LPFORMATETC lpFormatEtc, CFile* pFile);
	virtual BOOL OnRenderData(LPFORMATETC lpFormatEtc, LPSTGMEDIUM lpStgMedium);
		// OnRenderFileData and OnRenderGlobalData are called by
		//  the default implementation of OnRenderData.

	virtual BOOL OnSetData(LPFORMATETC lpFormatEtc, LPSTGMEDIUM lpStgMedium,
		BOOL bRelease);
		// used only in COleServerItem implementation

// Implementation
public:
	virtual ~COleDataSource();
#ifdef _DEBUG
	virtual void AssertValid() const;
	virtual void Dump(CDumpContext& dc) const;
#endif

protected:
	AFX_DATACACHE_ENTRY* m_pDataCache;  // data cache itself
	UINT m_nMaxSize;    // current allocated size
	UINT m_nSize;       // current size of the cache
	UINT m_nGrowBy;     // number of cache elements to grow by for new allocs

	AFX_DATACACHE_ENTRY* Lookup(
		LPFORMATETC lpFormatEtc, DATADIR nDataDir) const;
	AFX_DATACACHE_ENTRY* GetCacheEntry(
		LPFORMATETC lpFormatEtc, DATADIR nDataDir);

// Interface Maps
public:
	BEGIN_INTERFACE_PART(DataObject, IDataObject)
		INIT_INTERFACE_PART(COleDataSource, DataObject)
		STDMETHOD(GetData)(LPFORMATETC, LPSTGMEDIUM);
		STDMETHOD(GetDataHere)(LPFORMATETC, LPSTGMEDIUM);
		STDMETHOD(QueryGetData)(LPFORMATETC);
		STDMETHOD(GetCanonicalFormatEtc)(LPFORMATETC, LPFORMATETC);
		STDMETHOD(SetData)(LPFORMATETC, LPSTGMEDIUM, BOOL);
		STDMETHOD(EnumFormatEtc)(DWORD, LPENUMFORMATETC*);
		STDMETHOD(DAdvise)(LPFORMATETC, DWORD, LPADVISESINK, LPDWORD);
		STDMETHOD(DUnadvise)(DWORD);
		STDMETHOD(EnumDAdvise)(LPENUMSTATDATA*);
	END_INTERFACE_PART(DataObject)

	DECLARE_INTERFACE_MAP()

	friend class COleServerItem;
};
```
    As you can tell from the header file, COleDataSource is designed specifically to support Clipboard and drag-and-drop 
transfers (notice the "SetClipboard()" and "DoDragDrop()" function). We'll skip the drag-and-drop support for the moment 
and concertrate on the Clipboard support.
    Recall how the OLE Clipboard works. When a data producer decides to put data on the OLE Clipboard, it simply has to 
implement IDataObject and use OleSetClipboard() to place the IDataObject on the Clipboard.
	COleDataSource obviously implements IDataObject: notice the Interface map macros. Also notice that COleDataSource has 
a member function called SetClipboard(). SetClipboard() simple places the COleDataSource's IDataObject Interface pointer 
by calling the global API function ::OleSetClipboard() to put it on the Clipboard. That part is simple. However, there's 
still the issue of getting the data into the COleDataSource. That's done using COleDataSource's caching function, CacheData() 
and CacheGlobalData().

### Caching the Data
The idea behind caching the data is that COleDataSource keeps the data around so that it can render the data immediately upon 
demand. That implies that the COleDataSource utilizes some sort of data structure to manage data that's been cached. In fact, 
COleDataSource uses a structure called AFX_DATACACHE_ENTRY to store the cached data. Here's the definition of the AFX_DATACACHE_ENTRY: 
```
struct AFX_DATACACHE_ENTRY 
{
    FORMATETC m_formatEtc;
	STGMEDIUM m_stgMedium;
	DATADIR m_nDataDir;
}
```
    There's nothing too complicated here. The structure contains FORMATETC and STGMEDIUM members as well as a DATADIR member. 
You've already seen the FORMATETC and the STGMEDIUM structures. DATADIR is just an enumeration that establishes the direction 
of a data transfer. It's defined in OBJIDL.H:
```
enum tagDATADIR {
    DATADIR_GET = 1,
	DATADIR_SET = 2
}
```
    The DATADIR field is used during delayed rendering, as we'll see shortly.
	Take another look at COleDataSource; you'll see that it maintains an array of these AFX_DATACACHE_ENTRY structures. 
The m_pDataCache member points to the first element in this array. CacheData() and CacheGlobalData() simply add elements 
to this array.

### Inside CacheData() and CacheGlobalData()
COleDataSource::CacheData() and COleDataSource::CacheGlobalData() are similar function. Both store data in a COleDataSource 
object so that it may be rendered immediately. CacheData() stores data in a STGMEDIUM structure, while CacheGlobalData() 
is a shortcut for caching data in an HGLOBAL. Let's look at the more general function, CacheData(), to see how COleDataSource 
caches data.
    When an application caches data using CacheData(), the application is responsible for packaging the STGMEDIUM structure. 
In addition, the application has to at least provide a Clipboard format (one of those CF_... constants) indicating the Clipboard 
format, then the application wants to define the data using more than the Clipboard format, then the application has to fill in a 
FORMATETC structure and send that along as part of the CacheData() function.
    Notice that COleDataSource::CacheData() includes a FORMATETC structure in the parameter list. This is an optional parameter: 
the caller can pass just the CLIPFORMAT if it wants to. However, the AFX_DATACACHE_ENTRY structure needs an entire FORMATETC structure-
not just a CLIPFORMAT. If the caller doesn't pass in a FORMATETC structure, CacheData() fills the structure using _AfxFillFormatEtc(). 
_AfxFillFormatEtc() fills the FORMATETC structure using these default values:
```
lpFormatEtc->cfFormat = <the CF_ format provided by the caller>;
lpFormatEtc->ptd = NULL;
lpFormatEtc->dwAspect = DVASPECT_CONTENT;
lpFormatEtc->lindex = -1;
lpFormatEtc->tymed = (TYMED)-1
```
    Finally, CacheData() sets the tymed field of the FORMATETC structure to the tymed field of the STGMEDIUM structure 
passed in by the caller.
    Once the framework has a viable FORMATETC, CacheData() makes a place for the data in the cache by calling 
COleDataSource::GetCacheEntry(). GetCacheEntry() uses the COleDataSource Lookup() to walk the array of AFX_DATACACHE_ENTRY 
structures in an effort to find an entry that has the same FORMATETC structure as the one the caller is trying to add. 
If it's already there, Lookup() returns that one. Otherwise, it allocates a new AFX_DATACACHE_ENTRY for the cache array and 
returns a pointer to the new AFX_DATACACHE_ENTRY. This way, there's no ambiguity regarding the COleDataSource's cache entries. 
There is at most only one entry for each format described in the FORMATETC structure. Once GetCacheEntry() has a pointer to a 
valid AFX_DATACACHE_ENTRY, the GetCacheEntry() fills the structure. Of course, if there's already data in the structure, GetCacheEntry() 
has to release it first (using ReleaseStgMedium()). Once the data's cached in the COleDataSource, data consumers can retrieve it by first 
getting the IDataObject Interface pointer and then calling GetData(). (We'll see exactly how GetData() works shortly.)

### Inside Delayed Rendering
When using delayed rendering, data sources are not required to render the data until the very last minute. Delayed rendering 
happens in much the same way as caching data. Delayed rendering uses the same AFX_DATACACHE_ENTRY but in a slightly different way. 
    Like CacheData(), DelayRenderData() takes a CLIPFORMAT and a FORMATETC. However, DelayRenderData() doesn't take a STGMEDIUM. 
Remember, in this situation, the data producer doesn't have to cough up the data until absolutely necessary, so there's no need 
for a STGMEDIUM structure.
    Just as CacheData() does, DelayRenderData() calls _AfxFillFormatEtc(). At that point, DelayRenderData() uses GetCacheEntry() 
to either reuse a cache entry (if one already exists for a specific FORMATETC structure) or to create a new one if necessary. 
However, instead of adding a STGMEDIUM structure) or to create a new one if necessary. However, instead of adding a STGMEDIUM 
to the cache, DelayRenderData() zeroes out the STGMEDIUM area of the AFX_DATACACHE_ENTRY. That's how COleDataSource::GetData() 
knows whether to render the data from the cache directly or to call one of the COleDataSource::OnRenderData() variants.
    As you can see, the decision as to when to render the data is made up front. Both CacheData() and DelayRenderData() place an 
AFX_DATACACHE_ENTRY in the COleDataSource. However, while CacheData() stores the STGMEDIUM structure and the FORMATETC structure, 
DelayRenderData() stores only the FORMATETC structure.
    COleDataSource uses this information when responding to IDataObject::GetData().
### Responding to GetData()
COleDataSource is a fully qualified COM object that implements IDataObject. When clients pull the data down from the Clipboard, 
COleDataSource's IDataObject eventually has to respond to IDataObject::GetData().
    COleDataSource's implementation is fairly straightforward. If you look in the MFC source code, you'll see a file 
called OLEDOBJ2.CPP. In it you'll find the code for COleDataSource's IDataObject::GetData() function. Of course, COleDataObject 
implements the interface using the same mechanism as all other MFC COM objects: using interface maps. The actual function is 
COleDataSource::XDataObject::GetData(). This function walks COleDataSource's data cache looking for an entry that matches 
the requested format. If the data cache has data in the STGMEDIUM field, then GetData() returns the data to the caller using an 
MFC helper function called _AfxCopyStgMedium().
    _AfxCopyStgMedium() is a long function (about 160 lines). Whoa! It's very much like the API function ReleaseStgMedium(). 
_AfxCopyStgMedium() is a big switch statement that switches on the type of medium being copied. For example, if the type of 
medium being copied is an HGLOBAL, _AfxCopyStgMedium() uses the API function CopyGlobalMemory() to make a copy of the data.
    If the entry was placed in the cache using delayed rendering, then the data cache entry's STGMEDIUM is empty. In this case, 
GetData() calls COleDataSource::OnRenderData(), at which point the data producer is required to pay up.
### Other IDataObject Interface Functions
#### GetDataHere()
IDataObject::GetDataHere() is just like IDataObject::GetData() except the caller supplies the medium(intead of the object). 
COleDataSource's implementation uses the Lookup() function to find the appropriate entry in the cache. If Lookup() produces 
an entry, GetDataHere() uses _AfxCopyStgMedium() to copy the data from the cache entry to the STGMEDIUM provided by the caller. 
#### QueryGetData()
QueryGetData() is simple: it just uses COleDataSource::Lookup() to see if a requested format is in the cache.
#### GetCanonicalFormatEtc()
There is no canonical FORMATETC for MFC's COleDataSource. Because MFC supports the target device (ptd) for server metafile format, 
all members of the FORMATETC are significant.
#### SetData()
SetData() looks in the cache for an entry matching the FORMATETC specified by the caller. If it can find an entry, SetData() calls 
the virtual function OnSetData(). MFC's default implementation of OnSetData() does nothing. To enable COleDataSource's SetData() 
function, you need to override OnSetData().
#### EnumFormatEtc()
Data consumers that want to learn all the formats supplied by a particular data object call EnumFormatEtc(). To accomplish this, 
COleDataSource supplies an enumerator for the entries in its cache.
    COM defines several enumerator interfaces, including IEnum VARIANT, IEnumUnknown, and IEnumFORMATETC. The semantics of enumerating 
a collection is almost always the same, regardless of the elements involved. Therefore, each of the COM enumerators follows the same 
form. That is, each enumerator has the same four Functions: Next(), Skip(), Reset(), and Clone(). MFC has a helper class defined within 
OLEIMPL2.H that defines a generic enumerator class called CEnumArray. CEnumArray is another COM object that implements an interface 
called IEnumVOID. IEnumVOID isn't a standard COM interface: it's defined by MFC in OLEIMPL.H. IEnumVOID enumerates a collection of 
void pointers. CEnumArray maintains a collection of some arbitrary type and provides all the functionality necessary to enumerate the collection. 
    Inside OLEDOBJ2.CPP, MFC defines a class called CEnumFormatEtc, which is derived from CEnumArray. CEnumFormatEtc implements an enumerator 
COleDataSource's data cache. COleDataSource implements EnumFormatEtc() using CEnumFormatEtc. EnumFormatEtc() starts declaring an instance of 
CEnumFormatEtc, walking the data cache (the array of AFX_DATACACHE_ENTRY structures), and adding each FORMATETC to the list maintained by 
CEnumFormatEtc. Then COleDataSource::EnumFormatEtc() hands the enumerator interface pointer back to the client.
#### DAdvise(), DUnadvise(), and EnumDAdvise()
There's not much to say here. COleDataSource is meant to manage Clipboard and drag-and-drop transfers. Each of the aadvise-loop functions 
returns OLE_E_ADVISENOTSUPPORTED.

## Ref
- COleDataSource - Excerpt from "MFC Internals"
