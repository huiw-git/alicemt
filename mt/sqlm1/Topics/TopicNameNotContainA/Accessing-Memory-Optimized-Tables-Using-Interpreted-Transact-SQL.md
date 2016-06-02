---
title: Accessing Memory-Optimized Tables Using Interpreted Transact-SQL
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
---
# Accessing Memory-Optimized Tables Using Interpreted Transact-SQL
 With only a few exceptions, you can access memory\-optimized tables using any [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] query or DML operation \(select, insert, update, or delete\), ad hoc batches, and SQL modules such as stored procedures, table\-value functions, triggers, and views.  
  
Interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] refers to [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] batches or stored procedures other than a natively compiled stored procedure. Interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access to memory\-optimized tables is referred to as interop access.  

Starting with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], queries in interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] can scan memory-optimized tables in parallel, instead of just in serial mode.

Memory\-optimized tables can also be accessed using a natively compiled stored procedure. Natively compiled stored procedures are recommended for performance\-critical OLTP operations.  
  
Interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access is recommended for these scenarios:  
  
- Ad hoc queries and administrative tasks.  
  
- Reporting queries, which typically use constructs not available in natively compiled stored procedures \(such as *window* functions, sometimes referred to as [OVER](../Topic/OVER%20Clause%20\(Transact-SQL\).md) functions\).  
  
- To migrate performance\-critical parts of your application to memory\-optimized tables, with minimal \(or no\) application code changes. You can potentially see performance improvements from migrating tables. If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.  
  
- When a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement is not available for natively compiled stored procedures.  
  
However, the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stored procedures that access data in a memory\-optimized table.  
  
|Area|Unsupported|  
|----------|-----------------|  
|Access to tables|TRUNCATE TABLE<br /><br /> MERGE \(memory\-optimized table as target\)<br /><br /> Dynamic and keyset cursors \(these automatically degrade to static\).<br /><br /> Access from CLR modules, using the context connection.<br /><br /> Referencing a memory\-optimized table from an indexed view.|  
|Cross\-database|Cross\-database queries<br /><br /> Cross\-database transactions<br /><br /> Linked servers|  
  
## Table Hints

For more information about table hints, see. [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md). The SNAPSHOT was added to support [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)].  
  
The following table hints are not supported when accessing a memory\-optimized table using interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  

  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE\_CONSTRAINTS|IGNORE\_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL\_WINDOW\_MAX\_CELLS \= *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  

When accessing a memory\-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], you must do at least one of the following:  
  
- Specify  an [isolation level table hint](../../Topics\TopicNameNotContainA/Transactions-with-Memory-Optimized-Tables.md) such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE.  
  
- Set the database option [MEMORY\_OPTIMIZED\_ELEVATE\_TO\_SNAPSHOT](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) to ON.  
  
An isolation level table hint is not required for memory\-optimized tables accessed by queries running in [auto\-commit mode](assetId:///c8de5b60-d147-492d-b601-2eeae8511d00).  
  
## See Also

[Transact-SQL Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)   

[Migrating to In-Memory OLTP](../../Topics\TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)  
