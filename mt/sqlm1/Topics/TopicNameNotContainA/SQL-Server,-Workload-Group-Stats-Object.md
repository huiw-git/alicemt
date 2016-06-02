---
title: SQL Server, Workload Group Stats Object
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
---
# SQL Server, Workload Group Stats Object
  The SQLServer:Workload Group Stats object contains performance counters that report information about Resource Governor workload group statistics.  
  
 Each active workload group creates an instance of the SQLServer:Workload Group Stats performance object that has the same instance name as the Resource Governor workload group name. The following table describes counters supported on this instance.  
  
|Counter name|Description|  
|------------------|-----------------|  
|Active parallel threads|The current count of parallel threads usage.|  
|Active requests|The number of requests that are currently running in this workload group. This should be equivalent to the count of rows from sys.dm\_exec\_requests filtered by group ID.|  
|Blocked requests|The current number of blocked requests in the workload group. This can be used to determine workload characteristics.|  
|CPU  delayed %|System CPU delayed for all requests in the specified instance of the performance object as a percentage of the total time active.|  
|CPU  effective %|System CPU usage by all requests in the specified instance of the performance object as a percentage of the total time active.|  
|CPU usage %|The CPU bandwidth usage by all requests in this workload group measured relative to the computer and normalized to all the CPUs on the system. This value will change as the amount of CPU available to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process changes. It is not normalized to what the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process receives.|  
|CPU  violated %|The difference between the CPU reservation and the effective scheduling percentage.|  
|Max request CPU time \(ms\)|The maximum CPU time, in milliseconds, used by a request currently running in the workload group.|  
|Max request memory grant \(KB\)|The maximum value of memory grant, in kilobytes \(KB\), for a query.|  
|Query optimizations\/sec|The number of query optimizations that have happened in this workload group per second. This can be used to determine workload characteristics.|  
|Queued requests|The current number of queued requests that is waiting to be picked up. This count can be non\-zero if throttling occurs after the GROUP\_MAX\_REQUESTS limit is reached.|  
|Reduced memory grants\/sec|The number of queries that are getting less than ideal amount of memory grants per second.|  
|Requests completed\/sec|The number of requests that have completed in this workload group. This number is cumulative.|  
|Suboptimal plans\/sec|The number of suboptimal plans that are generated in this workload group per second.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [SQL Server, Resource Pool Stats Object](../../Topics\TopicNameNotContainA/SQL-Server,-Resource-Pool-Stats-Object.md)   
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)  
  
  