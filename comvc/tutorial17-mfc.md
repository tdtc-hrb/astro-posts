---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Complete this project - Serialization"
description: ""
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The project requires the following articles:
- [Serialization class](https://tdtc-hrb.github.io/com-vc/posts/tutorial12-mfc)
- [Constructors and member initializer lists](https://tdtc-hrb.github.io/com-vc/posts/tutorial13-mfc)
- [ListBox and Edit Control](https://tdtc-hrb.github.io/com-vc/posts/tutorial14-mfc)
- [Collection Serialization](https://tdtc-hrb.github.io/com-vc/posts/tutorial15-mfc)
- [List Control - Report View](https://tdtc-hrb.github.io/com-vc/posts/tutorial16-mfc)

### Opening a List
```
    CFile fleConns;
    CFileFind fndFile;
    CString strFilename = _T("conns.str");

    // Look for the conns.str file
    BOOL exists = fndFile.FindFile(strFilename);

    if( exists == TRUE )
    {
        // If the file exists, open it and fill the controls with it
        fleConns.Open(strFilename, CFile::modeRead);
        // Create a CArchive object to receive the collection
        CArchive arc(&fleConns, CArchive::load);
        // Pass the CArchive object to the Serialize() function of this application
        Serialize(arc);

        // Close the archive
        arc.Close();
        // Close the file stream
        fleConns.Close();

        // Behave as if the user had just clicked the "Get Data" button
        OnBnClickedButton1();
    }
```
- [ObjArraySerialDemo.zip](https://pan.baidu.com/s/1U3j5izzjRN_l6svOd4JGOA?pwd=4iiu)
> This is an addition based on the CollSerialDemo.zip.
