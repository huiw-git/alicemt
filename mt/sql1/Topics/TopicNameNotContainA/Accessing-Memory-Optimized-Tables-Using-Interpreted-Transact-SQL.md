---
title: "Accessing Memory-Optimized Tables Using Interpreted Transact-SQL"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Accessing Memory-Optimized Tables Using Interpreted Transact-SQL
With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] query or DML operation (select, insert, update, or delete), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.  
  
 Interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] refers to [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] batches or stored procedures other than a natively compiled stored procedure. Interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] access to memory-optimized tables is referred to as interop access.  
  
 Memory-optimized tables can also be accessed using a natively compiled stored procedure. Natively compiled stored procedures are recommended for performance-critical OLTP operations.  
  
 Interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] access is recommended for these scenarios:  
  
-   Ad hoc queries and administrative tasks.  
  
-   Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as *window* functions, sometimes referred to as [OVER](assetId:///ddcef3a6-0341-43e0-ae73-630484b7b398) functions).  
  
-   To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes. You can potentially see performance improvements from migrating tables. If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.  
  
-   When a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement is not available for natively compiled stored procedures.  
  
 However, the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] stored procedures that access data in a memory-optimized table.  
  
|Area|Unsupported|  
|----------|-----------------|  
|Access to tables|TRUNCATE TABLE<br /><br /> MERGE (memory-optimized table as target)<br /><br /> Dynamic and keyset cursors (these automatically degrade to static).<br /><br /> Access from CLR modules, using the context connection.<br /><br /> Referencing a memory-optimized table from an indexed view.|  
|Cross-database|Cross-database queries<br /><br /> Cross-database transactions<br /><br /> Linked servers|  
  
## Table Hints  
 For more information about table hints, see. [Table Hints](assetId:///8bf1316f-c0ef-49d0-90a7-3946bc8e7a89). The SNAPSHOT was added to support [!INCLUDE[hek_2](../../Topics/TopicNameContainA/tokens/hek_2_md.md)].  
  
 The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE_CONSTRAINTS|IGNORE_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL_WINDOW_MAX_CELLS = *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  
 When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], you must do at least one of the following:  
  
-   Specify  an [isolation level table hint](../../Topics/TopicNameNotContainA/Transactions-with-Memory-Optimized-Tables.md) such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE.  
  
-   Set the database option [MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) to ON.  
  
 An isolation level table hint is not required for memory-optimized tables accessed by queries running in [auto-commit mode](assetId:///c8de5b60-d147-492d-b601-2eeae8511d00).  
  
## See Also  
 [Transact-SQL Support for In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)   
 [Migrating to In-Memory OLTP](../../Topics/TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)