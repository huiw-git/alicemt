---
title: Natively Compiled Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
---
# Natively Compiled Stored Procedures
  Natively compiled stored procedures are [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stored procedures compiled to native code that access memory\-optimized tables. Natively compiled stored procedures allow for efficient execution of the queries and business logic in the stored procedure. For more details about the native compilation process, see [Native Compilation of Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Native-Compilation-of-Tables-and-Stored-Procedures.md). For more information about migrating disk\-based stored procedures to natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md).  
  
> [!NOTE]  
>  One difference between interpreted \(disk\-based\) stored procedures and natively compiled stored procedures is that an interpreted stored procedure is compiled at first execution, whereas a natively compiled stored procedure is compiled when it is created. With natively compiled stored procedures, many error conditions can be detected at create time and will cause creation of the natively compiled stored procedure to fail \(such as arithmetic overflow, type conversion, and some divide\-by\-zero conditions\). With interpreted stored procedures, these error conditions typically do not cause a failure when the stored procedure is created, but all executions will fail.  
  
 Topics in this section:  
  
-   [Creating Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Creating-Natively-Compiled-Stored-Procedures.md)  
  
-   [Atomic Blocks](../../Topics\TopicNameNotContainA/Atomic-Blocks.md)  
  
-   [Supported Features for Natively Compiled T-SQL Modules](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md)  
  
-   [Supported DDL for Natively Compiled T-SQL modules](../../Topics\TopicNameNotContainA/Supported-DDL-for-Natively-Compiled-T-SQL-modules.md)  
  
-   [Natively Compiled Stored Procedures and Execution Set Options](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures-and-Execution-Set-Options.md)  
  
-   [Best Practices for Calling Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Best-Practices-for-Calling-Natively-Compiled-Stored-Procedures.md)  
  
-   [Monitoring Performance of Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Monitoring-Performance-of-Natively-Compiled-Stored-Procedures.md)  
  
-   [Calling Natively Compiled Stored Procedures from Data Access Applications](../../Topics\TopicNameNotContainA/Calling-Natively-Compiled-Stored-Procedures-from-Data-Access-Applications.md)  
  
## See Also  
 [Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Memory-Optimized-Tables.md)  
  
  