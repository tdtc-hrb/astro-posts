---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Deploying SQLite in the .NET Framework"
description: "ADO.NET provider for SQLite"
date: 2025-02-22
author: xiaobin
tags: ["faq6", ".NET Framework 4.6", "System.Data.SQLite"]
---

- [Method not found: System.Array.Empty](https://stackoverflow.com/questions/46467530/method-not-found-0-system-array-empty)
```
System.MissingMethodException: Method not found: '!!0[] System.Array.Empty()'.
   at System.Data.SQLite.SQLiteConvert.TypeNameToDbType(SQLiteConnection connection, String typeName, SQLiteConnectionFlags flags)
   at System.Data.SQLite.SQLiteDataReader.GetSQLiteType(SQLiteConnectionFlags flags, Int32 i)
   at System.Data.SQLite.SQLiteDataReader.GetValue(Int32 i)
   at System.Data.SQLite.SQLiteDataReader.get_Item(Int32 i)
   at System.Data.SQLite.SQLiteCommand.ExecuteScalar(CommandBehavior behavior)
   at System.Data.SQLite.SQLiteCommand.ExecuteScalar()
... ...
```
down [v4.6.2](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net462) / 
[v4.7.2](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net472) or above.

- File Not Found Exception
```
System.IO.FileNotFoundException
   at System.Reflection.RuntimeAssembly._nLoad(System.Reflection.AssemblyName, System.String, System.Security.Policy.Evidence, System.Reflection.RuntimeAssembly, System.Threading.StackCrawlMark ByRef, IntPtr, Boolean, Boolean, Boolean)
   at System.Reflection.RuntimeAssembly.nLoad(System.Reflection.AssemblyName, System.String, System.Security.Policy.Evidence, System.Reflection.RuntimeAssembly, System.Threading.StackCrawlMark ByRef, IntPtr, Boolean, Boolean, Boolean)
   at System.Reflection.RuntimeAssembly.InternalLoadAssemblyName(System.Reflection.AssemblyName, System.Security.Policy.Evidence, System.Reflection.RuntimeAssembly, System.Threading.StackCrawlMark ByRef, IntPtr, Boolean, Boolean, Boolean)
   at System.Reflection.RuntimeAssembly.InternalLoadFrom(System.String, System.Security.Policy.Evidence, Byte[], System.Configuration.Assemblies.AssemblyHashAlgorithm, Boolean, Boolean, System.Threading.StackCrawlMark ByRef)
   at System.Reflection.Assembly.LoadFrom(System.String)
```
应用程序使用x86的 System.Data.SQLite.dll , 
而在使用中没有安装x86版的VC Redist.

- File Load Exception
```
System.IO.FileLoadException: Could not load file or assembly 'System.Data.SQLite.dll' or one of its dependencies. 
A dynamic link library (DLL) initialization routine failed. (Exception from HRESULT: 0x8007045A)
File name: 'System.Data.SQLite.dll'
   at System.Reflection.RuntimeAssembly._nLoad(AssemblyName fileName, String codeBase, Evidence assemblySecurity, RuntimeAssembly locationHint, StackCrawlMark& stackMark, IntPtr pPrivHostBinder, Boolean throwOnFileNotFound, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.nLoad(AssemblyName fileName, String codeBase, Evidence assemblySecurity, RuntimeAssembly locationHint, StackCrawlMark& stackMark, IntPtr pPrivHostBinder, Boolean throwOnFileNotFound, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.InternalLoadAssemblyName(AssemblyName assemblyRef, Evidence assemblySecurity, RuntimeAssembly reqAssembly, StackCrawlMark& stackMark, IntPtr pPrivHostBinder, Boolean throwOnFileNotFound, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.InternalLoadFrom(String assemblyFile, Evidence securityEvidence, Byte[] hashValue, AssemblyHashAlgorithm hashAlgorithm, Boolean forIntrospection, Boolean suppressSecurityChecks, StackCrawlMark& stackMark)
   at System.Reflection.Assembly.LoadFrom(String assemblyFile)
```
使用了.net的低版本 System.Data.SQLite.dll :
```
sqlite-netFx35-binary-bundle-Win32-2008
```
而应用程序是: .net 4.6:
```
sqlite-netFx46-binary-bundle-Win32-2015
```
