---
title: "FileTable DDL, Functions, Stored Procedures, and Views"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# FileTable DDL, Functions, Stored Procedures, and Views
Lists the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database objects that have been added or changed to support the FileTable feature in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 The Status column in the following tables indicates whether the item is new in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], or was present in previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] but has been changed in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] to support semantic search.  
  
 For the list of statements and database objects that support FILESTREAM, see [FILESTREAM DDL, Functions, Stored Procedures, and Views](../../Topics/TopicNameNotContainA/FILESTREAM-DDL--Functions--Stored-Procedures--and-Views.md).  
  
##  <a name="ddl"></a> Transact-SQL Data Definition Language (DDL) Statements  
  
|Object|Status|More Information|  
|------------|------------|----------------------|  
|[ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)<br /><br /> [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)|Changed|[Enable the Prerequisites for FileTable](../../Topics/TopicNameNotContainA/Enable-the-Prerequisites-for-FileTable.md)<br /><br /> [Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
|[ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1)|Changed|[Create, Alter, and Drop FileTables](../../Topics/TopicNameNotContainA/Create--Alter--and-Drop-FileTables.md)<br /><br /> [Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
|[CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)|Changed|[Enable the Prerequisites for FileTable](../../Topics/TopicNameNotContainA/Enable-the-Prerequisites-for-FileTable.md)|  
|[CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)|Changed|[Create, Alter, and Drop FileTables](../../Topics/TopicNameNotContainA/Create--Alter--and-Drop-FileTables.md)|  
|[RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)<br /><br /> [RESTORE Arguments (Transact-SQL)](assetId:///4bfe5734-3003-4165-afd4-b1131ea26e2b)|Changed||  
  
##  <a name="func"></a> Functions  
  
|Object|Status|More Information|  
|------------|------------|----------------------|  
|[FileTableRootPath (Transact-SQL)](assetId:///0cba908a-c85c-4b09-b16a-df1cb333c629)|**Added**|[Work with Directories and Paths in FileTables](../../Topics/TopicNameNotContainA/Work-with-Directories-and-Paths-in-FileTables.md)|  
|[GetFileNamespacePath (Transact-SQL)](assetId:///b393ecef-baa8-4d05-a268-b2f309fce89a)|**Added**|[Work with Directories and Paths in FileTables](../../Topics/TopicNameNotContainA/Work-with-Directories-and-Paths-in-FileTables.md)|  
|[GetPathLocator (Transact-SQL)](assetId:///78b7e220-445b-4fdf-811b-7253f4f2b058)|**Added**|[Work with Directories and Paths in FileTables](../../Topics/TopicNameNotContainA/Work-with-Directories-and-Paths-in-FileTables.md)|  
  
##  <a name="sproc"></a> Stored Procedures  
  
|Object|Status|More Information|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles (Transact-SQL)](assetId:///7188353e-ab29-49a0-8f25-7fb8ab122589)|**Added**|[Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
  
##  <a name="cv"></a> Catalog Views  
  
|Object|Status|More Information|  
|------------|------------|----------------------|  
|[sys.database_filestream_options (Transact-SQL)](assetId:///3383c607-0bbc-456a-ab37-7230f4cbf0e9)|**Added**|[Enable the Prerequisites for FileTable](../../Topics/TopicNameNotContainA/Enable-the-Prerequisites-for-FileTable.md)|  
|[sys.filetable_system_defined_objects (Transact-SQL)](assetId:///62022e6b-46f6-495f-b14b-53f41e040361)|**Added**|[Create, Alter, and Drop FileTables](../../Topics/TopicNameNotContainA/Create--Alter--and-Drop-FileTables.md)<br /><br /> [Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
|[sys.filetables (Transact-SQL)](assetId:///a740be59-cd52-4707-9ad2-5203669a63ac)|**Added**|[Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
|[sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090)|Changed|[Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
  
##  <a name="dmv"></a> Dynamic Management Views  
  
|Object|Status|More Information|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles (Transact-SQL)](assetId:///507ec125-67dc-450a-9081-94cde5444a92)|**Added**|[Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)|  
  
## See Also  
 [Manage FileTables](../../Topics/TopicNameNotContainA/Manage-FileTables.md)