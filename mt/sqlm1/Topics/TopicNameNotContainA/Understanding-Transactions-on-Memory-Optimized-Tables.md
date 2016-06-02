---
title: Understanding Transactions on Memory-Optimized Tables
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
robots: noindex,nofollow
---
# Understanding Transactions on Memory-Optimized Tables
  Transactions access memory\-optimized tables using a form of optimistic, multi\-version concurrency control. This means that there are different versions of the data. Each transaction operates on its own transactionally consistent version of the database, independent from other concurrently running transactions. In addition, transactions operate under the optimistic assumption that there will be no conflicts with other, concurrent, transactions. This avoids the need to use locks, but does require the system to detect conflicts and terminate one of the conflicting transactions. Conflicts can occur only for write\-write transactions and for read\-write transactions. If there is a write\-write conflict, one write transaction is terminated.  
  
 There are similarities between the concurrency control for memory\-optimized tables and the concurrency control for disk\-based tables for the READ\_COMMITTED\_SNAPSHOT and SNAPSHOT transaction isolation levels. \(For more information about disk\-based tables, see [Row Versioning\-based Isolation Levels in the Database Engine](http://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).\)  
  
## Topics in This Section  
 This section on transactions in memory\-optimized tables includes the following topics:  
  
-   [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Guidelines-for-Transaction-Isolation-Levels-with-Memory-Optimized-Tables.md)  
  
-   [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Guidelines-for-Retry-Logic-for-Transactions-on-Memory-Optimized-Tables.md)  
  
-   [Transactions in Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Transactions-in-Memory-Optimized-Tables.md)  
  
-   [Transaction Isolation Levels for Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Transaction-Isolation-Levels-for-Memory-Optimized-Tables.md)  
  
-   [Cross-Container Transactions](../../Topics\TopicNameNotContainA/Cross-Container-Transactions.md)  
  
 For more information, see [Control Transaction Durability](../../Topics\TopicNameNotContainA/Control-Transaction-Durability.md).  
  
## See Also  
 [Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Memory-Optimized-Tables.md)  
  
  