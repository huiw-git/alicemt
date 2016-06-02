---
title: Access FILESTREAM Data with Transact-SQL
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
---
# Access FILESTREAM Data with Transact-SQL
  This topic describes how to use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] INSERT, UPDATE, and DELETE statements to manage FILESTREAM data.  
  
> [!NOTE]  
>  The examples in this topic require the FILESTREAM\-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](../../Topics\TopicNameContainA/Create-a-FILESTREAM-Enabled-Database.md) and [Create a Table for Storing FILESTREAM Data](../../Topics\TopicNameContainA/Create-a-Table-for-Storing-FILESTREAM-Data.md).  
  
##  <a name="ins"></a> Inserting a Row That Contains FILESTREAM Data  
 To add a row to a table that supports FILESTREAM data, use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] INSERT statement. When you insert data into a FILESTREAM column, you can insert NULL or a **varbinary\(max\)** value.  
  
### Inserting NULL  
 The following example shows how to insert `NULL`. When the FILESTREAM value is `NULL`, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] does not create a file in the file system.  
  
 [!CODE [FILESTREAM#FS_InsertNULL](../CodeSnippet/SQL15/tsql/filestream#fs_insertnull)]  
  
### Inserting a Zero\-Length Record  
 The following example shows how to use `INSERT` to create a zero\-length record. This is useful for when you want to obtain a file handle, but will be manipulating the file by using Win32 APIs.  
  
 [!CODE [FILESTREAM#FS_InsertZero](../CodeSnippet/SQL15/tsql/filestream#fs_insertzero)]  
  
### Creating a Data File  
 The following example shows how to use `INSERT` to create a file that contains data. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] converts the string `Seismic Data` to a `varbinary(max)` value. FILESTREAM creates the Windows file if it does not already exist.The data is then added to the data file.  
  
 [!CODE [FILESTREAM#FS_InsertData](../CodeSnippet/SQL15/tsql/filestream#fs_insertdata)]  
  
 When you select all data from the `Archive`.`dbo.Records` table, the results are similar to the results that are shown in the following table. However, the `Id` column will contain different GUIDs.  
  
|Id|SerialNumber|Resume|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
 [In This Topic](#TOP)  
  
##  <a name="upd"></a> Updating FILESTREAM Data  
 You can use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to update the data in the file system file; although, you might not want to do this when you have to stream large amounts of data to a file.  
  
 The following example replaces any text in the file record with the text `Xray 1`.  
  
 [!CODE [FILESTREAM#FS_UpdateData](../CodeSnippet/SQL15/tsql/filestream#fs_updatedata)]  
  
 [In This Topic](#TOP)  
  
##  <a name="del"></a> Deleting FILESTREAM Data  
 When you delete a row that contains a FILESTREAM field, you also delete its underlying file system files. The only way to delete a row, and therefore the file, is to use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] DELETE statement.  
  
 The following example shows how to delete a row and its associated file system files.  
  
 [!CODE [FILESTREAM#FS_DeleteData](../CodeSnippet/SQL15/tsql/filestream#fs_deletedata)]  
  
 When you select all data from the `dbo.Archive` table, the row is gone. You can no longer use the associated file.  
  
> [!NOTE]  
>  The underlying files are removed by the FILESTREAM garbage collector.  
  
 [In This Topic](#TOP)  
  
## See Also  
 [Enable and Configure FILESTREAM](../../Topics\TopicNameNotContainA/Enable-and-Configure-FILESTREAM.md)   
 [Avoid Conflicts with Database Operations in FILESTREAM Applications](../../Topics\TopicNameNotContainA/Avoid-Conflicts-with-Database-Operations-in-FILESTREAM-Applications.md)  
  
  