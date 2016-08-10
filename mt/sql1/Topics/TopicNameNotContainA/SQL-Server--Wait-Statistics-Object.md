---
title: "SQL Server, Wait Statistics Object"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server, Wait Statistics Object
The **SQLServer:Wait Statistics** performance object contains performance counters that report information about wait status.  
  
 The table below lists the counters that the Wait Statistics object contains.  
  
|SQL Server Wait Statistics counters|Description|  
|-----------------------------------------|-----------------|  
|**Lock waits**|Statistics for processes waiting on a lock.|  
|**Log buffer waits**|Statistics for processes waiting for log buffer to be available.|  
|**Log write waits**|Statistics for processes waiting for log buffer to be written.|  
|**Memory grant queue waits**|Statistics for processes waiting for memory grant to become available.|  
|**Network IO waits**|Statistics relevant to wait on network I/O.|  
|**Non-Page latch waits**|Statistics relevant to non-page latches.|  
|**Page IO latch waits**|Statistics relevant to page I/O latches.|  
|**Page latch waits**|Statistics relevant to page latches, not including I/O latches.|  
|**Thread-safe memory objects waits**|Statistics for processes waiting on thread-safe memory allocators.|  
|**Transaction ownership waits**|Statistics relevant to processes synchronizing access to transaction.|  
|**Wait for the worker**|Statistics relevant to processes waiting for worker to become available.|  
|**Workspace synchronization waits**|Statistics relevant to processes synchronizing access to workspace.|  
  
 Each counter in the object contains the following instances:  
  
|Item|Description|  
|----------|-----------------|  
|**Average wait time (ms)**|Average time for the selected type of wait.|  
|**Cumulative wait time (ms) per second**|Aggregated wait time per second, for the selected type of wait.|  
|**Waits in progress**|Number of processes currently waiting on the following type.|  
|**Waits started per second**|Number of waits started per second of the selected type of wait.|  
  
## See Also  
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)