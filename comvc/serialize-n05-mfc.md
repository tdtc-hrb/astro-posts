---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Complete this project - Serialization"
description: ""
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
The project requires the following articles:
- [Serialization class](https://tdtc-hrb.github.io/com-vc/posts/serialize-n01-mfc)
- [Constructors and member initializer lists](https://tdtc-hrb.github.io/com-vc/posts/serialize-n02-mfc)
- [ListBox and Edit Control](https://tdtc-hrb.github.io/com-vc/posts/ctrl09-mfc)
- [Collection Serialization](https://tdtc-hrb.github.io/com-vc/posts/serialize-n03-mfc)
- [List Control - Report View](https://tdtc-hrb.github.io/com-vc/posts/serialize-n04-mfc)

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
- [ObjArraySerialDemo.zip](https://mega.nz/file/TY8jhJJT#dV19QLuCJHlKpuGAYInCziVp_pHo5_szLOZr2YUuKFY)
> This is an addition based on the [CollSerialDemo.zip](https://mega.nz/file/aQE3FQpY#JarPutLeKjGr-Q66wqgkKEL7CGpCrMSLMa-DOBzlZao).
