---
title: SQL Server, Broker TO Statistics Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
---
# SQL Server, Broker TO Statistics Object
  The SQLServer:Broker TO Statistics performance object reports information about how many times [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] dialogs request transmission objects, and how often transmission objects are written to **tempdb**.  
  
 Transmission objects record the state of message transmissions for a [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] dialog. They are stored in memory. To free memory, [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] periodically writes batches of inactive transmission objects to work tables in **tempdb**.  
  
 The following table lists the counters that this object contains.  
  
|SQL Server Broker TO Statistics counters|Description|  
|----------------------------------------------|-----------------|  
|**Avg. Length of Batched Writes**|The average number of transmission objects saved in a batch.|  
|**Avg. Time To Write Batch \(ms\)**|The average number of milliseconds required to save a batch of transmission objects.|  
|**Avg. Time Between Batches \(ms\)**|The average number of milliseconds between writes of transmission object batches.|  
|**Tran Object Gets\/sec**|The number of times per second that dialogs requested transmission objects.|  
|**Tran Objects Marked Dirty\/sec**|The number of times per second that transmission objects were marked as dirty. Transmission objects are marked as dirty by the first modification that causes the in\-memory copy to differ from the copy stored in **tempdb**. Transmission objects are modified when [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] has to record a change in the state of message transmissions for the dialog.|  
|**Tran Object Writes\/sec**|The number of times per second that a batch of transmission objects were written to **tempdb** work tables. Large numbers of writes could indicate that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] memory is being stressed.|  
  
## See Also  
 [SQL Server, Access Methods Object](../../Topics\TopicNameNotContainA/SQL-Server,-Access-Methods-Object.md)   
 [SQL Server, Memory Manager Object](../../Topics\TopicNameNotContainA/SQL-Server,-Memory-Manager-Object.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  