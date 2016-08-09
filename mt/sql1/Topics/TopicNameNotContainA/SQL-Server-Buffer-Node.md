---
title: "SQL Server:Buffer Node"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server:Buffer Node
The **Buffer Node** object provides counters that complement counters provided by the **Buffer Manager** object. It allows you to monitor the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] buffer pool page distribution for each non-uniform memory access (NUMA) node. There is an instance of the **Buffer Node** object for each NUMA node in use. On non-NUMA architecture, there will be a single instance of the **Buffer Node** object.  
  
## Buffer Node Performance Objects  
 This table describes the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **Buffer Node** performance objects.  
  
|SQL Server Buffer Node counters|Description|  
|-------------------------------------|-----------------|  
|**Database pages**|Indicates the number of pages in the buffer pool on this node with database content.|  
|**Page life expectancy**|Indicates the minimum number of seconds a page will stay in the buffer pool on this node without references.|  
|**Local Node page lookups/sec**|Indicates the number of lookup requests from this node which were satisfied from this node.|  
|**Remote Note page lookups/sec**|Indicates the number of lookup requests from this node which were satisfied from other nodes.|  
  
 If SQL Server is running on non-NUMA hardware, the counters of **Buffer Node** and **Buffer Manager** objects should match.  
  
 On NUMA hardware, sums of respective counters of all **Buffer Nodes** should match their counterparts of **Buffer Manager**.  
  
> [!NOTE]  
>  The counter values and sums may not match precisely due to the dynamic nature of the counters and the sampling accuracy.  
  
## See Also  
 [SQL Server, Buffer Manager Object](../../Topics/TopicNameNotContainA/SQL-Server--Buffer-Manager-Object.md)   
 [Server Memory Server Configuration Options](../../Topics/TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)   
 [sys.dm_os_performance_counters](assetId:///a1c3e892-cd48-40d4-b6be-2a9246e8fbff)