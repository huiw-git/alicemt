---
title: "Supported DDL for Natively Compiled T-SQL modules"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Supported DDL for Natively Compiled T-SQL modules
This topic lists the supported DDL constructs for natively compiled T-SQL modules, such as stored procedures, scalar UDFs, inline TVFs, and triggers.  
  
 For information on features and T-SQL surface area that can be used as part of natively compiled T-SQL modules, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md).  
  
 For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
 The following are supported:  
  
-   [CREATE PROCEDURE (Transact-SQL)](assetId:///afe3d86d-c9ab-44e4-b74d-4e3dbd9cc58c)  
  
-   [DROP PROCEDURE (Transact-SQL)](assetId:///1c2d7235-7b9b-4336-8f17-429e7d82c2c3)  
  
-   [ALTER PROCEDURE (Transact-SQL)](assetId:///ed9b2f76-11ec-498d-a95e-75b490a75733)  
  
-   [SELECT (Transact-SQL)](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0) and INSERT SELECT statements  
  
-   SCHEMABINDING and BEGIN ATOMIC (required for natively compiled stored procedures)  
  
     For more information, see [Creating Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Creating-Natively-Compiled-Stored-Procedures.md).  
  
-   NATIVE_COMPILATION  
  
     For more information, see [Native Compilation of Tables and Stored Procedures](../../Topics/TopicNameNotContainA/Native-Compilation-of-Tables-and-Stored-Procedures.md).  
  
-   Parameters and variables can be declared as NOT NULL (available only for natively compiled modules: natively compiled stored procedures and natively compiled, scalar user-defined functions).  
  
-   Table-valued parameters.  
  
     For more information, see [Use Table-Valued Parameters (Database Engine)](../../Topics/TopicNameNotContainA/Use-Table-Valued-Parameters--Database-Engine-.md).  
  
-   EXECUTE AS OWNER, SELF, CALLER and user.  
  
-   GRANT and DENY permissions on tables and procedures.  
  
     For more information, see [GRANT Object Permissions (Transact-SQL)](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea) and [DENY Object Permissions (Transact-SQL)](assetId:///0b8d3ddc-38c0-4241-b7bb-ee654a5081aa).  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)