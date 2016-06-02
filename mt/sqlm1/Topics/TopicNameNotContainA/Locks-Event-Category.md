---
title: Locks Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
---
# Locks Event Category
  Use the event classes in the **Locks** event category to monitor locking activity in an instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. These event classes can help you investigate locking problems caused by multiple users reading and modifying data concurrently.  
  
 Because the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] often processes many locks, capturing the **Locks** event classes during a trace can incur significant overhead and result in large trace files or tables.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Deadlock Graph Event Class](../../Topics\TopicNameNotContainA/Deadlock-Graph-Event-Class.md)|Provides an XML description of a deadlock.|  
|[Lock:Acquired Event Class](../Topic/Lock:Acquired%20Event%20Class.md)|Indicates that a lock has been acquired on a resource, such as a row in a table.|  
|[Lock:Cancel Event Class](../Topic/Lock:Cancel%20Event%20Class.md)|Tracks requests for locks that were canceled before the lock was acquired \(for example, to prevent a deadlock\).|  
|[Lock:Deadlock Chain Event Class](../Topic/Lock:Deadlock%20Chain%20Event%20Class.md)|Monitors when deadlock conditions occur and which objects are involved.|  
|[Lock:Deadlock Event Class](../Topic/Lock:Deadlock%20Event%20Class.md)|Tracks when a transaction has requested a lock on a resource already locked by another transaction, resulting in a deadlock.|  
|[Lock:Escalation Event Class](../Topic/Lock:Escalation%20Event%20Class.md)|Indicates that a finer\-grained lock has been converted to a coarser\-grained lock.|  
|[Lock:Released Event Class](../Topic/Lock:Released%20Event%20Class.md)|Tracks when a lock is released.|  
|[Lock:Timeout &#40;timeout &#62; 0&#41; Event Class](../Topic/Lock:Timeout%20\(timeout%20%3E%200\)%20Event%20Class.md)|Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource. This event occurs only in situations where the lock time\-out value is greater than zero.|  
|[Lock:Timeout Event Class](../Topic/Lock:Timeout%20Event%20Class.md)|Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.|  
  
  