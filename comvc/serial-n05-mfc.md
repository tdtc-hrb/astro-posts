---
layout: ../../layouts/MarkdownPostLayout.astro
title: "6.1.1 Opening, Closing, and Creating Files"
description: "The CFile Class - MFC"
date: 2025-10-31
author: Jeff Prosise
tags: ["Microsoft Foundation Class"]
---
Files can be opened with <i>CFile</i> in either of two ways. 
The first option is to construct an uninitialized <i>CFile</i> object and call <i>CFile::Open</i>. 
The following code fragment uses this technique to open a file named File.txt with read/write access. 
Because no path name is provided in the function's first parameter, <i>Open</i> will fail unless the file 
is located in the current directory:
```
CFile file;
file.Open (_T ("File.txt"), CFile::modeReadWrite);
```
<i>CFile::Open</i> returns a BOOL indicating whether the operation was successful. 
The following example uses that return value to verify that the file was successfully opened:
```
CFile file;
    if (file.Open (_T ("File.txt"), CFile::modeReadWrite)) {
        // It worked!
}
```
A nonzero return value means the file was opened; 0 means it wasn't. 
If <i>CFile::Open</i> returns 0 and you want to know why the call failed, 
create a <i>CFileException</i> object and pass its address to <i>Open</i> in the third parameter:
```
CFile file;
CFileException e;
if (file.Open (_T ("File.txt"), CFile::modeReadWrite, &e)) {
    // It worked!
}
else {
    // Open failed. Tell the user why.
    e.ReportError ();
}
```
If Open fails, it initializes the <i>CFileException</i> object with information describing the nature of the failure. 
ReportError displays an error message based on that information. 
You can find out what caused the failure by examining the <i>CFileException</i>'s public m_cause data member. 
The documentation for <i>CFileException</i> contains a complete list of error codes.
The second option is to open the file using <i>CFile</i>'s constructor. 
Rather than construct an empty <i>CFile</i> object and call <i>Open</i>, 
you can create a <i>CFile</i> object and open a file in one step like this:
```
CFile file (_T ("File.txt"), CFile::modeReadWrite);
```
If the file can't be opened, <i>CFile</i>'s constructor throws a <i>CFileException</i>. 
Therefore, code that opens files using <i>CFile::CFile</i> normally uses try and catch blocks to trap errors:
```
try {
    CFile file (_T ("File.txt"), CFile::modeReadWrite);
}
catch (CFileException* e) {
    // Something went wrong.
    e->ReportError ();
    e->Delete ();
}
```
It's up to you to delete the <i>CFileException</i> objects MFC throws to you. 
That's why this example calls Delete on the exception object after processing the exception. 
The only time you don't want to call Delete is the rare occasion when you use throw to rethrow the exception. 
To create a new file rather than open an existing one, include a <i>CFile::modeCreate</i> flag 
in the second parameter to <i>CFile::Open</i> or the <i>CFile</i> constructor:
```
CFile file (_T ("File.txt"), CFile::modeReadWrite | CFile::modeCreate);
```
If a file created this way already exists, its length is truncated to 0. 
To create the file if it doesn't exist or to open it without truncating it if it does exist, 
include a <i>CFile::modeNoTruncate</i> flag as well:
```
CFile file (_T ("File.txt"), CFile::modeReadWrite | CFile::modeCreate | CFile::modeNoTruncate);
```
An open performed this way almost always succeeds because the file is automatically created 
for you if it doesn't already exist. By default, a file opened with <i>CFile::Open</i> or <i>CFile::CFile</i> 
is opened for exclusive access, which means that no one else can open the file. 
If desired, you can specify a sharing mode when opening the file to explicitly grant others permission to access the file, too. 
Here are the four sharing modes that you can choose from:

|Sharing Mode| Description|
|-|-|
|CFile::shareDenyNone| Opens the file nonexclusively|
|CFile::shareDenyRead| Denies read access to other parties|
|CFile::shareDenyWrite| Denies write access to other parties|
|CFile::shareExclusive| Denies both read and write access to other parties(default)|

In addition, you can specify any one of the following three types of read/write access:

|Access Mode| Description|
|-|-|
|CFile::modeReadWrite| Requests read and write access|
|CFile::modeRead| Requests read access only|
|CFile::modeWrite| Requests write access only|

A common use for these options is to allow any number of clients to 
open a file for reading but to deny any client the ability to write to it:
```
CFile file (_T ("File.txt"), CFile::modeRead ¦ CFile::shareDenyWrite);
```
If the file is already open for writing when this statement is executed, 
the call will fail and <i>CFile</i> will throw a <i>CFileException</i> with <i>m_cause</i> 
equal to <i>CFileException::sharingViolation</i>.
An open file can be closed in two ways. To close a file explicitly, call <i>CFile::Close</i> 
on the corresponding <i>CFile</i> object:
```
file.Close ();
```
If you'd prefer, you can let <i>CFile</i>'s destructor close the file for you. 
The class destructor calls Close if the file hasn't been closed already. 
This means that a <i>CFile</i> object created on the stack will be closed automatically when it goes out of scope. 
In the following example, the file is closed the moment the brace marking the end of the try block is reached:
```
try {
    CFile file (_T ("File.txt"), CFile::modeReadWrite);
    // CFile::~CFile closes the file.
}
```
One reason programmers sometimes call Close explicitly is to close the file that is currently open so that they can open 
another file using the same <i>CFile</i> object

## Ref
- [6.1. The CFile Class(P335) - Programming Windows With MFC](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
