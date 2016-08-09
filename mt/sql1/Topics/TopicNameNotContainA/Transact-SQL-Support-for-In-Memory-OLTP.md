---
title: "Transact-SQL Support for In-Memory OLTP"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 53
caps.handback.revision: 0
manager: jhubbard
---
# Transact-SQL Support for In-Memory OLTP
The following [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements include syntax options to support In-Memory OLTP:  
  
-   [ALTER DATABASE Filegroup Options](assetId:///1f635762-f7aa-4241-9b7a-b51b22292b07) (added **MEMORY_OPTIMIZED_DATA**)  
  
-   [ALTER TRIGGER (Transact-SQL)](assetId:///2a99c7c1-ac2f-4637-aa7c-3d1bf514e500)  
  
-   [CREATE DATABASE](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8) (added **MEMORY_OPTIMIZED_DATA**)  
  
-   [CREATE PROCEDURE](assetId:///afe3d86d-c9ab-44e4-b74d-4e3dbd9cc58c)  
  
-   [CREATE TABLE](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)  
  
-   [CREATE TRIGGER (Transact-SQL)](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7)  
  
-   [CREATE TYPE](assetId:///2202236b-e09f-40a1-bbc7-b8cff7488905)  
  
-   [DECLARE @local_variable (Transact-SQL)](assetId:///d1635ebb-f751-4de1-8bbc-cae161f90821)   
    In a natively compiled stored procedure, you can declare a variable as **NOT NULL**. You cannot do so in a regular stored procedure.  
  
 **AUTO_UPDATE_STATISTICS** can be **ON** for memory-optimized tables, starting with SQL Server 2016. For more information, see [sp_autostats (Transact-SQL)](assetId:///d1df8c15-ee73-49eb-9d13-6e98943c3e38).  
  
 [SET STATISTICS XML (Transact-SQL)](assetId:///2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7) ON is not supported for natively compiled stored procedures.  
  
 For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
 For information about supported constructs in and on natively compiled stored procedures, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md) and [Supported DDL for Natively Compiled T-SQL modules](../../Topics/TopicNameNotContainA/Supported-DDL-for-Natively-Compiled-T-SQL-modules.md).  
  
## See Also  
 [In-Memory OLTP (In-Memory Optimization)](../../Topics/TopicNameNotContainA/In-Memory-OLTP--In-Memory-Optimization-.md)   
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)   
 [Unsupported SQL Server Features for In-Memory OLTP](../../Topics/TopicNameNotContainA/Unsupported-SQL-Server-Features-for-In-Memory-OLTP.md)   
 [Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)