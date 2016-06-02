---
title: Supported DDL for Natively Compiled T-SQL modules
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
---
# Supported DDL for Natively Compiled T-SQL modules
  This topic lists the supported DDL constructs for natively compiled T\-SQL modules, such as stored procedures, scalar UDFs, inline TVFs, and triggers.  
  
 For information on features and T\-SQL surface area that can be used as part of natively compiled T\-SQL modules, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md).  
  
 For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
 The following are supported:  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../Topic/CREATE%20PROCEDURE%20\(Transact-SQL\).md)  
  
-   [DROP PROCEDURE &#40;Transact-SQL&#41;](../Topic/DROP%20PROCEDURE%20\(Transact-SQL\).md)  
  
-   [ALTER PROCEDURE &#40;Transact-SQL&#41;](../Topic/ALTER%20PROCEDURE%20\(Transact-SQL\).md)  
  
-   [SELECT &#40;Transact-SQL&#41;](../Topic/SELECT%20\(Transact-SQL\).md) and INSERT SELECT statements  
  
-   SCHEMABINDING and BEGIN ATOMIC \(required for natively compiled stored procedures\)  
  
     For more information, see [Creating Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Creating-Natively-Compiled-Stored-Procedures.md).  
  
-   NATIVE\_COMPILATION  
  
     For more information, see [Native Compilation of Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Native-Compilation-of-Tables-and-Stored-Procedures.md).  
  
-   Parameters and variables can be declared as NOT NULL \(available only for natively compiled modules: natively compiled stored procedures and natively compiled, scalar user\-defined functions\).  
  
-   Table\-valued parameters.  
  
     For more information, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../Topic/Use%20Table-Valued%20Parameters%20\(Database%20Engine\).md).  
  
-   EXECUTE AS OWNER, SELF, CALLER and user.  
  
-   GRANT and DENY permissions on tables and procedures.  
  
     For more information, see [GRANT Object Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Object%20Permissions%20\(Transact-SQL\).md) and [DENY Object Permissions &#40;Transact-SQL&#41;](../Topic/DENY%20Object%20Permissions%20\(Transact-SQL\).md).  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)  
  
  