---
title: Transactions Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
---
# Transactions Event Category
  The **Transactions** event classes can be used to monitor the status of transactions. The event class names that are prefixed with **TM:** are used to track the transaction\-related operations that are sent through the transaction management interface.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[DTCTransaction Event Class](../../Topics\TopicNameNotContainA/DTCTransaction-Event-Class.md)|Tracks transactions coordinated by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Distributed Transaction Coordinator \(MS DTC\). These are transactions distributed between two or more databases or instances of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].|  
|[SQLTransaction Event Class](../../Topics\TopicNameNotContainA/SQLTransaction-Event-Class.md)|Tracks [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN, and ROLLBACK TRAN statements.|  
|[TM: Begin Tran Completed Event Class](../Topic/TM:%20Begin%20Tran%20Completed%20Event%20Class.md)|Indicates that a BEGIN TRANSACTION request has completed.|  
|[TM: Begin Tran Starting Event Class](../Topic/TM:%20Begin%20Tran%20Starting%20Event%20Class.md)|Indicates that a BEGIN TRANSACTION request is starting.|  
|[TM: Commit Tran Completed Event Class](../Topic/TM:%20Commit%20Tran%20Completed%20Event%20Class.md)|Indicates that a COMMIT TRANSACTION request has completed.|  
|[TM: Commit Tran Starting Event Class](../Topic/TM:%20Commit%20Tran%20Starting%20Event%20Class.md)|Indicates that a COMMIT TRANSACTION request is starting.|  
|[TM: Promote Tran Completed Event Class](../Topic/TM:%20Promote%20Tran%20Completed%20Event%20Class.md)|Indicates that a PROMOTE TRANSACTION request has completed.|  
|[TM: Promote Tran Starting Event Class](../Topic/TM:%20Promote%20Tran%20Starting%20Event%20Class.md)|Indicates that a PROMOTE TRANSACTION request is starting.|  
|[TM: Rollback Tran Completed Event Class](../Topic/TM:%20Rollback%20Tran%20Completed%20Event%20Class.md)|Indicates that a ROLLBACK TRANSACTION request has completed.|  
|[TM: Rollback Tran Starting Event Class](../Topic/TM:%20Rollback%20Tran%20Starting%20Event%20Class.md)|Indicates that a ROLLBACK TRANSACTION request is starting.|  
|[TM: Save Tran Completed Event Class](../Topic/TM:%20Save%20Tran%20Completed%20Event%20Class.md)|Indicates that a SAVE TRANSACTION request has completed.|  
|[TM: Save Tran Starting Event Class](../Topic/TM:%20Save%20Tran%20Starting%20Event%20Class.md)|Indicates that a SAVE TRANSACTION request is starting.|  
|[TransactionLog Event Class](../../Topics\TopicNameNotContainA/TransactionLog-Event-Class.md)|Tracks when transactions are written to a database transaction log.|  
  
  