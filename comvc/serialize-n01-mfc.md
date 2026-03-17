---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Fundamentals of Serialization - MFC"
description: "Run-Time Object Model Support"
date: 2025-11-10
author: xiaobin
tags: ["Microsoft Foundation Class"]
---
Add Class - MFC Class

![add class - MFC Class](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class1-mfc_class.png)
![add class - MFC Class](https://github.com/tdtc-hrb/csdn/raw/master/images/add_class2-mfc_class.png)

#### [When to use virtual destructors?](https://stackoverflow.com/questions/461203/when-to-use-virtual-destructors)
In the Add Class Wizard: 
- When selecting a C++ Class, there is no virtual destructor by default; 
- when selecting an MFC Class, a virtual destructor is enabled by default.

### Serialization class
- define
```
DECLARE_SERIAL(CConnectString)
```
- impl
```
IMPLEMENT_SERIAL(CConnectString, CObject, 1)
```
#### member
```
private:
    CString Server;
    CString Db;
    CString User;
    CString Pwd;
    int     Type;
```
#### Serializating an Object
- define
```
virtual void Serialize(CArchive& ar);
```
- impl
```
void CConnectString::Serialize(CArchive &ar)
{
    CObject::Serialize(ar);

    if (ar.IsStoring()) {
        ar << Server << Db << User << Pwd << Type;
    }
    else {
        ar >> Server >> Db >> User >> Pwd >> Type;
    }
}
```
#### getter and setter
> option

- define - public
```
    //// Getter and Setter
    CString GetServer(void);
    void    SetServer(CString server);
    CString GetDb(void);
    void    SetDb(CString db);
    CString GetUser(void);
    void    SetUser(CString user);
    CString GetPwd(void);
    void    SetPwd(CString pwd);
    int     GetType(void);
    void    SetType(int type);
```
- impl
```
//// Getter and Setter
CString CConnectString::GetServer(void)
{
    return Server;
}

void    CConnectString::SetServer(CString server)
{
    Server = server;
}
CString CConnectString::GetDb(void)
{
    return Db;
}
void    CConnectString::SetDb(CString db)
{
    Db = db;
}
CString CConnectString::GetUser(void)
{
    return User;
}
void    CConnectString::SetUser(CString user)
{
    User = user;
}
CString CConnectString::GetPwd(void)
{
    return Pwd;
}
void    CConnectString::SetPwd(CString pwd)
{
    Pwd = pwd;
}
int     CConnectString::GetType(void)
{
    return Type;
}
void    CConnectString::SetType(int type)
{
    Type = type;
}
```
