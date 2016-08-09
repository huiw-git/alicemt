---
title: "SQL Server, Query Store Object"
ms.custom: na
ms.date: 2016-03-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
caps.latest.revision: 8
manager: jhubbard
---
# SQL Server, Query Store Object
The Query Store object provides counters to monitor resource utilization of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to store query texts, execution plans and runtime stats for objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, and triggers.  
  
 This table describes are the **SQLServer:Query Store**counters.  
  
|SQL Server Query Store counters|Description|  
|-------------------------------------|-----------------|  
|**Query Store CPU usage**|Indicates Query Stores usage of the CPU.|  
|**Query Store logical reads**|Indicates the number of logical reads made by the Query Store.|  
|**Query Store logical writes**|Indicates how much data is being queued to be flushed from the Query Store. The frequency and delay of adding items (that represent runtime stats) to the queue is controlled by Data Flush Interval setting.|  
|**Query Store physical reads**|Indicates the number of physical reads made by the Query Store.|  
  
 Each counter in the object contains the following instances:  
  
|Query Store instance|Description|  
|--------------------------|-----------------|  
|**_Total**|Information for the Query Store for this instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|  
|<database name\>|Query Store information for this database.|  
  
## See Also  
 [Monitoring Performance By Using the Query Store](../../Topics/TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md)   
 [Query Store Stored Procedures (Transact-SQL)](assetId:///9bddbb74-e67a-43e3-b89e-896c498e53cb)   
 [Query Store Catalog Views (Transact-SQL)](assetId:///43d5466a-89e2-4e59-b87e-a2a78e59a1de)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)