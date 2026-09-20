---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Collection Serialization"
description: "database connection string"
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---

### Usage Collection Serialization
first declare a member variable of type CObArray.

To serialize a CObArray collection in your project, 
all of you have to do is to call the CObArray::Serialize() member function. 
Everything else would be handled behind the scenes.
#### define
```
private:
    CObArray ListOfConnStrings;
```
#### impl
On the main menu, click Project -> Class Wizard...    
In the Class Name, make sure CMFCApplication1Dlg is selected.    
Click the Virtual Functions tab    
In the Virtual Functions list, scroll down and double-click Serialize    
Click Edit Code and implement the member function as follows:
```
void CMFCApplication1Dlg::Serialize(CArchive &ar)
{
    if (ar.IsStoring())
    {   // storing code
    }
    else
    {   // loading code
    }
    ListOfConnStrings.Serialize(ar);
}
```

## project
- Editor
- Event
### Editor
|Server|DB|User|Pwd|Type|
|-|-|-|-|-|
|.|c:\\fde.mdb|admin|wwsrts12|MS-Access|
|serverdb|pubs|sa|qwerty|MSSQL|
|192.168.1.107|employees|DBA|xb12345|MySQL|

#### add dialog
![IDC_DIALOGBAR](https://github.com/tdtc-hrb/csdn/raw/master/images/dialog_bar-res.png)

and set:
- Style: Popup
- System Menu: True
- Title Bar: True
#### add class
![Add a class from the control](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class1-ctl.png)
#### [Add Variable](https://tdtc-hrb.github.io/com-vc/posts/ctrl09-mfc)

### event
Add event handlers to the main dialog box.
#### New
```
    int iCurSel = 0;
    iCurSel = m_Types.GetCurSel();

    CConnEditorDlg dlg;

    if (dlg.DoModal() == IDOK)
    {
        CConnectString *connStr = new CConnectString(dlg.m_Server,
            dlg.m_Db, dlg.m_User,
            dlg.m_Pwd, iCurSel);
        // Add that new connect string to the collection
        ListOfConnStrings.Add(connStr);
    }
```
#### Save
```
    CFile fileConnStrs;
    CString strFilename = _T("conns.str");

    fileConnStrs.Open(strFilename, CFile::modeCreate | CFile::modeWrite);
    CArchive arc(&fileConnStrs, CArchive::store);
    Serialize(arc);

    arc.Close();
    fileConnStrs.Close();
```

## Ref
- [Fundamentals of Serialization](https://www.functionx.com/visualc/fileprocessing/serialization.htm)
- [Serialization class](https://tdtc-hrb.github.io/com-vc/posts/serialize-n01-mfc)
- [CollSerialDemo.zip](https://mega.nz/file/aQE3FQpY#JarPutLeKjGr-Q66wqgkKEL7CGpCrMSLMa-DOBzlZao)
