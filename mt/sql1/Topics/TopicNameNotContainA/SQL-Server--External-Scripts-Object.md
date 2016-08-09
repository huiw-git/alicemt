---
title: "SQL Server, External Scripts Object"
ms.custom: na
ms.date: 2016-03-21
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: language-reference
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
caps.latest.revision: 8
manager: jhubbard
---
# SQL Server, External Scripts Object
The **SQLServer:External Scripts** object in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides counters to monitor the actions associated with executing external scripts. For information about executing external scripts, see [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df).  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **External Scripts** counters.  
  
|SQL Server External Scripts counters|Description|  
|------------------------------------------|-----------------|  
|**Execution Errors**|The number of errors in executing external scripts.|  
|**Implied Auth. Logins**|The number of logins from satellite processes authenticated by using implied authentication.|  
|**Parallel Executions**|The number of external scripts executed with @parallel = 1.|  
|**SQL CC Executions**|The number of external scripts executed using SQL Compute Context.|  
|**Streaming Executions**|The number of external scripts executed with the @r_rowsPerRead parameter.|  
|**Total Execution Time (ms)**|The total time spent in executing external scripts.|  
|**Total Executions**|The number of external scripts executed.|  
  
## See Also  
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)   
 [sys.resource_governor_external_resource_pools (Transact-SQL)](assetId:///75063e36-a91b-496f-9936-88f3d57bd447)   
 [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](assetId:///e32fac49-5161-47c0-8540-af3fe730c00c)