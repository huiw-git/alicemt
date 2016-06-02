---
title: In-Memory OLTP (In-Memory Optimization)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
---
# In-Memory OLTP (In-Memory Optimization)
  [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] can significantly improve OLTP database application performance. [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] is a memory\-optimized database engine integrated into the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] engine, optimized for OLTP. To jump into the basic code and knowledge you need to quickly test your own memory\-optimized table and natively compiled stored procedure \(NCSProc\), see [Quick Start 1: In-Memory OLTP Technologies for Faster Transact-SQL Performance](../Topic/Quick%20Start%201:%20In-Memory%20OLTP%20Technologies%20for%20Faster%20Transact-SQL%20Performance.md).  
  
 Several improvements have recently been made to In\-Memory OLTP. The Transact\-SQL surface area has been increased to make it easier to migrate database applications. Support for performing ALTER operations for memory\-optimized tables and natively compiled stored procedures has been added, to make it easier to maintain applications. For information about the new features in [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)], see [What's New in Database Engine](../../Topics\TopicNameNotContainA/What-s-New-in-Database-Engine.md).  
  
> [!NOTE]  
>  **Try it out**  
>   
>  In\-Memory OLTP is in preview for Premium Azure SQL databases. To get started with an In\-Memory OLTP sample, and an In\-Memory Analytics sample, see [Get started with In\-Memory \(Preview\)](https://azure.microsoft.com/en-us/documentation/articles/sql-database-in-memory/).  
  
 To use [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)], you define a heavily accessed table as memory optimized. Memory\-optimized\-tables are fully transactional, durable, and are accessed using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] in the same way as disk\-based tables. A query can reference both memory\-optimized tables and disk\-based tables. A transaction can update data in memory\-optimized tables and disk\-based tables. Stored procedures that only reference memory\-optimized tables can be natively compiled into machine code for further performance improvements. The [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] engine is designed for extremely high session concurrency for OLTP type of transactions driven from a highly scaled\-out middle\-tier. To achieve this, it uses latch\-free data structures and optimistic, multi\-version concurrency control. The result is predictable, sub\-millisecond low latency and high throughput with linear scaling for database transactions. The actual performance gain depends on many factors, but 5\-to\-20 times performance improvements are common.  
  
 The following table summarizes the workload patterns that may benefit most by using [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)]:  
  
|Implementation Scenario|Characteristics|Benefits of [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)]|  
|-----------------------------|---------------------|-------------------------------------|  
|High data insertion rate from multiple concurrent connections.|Primarily append\-only store.<br /><br /> Unable to keep up with the insert workload.|Eliminate contention.<br /><br /> Reduce logging.|  
|Read performance and scale with periodic batch inserts and updates.|High performance read operations, especially when each server request has multiple read operations to perform.<br /><br /> Unable to meet scale\-up requirements.|Eliminate contention when new data arrives.<br /><br /> Lower latency data retrieval.<br /><br /> Minimize code execution time.|  
|Intensive business logic processing in the database server.|Insert, update, and delete workload.<br /><br /> Intensive computation inside stored procedures.<br /><br /> Read and write contention.|Eliminate contention.<br /><br /> Minimize code execution time for reduced latency and improved throughput.|  
|Low latency.|Require low latency business transactions which typical database solutions cannot achieve.|Eliminate contention.<br /><br /> Minimize code execution time.<br /><br /> Low latency code execution.<br /><br /> Efficient data retrieval.|  
|Session state management.|Frequent insert, update and point lookups.<br /><br /> High scale load from numerous stateless web servers.|Eliminate contention.<br /><br /> Efficient data retrieval.<br /><br /> Optional IO reduction or removal, when using non\-durable tables|  
  
 For more information about scenarios where [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] will result in the greatest performance gains, see [In\-Memory OLTP – Common Workload Patterns and Migration Considerations](http://msdn.microsoft.com/library/dn673538.aspx).  
  
 [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] will improve performance best in OLTP with short\-running transactions.  
  
 Programming patterns that [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] will improve include concurrency scenarios, point lookups, workloads where there are many inserts and updates, and business logic in stored procedures.  
  
 Integration with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)] means you can have both memory\-optimized tables and disk\-based tables in the same database, and query across both types of tables.  
  
 Note that there same are limitations in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] surface area supported for [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)]. See [Transact-SQL Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md).  
  
 [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] achieves significant performance and scalability gains by using:  
  
-   Algorithms that are optimized for accessing memory\-resident data.  
  
-   Optimistic concurrency control that eliminates logical locks.  
  
-   Lock free objects that eliminate all physical locks and latches. Threads that perform transactional work don’t use locks or latches for concurrency control.  
  
-   Natively compiled stored procedures, which have significantly better performance than interpreted stored procedures, when accessing a memory\-optimized table.  
  
> [!IMPORTANT]  
>  Some syntax changes to tables and stored procedures will be required to use [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)]. For more information, see [Migrating to In-Memory OLTP](../../Topics\TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md). Before you attempt to migrate a disk\-based table to a memory\-optimized table, read [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](../../Topics\TopicNameContainA/Determining-if-a-Table-or-Stored-Procedure-Should-Be-Ported-to-In-Memory-OLTP.md) to see which tables and stored procedures will benefit from [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)].  
  
## In this section  
 This section provides information about the following concepts:  
  
|Topic|Description|  
|-----------|-----------------|  
|[Requirements for Using Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Requirements-for-Using-Memory-Optimized-Tables.md)|Discusses hardware and software requirements and guidelines for using memory\-optimized tables.|  
|[Using In-Memory OLTP in a VM Environment](../../Topics\TopicNameContainA/Using-In-Memory-OLTP-in-a-VM-Environment.md)|Covers using [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] in a virtualized environment.|  
|[In-Memory OLTP Code Samples](../../Topics\TopicNameNotContainA/In-Memory-OLTP-Code-Samples.md)|Contains code samples that show how to create and use a memory\-optimized table.|  
|[Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Memory-Optimized-Tables.md)|Introduces memory\-optimized tables.|  
|[Memory-Optimized Table Variables](../../Topics\TopicNameNotContainA/Memory-Optimized-Table-Variables.md)|Code example showing how to use a memory\-optimized table variable instead of a traditional table variable to reduce tempdb use.|  
|[Indexes on Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Indexes-on-Memory-Optimized-Tables.md)|Introduces memory\-optimized indexes.|  
|[Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)|Introduces natively compiled stored procedures.|  
|[Managing Memory for In-Memory OLTP](../../Topics\TopicNameNotContainA/Managing-Memory-for-In-Memory-OLTP.md)|Understanding and managing memory usage on your system.|  
|[Creating and Managing Storage for Memory-Optimized Objects](../../Topics\TopicNameNotContainA/Creating-and-Managing-Storage-for-Memory-Optimized-Objects.md)|Discusses data and delta files, which store information about transactions in memory\-optimized tables.|  
|[Backup, Restore, and Recovery of Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Backup,-Restore,-and-Recovery-of-Memory-Optimized-Tables.md)|Discusses backup, restore, and recovery for memory\-optimized tables.|  
|[Transact-SQL Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)|Discusses [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] support for [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)].|  
|[High Availability Support for In-Memory OLTP databases](../../Topics\TopicNameNotContainA/High-Availability-Support-for-In-Memory-OLTP-databases.md)|Discusses availability groups and failover clustering in [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)].|  
|[SQL Server Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/SQL-Server-Support-for-In-Memory-OLTP.md)|Lists new and updated syntax and features supporting memory\-optimized tables.|  
|[Migrating to In-Memory OLTP](../../Topics\TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)|Discusses how to migrate disk\-based tables to memory\-optimized tables.|  
  
 More information about [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] is available on:  
  
-   [Microsoft® SQL Server® 2014 Product Guide](http://www.microsoft.com/download/confirmation.aspx?id=39269)  
  
-   [In\-Memory OLTP Blog](http://go.microsoft.com/fwlink/?LinkId=311696)  
  
-   [In\-Memory OLTP – Common Workload Patterns and Migration Considerations](http://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [SQL Server In\-Memory OLTP Internals Overview](http://msdn.microsoft.com/library/dn720242.aspx)  
  
## See Also  
 [Database Features](../../Topics\TopicNameNotContainA/Database-Features.md)  
  
  