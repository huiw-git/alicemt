---
title: SQL Server, Query Store Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
---
# SQL Server, Query Store Object
  The Query Store object provides counters to monitor resource utilization of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to store query texts, execution plans and runtime stats for objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements, and triggers.  
  
 This table describes are the **SQLServer:Query Store**counters.  
  
|SQL Server Query Store counters|Description|  
|-------------------------------------|-----------------|  
|**Query Store CPU usage**|Indicates Query Stores usage of the CPU.|  
|**Query Store logical reads**|Indicates the number of logical reads made by the Query Store.|  
|**Query Store logical writes**|Indicates how much data is being queued to be flushed from the Query Store. The frequency and delay of adding items \(that represent runtime stats\) to the queue is controlled by Data Flush Interval setting.|  
|**Query Store physical reads**|Indicates the number of physical reads made by the Query Store.|  
  
 Each counter in the object contains the following instances:  
  
|Query Store instance|Description|  
|--------------------------|-----------------|  
|**\_Total**|Information for the Query Store for this instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|\<database name\>|Query Store information for this database.|  
  
## See Also  
 [Monitoring Performance By Using the Query Store](../../Topics\TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md)   
 [Query Store Stored Procedures &#40;Transact-SQL&#41;](../Topic/Query%20Store%20Stored%20Procedures%20\(Transact-SQL\).md)   
 [Query Store Catalog Views &#40;Transact-SQL&#41;](../Topic/Query%20Store%20Catalog%20Views%20\(Transact-SQL\).md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  