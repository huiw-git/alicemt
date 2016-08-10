---
title: "SQL Server, Memory Node"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server, Memory Node
The **Memory Node** object in Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides counters to monitor server memory usage on NUMA nodes.  
  
## Memory Node Counters  
 This table describes the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **Memory Node** counters.  
  
|SQL Server Memory Manager counters|Description|  
|----------------------------------------|-----------------|  
|**Database Node Memory (KB)**|Specifies the amount of memory the server is currently using on this node for database pages.|  
|**Free Node Memory (KB)**|Specifies the amount of memory the server is not using on this node.|  
|**Foreign Node Memory (KB)**|Specifies the amount of non NUMA-local memory on this node.|  
|**Stolen Memory Node (KB)**|Specifies the amount of memory the server is using on this node for purposes other than database pages.|  
|**Target Node Memory**|Specifies the ideal amount of memory for this node.|  
|**Total Node Memory**|Indicates the total amount of memory the server has committed on this node.|  
  
## See Also  
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)   
 [SQL Server, Buffer Manager Object](../../Topics/TopicNameNotContainA/SQL-Server--Buffer-Manager-Object.md)   
 [sys.dm_os_performance_counters](assetId:///a1c3e892-cd48-40d4-b6be-2a9246e8fbff)