---
title: Transact-SQL Support for In-Memory OLTP
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
---
# Transact-SQL Support for In-Memory OLTP
  The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements include syntax options to support In\-Memory OLTP:  
  
-   [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md) \(added **MEMORY\_OPTIMIZED\_DATA**\)  
  
-   [ALTER TRIGGER &#40;Transact-SQL&#41;](../Topic/ALTER%20TRIGGER%20\(Transact-SQL\).md)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md) \(added **MEMORY\_OPTIMIZED\_DATA**\)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../Topic/CREATE%20PROCEDURE%20\(Transact-SQL\).md)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](../Topic/CREATE%20TABLE%20\(Transact-SQL\).md)  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](../Topic/CREATE%20TRIGGER%20\(Transact-SQL\).md)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41;](../Topic/CREATE%20TYPE%20\(Transact-SQL\).md)  
  
-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../Topic/DECLARE%20@local_variable%20\(Transact-SQL\).md)   
    In a natively compiled stored procedure, you can declare a variable as **NOT NULL**. You cannot do so in a regular stored procedure.  
  
 **AUTO\_UPDATE\_STATISTICS** can be **ON** for memory\-optimized tables, starting with SQL Server 2016. For more information, see [sp_autostats &#40;Transact-SQL&#41;](../Topic/sp_autostats%20\(Transact-SQL\).md).  
  
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../Topic/SET%20STATISTICS%20XML%20\(Transact-SQL\).md) ON is not supported for natively compiled stored procedures.  
  
 For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
 For information about supported constructs in and on natively compiled stored procedures, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md) and [Supported DDL for Natively Compiled T-SQL modules](../../Topics\TopicNameNotContainA/Supported-DDL-for-Natively-Compiled-T-SQL-modules.md).  
  
## See Also  
 [In-Memory OLTP &#40;In-Memory Optimization&#41;](../Topic/In-Memory%20OLTP%20\(In-Memory%20Optimization\).md)   
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)   
 [Unsupported SQL Server Features for In-Memory OLTP](../../Topics\TopicNameNotContainA/Unsupported-SQL-Server-Features-for-In-Memory-OLTP.md)   
 [Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)  
  
  