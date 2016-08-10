---
title: "Create a FILESTREAM-Enabled Database"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
caps.latest.revision: 17
manager: jhubbard
---
# Create a FILESTREAM-Enabled Database
This topic shows how to create a database that supports FILESTREAM. Because FILESTREAM uses a special type of filegroup, when you create the database, you must specify the CONTAINS FILESTREAM clause for at least one filegroup.  
  
 A FILESTREAM filegroup can contain more than one file. For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files, see [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8).  
  
### To create a FILESTREAM-enabled database  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], click **New Query** to display the Query Editor.  
  
2.  Copy the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code from the following example into the Query Editor. This [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code creates a FILESTREAM-enabled database called Archive.  
  
    > [!NOTE]  
    >  For this script, the directory C:\Data must exist.  
  
3.  To build the database, click **Execute**.  
  
## Example  
 The following code example creates a database that is named `Archive`. The database contains three filegroups: `PRIMARY`, `Arch1`, and `FileStreamGroup1`. `PRIMARY` and `Arch1` are regular filegroups that cannot contain FILESTREAM data. `FileStreamGroup1` is the `FILESTREAM` filegroup.  
  
 [!CODE [FILESTREAM#FS_CreateDB](../CodeSnippet/SQL15/tsql/filestream#fs_createdb)]  
  
 For a `FILESTREAM` filegroup, `FILENAME` refers to a path. The path up to the last folder must exist, and the last folder must not exist. In this example, `c:\data` must exist. However, the `filestream1` subfolder cannot exist when you execute the `CREATE DATABASE` statement. For more information about the syntax, see [CREATE DATABASE](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8).  
  
 After you run the previous example, a filestream.hdr file and an $FSLOG folder appears in the c:\Data\filestream1 folder. The filestream.hdr file is a header file for the FILESTREAM container.  
  
> [!IMPORTANT]  
>  The filestream.hdr file is an important system file. It contains FILESTREAM header information. Do not remove or modify this file.  
  
 For existing databases, you can use the [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da) statement to add a FILESTREAM filegroup.  
  
## See Also  
 [CREATE DATABASE](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)   
 [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)