---
title: "SQL Server, Broker Activation Object"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server, Broker Activation Object
The **SQLServer:BrokerActivation** performance object contains performance counters that report information on stored procedure activation. The table below lists the counters that this object contains.  
  
|SQL Server Broker Activation counters|Description|  
|-------------------------------------------|-----------------|  
|**Stored Procedures Invoked/sec**|This counter reports the total number of activation stored procedures invoked by all queue monitors in the instance per second.|  
|**Task Limit Reached**|This counter reports the total number of times that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.|  
|**Task Limit Reached/sec**|This counter reports the number of times per second that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.|  
|**Tasks Aborted/sec**|This counter reports the number of activation stored procedure tasks that end with an error, or are aborted by a queue monitor for failing to receive messages.|  
|**Tasks Running**|This counter reports the number of activation stored procedures that are currently running.|  
|**Tasks Started/sec**|This counter reports the number of activation stored procedures started per second by all queue monitors in the instance.|  
  
## See Also  
 [Monitoring Resource Usage (System Monitor)](assetId:///17e6f87f-8f56-489d-9aed-216afc8ef310)   
 [sys.dm_broker_queue_monitors](assetId:///401207dc-ef4a-4a3f-879c-76dcbb52d6bc)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)