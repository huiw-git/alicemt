---
title: "In-Memory OLTP Garbage Collection"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
caps.latest.revision: 6
caps.handback.revision: 0
manager: jhubbard
---
# In-Memory OLTP Garbage Collection
A data row is considered stale if it was deleted by a transaction that is no longer active. A stale row is eligible for garbage collection. The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../Topics/TopicNameContainA/tokens/hek_2_md.md)]:  
  
-   Non-blocking. Garbage collection is distributed over time with minimal impact on the workload.  
  
-   Cooperative. User transactions participate in garbage collection with main garbage-collection thread.  
  
-   Efficient. User transactions delink stale rows in the access path (the index) being used. This reduces the work required when the row is finally removed.  
  
-   Responsive. Memory pressure leads to aggressive garbage collection.  
  
-   Scalable. After commit, user transactions do part of the work of garbage collection. The more transaction activity, the more the transactions delink stale rows.  
  
 Garbage collection is controlled by the main garbage collection thread. The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold. The task of the garbage collector is to:  
  
-   Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.  
  
-   Identity row versions created by these old transactions.  
  
-   Group old rows into one or more units of 16 rows each. This is done to distribute the work of the garbage collector into smaller units.  
  
-   Move these work units into the garbage collection queue, one for each scheduler. Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats (Transact-SQL)](assetId:///8287d611-50e3-43e1-ba8d-3e3793d3ba0e), [sys.dm_db_xtp_gc_cycle_stats (Transact-SQL)](assetId:///bbc9704e-158e-4d32-b693-f00dce31cd2f), and [sys.dm_xtp_gc_queue_stats (Transact-SQL)](assetId:///addef774-318d-46a7-85df-f93168a800cb).  
  
 After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory. If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node. If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue. If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.  
  
## See Also  
 [Managing Memory for In-Memory OLTP](../../Topics/TopicNameNotContainA/Managing-Memory-for-In-Memory-OLTP.md)