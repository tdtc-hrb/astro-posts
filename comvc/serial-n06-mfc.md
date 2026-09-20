---
layout: ../../layouts/MarkdownPostLayout.astro
title: "6.1.2. Reading and Writing"
description: "The CFile Class - MFC"
date: 2025-10-31
author: Jeff Prosise
tags: ["Microsoft Foundation Class"]
---
A file opened with read access can be read using <i>CFile::Read</i>. 
A file opened with write access can be written with <i>CFile::Write</i>. 
The following example allocates a 4-KB file I/O buffer and reads the file 4 KB at a time. 
Error checking is omitted for clarity.
```
BYTE buffer[0x1000];
CFile file (_T ("File.txt"), CFile::modeRead);
DWORD dwBytesRemaining = file.GetLength ();
while (dwBytesRemaining) {
    UINT nBytesRead = file.Read (buffer, sizeof (buffer));
    dwBytesRemaining -= nBytesRead;
}
```
A count of bytes remaining to be read is maintained in <i>dwBytesRemaining</i>, 
which is initialized with the file size returned by <i>CFile::GetLength</i>. 
After each call to <i>Read</i>, the number of bytes read from the file (<i>nBytesRead</i>) is subtracted from <i>dwBytesRemaining</i>. 
The while loop executes until <i>dwBytesRemaining</i> reaches 0. The following example builds on the code in the previous 
paragraph by using <i>::CharLowerBuff</i> to convert all the uppercase characters read from the file to lowercase and using
<i>CFile::Write</i> to write the converted text back to the file. Once again, error checking is omitted for clarity.
```
BYTE buffer[0x1000];
CFile file (_T ("File.txt"), CFile::modeReadWrite);
DWORD dwBytesRemaining = file.GetLength ();
while (dwBytesRemaining) {
    DWORD dwPosition = file.GetPosition ();
    UINT nBytesRead = file.Read (buffer, sizeof (buffer));
    ::CharLowerBuff ((LPTSTR)buffer, nBytesRead);
    file.Seek (dwPosition, CFile::begin);
    file.Write (buffer, nBytesRead);
    dwBytesRemaining -= nBytesRead;
}
```
This example uses the <i>CFile</i> functions <i>GetPosition</i> and <i>Seek</i> to manipulate the file pointer—the 
offset into the file at which the next read or write is performed—so that the modified data is written over the top of the original. 
<i>Seek</i>'s second parameter specifies whether the byte offset passed 
in the first parameter is relative to the beginning of the file (<i>CFile::begin</i>), 
the end ofthe file (<i>CFile::end</i>), or the current position (<i>CFile::current</i>).
To quickly seek to the beginning or end of a file, 
use <i>CFile::SeekToBegin</i> or <i>CFile::SeekToEnd</i>. <i>Read</i>, <i>Write</i>, and other <i>CFile</i> functions throw a <i>CFileException</i> 
if an error occurs during a file I/O operation. <i>CFileException::m_cause</i> tells you why the error occurred. 
For example, attempting to write to a disk that is full throws a <i>CFileException</i> with <i>m_cause</i> equal to <i>CFileException::diskFull</i>. 
Attempting to read beyond the end of a file throws a <i>CFileException</i> with m_cause equal to <i>CFileException::endOfFile</i>. 
Here's how the routine that converts all the lowercase text in a file to uppercase might look with error checking code included:
```
BYTE buffer[0x1000];
try {
    CFile file (_T ("File.txt"), CFile::modeReadWrite);
    DWORD dwBytesRemaining = file.GetLength ();
    while (dwBytesRemaining) {
        DWORD dwPosition = file.GetPosition ();
        UINT nBytesRead = file.Read (buffer, sizeof (buffer));
        ::CharLowerBuff ((LPTSTR)buffer, nBytesRead);
        file.Seek (dwPosition, CFile::begin);
        file.Write (buffer, nBytesRead);
        dwBytesRemaining -= nBytesRead;
    }
}
catch (CFileException* e) {
    e->ReportError ();
    e->Delete ();
}
```
If you don't catch exceptions thrown by <i>CFile</i> member functions, MFC will catch them for you. 
MFC's default handler for unprocessed exceptions uses ReportError to display a descriptive error message. 
Normally, however, it's in your best interest to catch file I/O exceptions to prevent critical sections 
of code from being skipped.

## Ref
- [6.1. The CFile Class(P335) - Programming Windows With MFC](https://assets.ctfassets.net/9pcn2syx7zns/6ejGpuR3LJdenVQWDCe23W/d152db4718309d396d07aa8b444a541e/mfc2.pdf)
