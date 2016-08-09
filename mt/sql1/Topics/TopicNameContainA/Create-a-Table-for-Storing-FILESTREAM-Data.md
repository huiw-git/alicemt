---
title: "Create a Table for Storing FILESTREAM Data"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
caps.latest.revision: 17
manager: jhubbard
---
# Create a Table for Storing FILESTREAM Data
This topic shows how to create a table for storing FILESTREAM data.  
  
 When the database has a FILESTREAM filegroup, you can create or modify tables to store FILESTREAM data. To specify that a column contains FILESTREAM data, you create a **varbinary(max)** column and add the FILESTREAM attribute.  
  
### To create a table to store FILESTREAM data  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], click **New Query** to display the Query Editor.  
  
2.  Copy the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code from the following example into the Query Editor. This [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code creates a FILESTREAM-enabled table called Records.  
  
3.  To create the table, click **Execute**.  
  
## Example  
 The following code example shows how to create a table that is named `Records`. The `Id` column is a `ROWGUIDCOL` column and is required to use FILESTREAM data with Win32 APIs. The `SerialNumber` column is a `UNIQUE INTEGER`. The `Chart` column is a `FILESTREAM` column and is used to store the `Chart` in the file system.  
  
> [!NOTE]  
>  This example refers to the Archive database that is created in [Create a FILESTREAM-Enabled Database](../../Topics/TopicNameContainA/Create-a-FILESTREAM-Enabled-Database.md).  
  
 [!CODE [FILESTREAM#FS_CreateTable](../CodeSnippet/SQL15/tsql/filestream#fs_createtable)]  
  
## See Also  
 [CREATE TABLE](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)   
 [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1)