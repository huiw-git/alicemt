---
title: SQL Server, External Scripts Object
ms.custom: na
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
---
# SQL Server, External Scripts Object
  The **SQLServer:External Scripts** object in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides counters to monitor the actions associated with executing external scripts. For information about executing external scripts, see [sp_execute_external_script &#40;Transact-SQL&#41;](../Topic/sp_execute_external_script%20\(Transact-SQL\).md).  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **External Scripts** counters.  
  
|SQL Server External Scripts counters|Description|  
|------------------------------------------|-----------------|  
|**Execution Errors**|The number of errors in executing external scripts.|  
|**Implied Auth. Logins**|The number of logins from satellite processes authenticated by using implied authentication.|  
|**Parallel Executions**|The number of external scripts executed with @parallel \= 1.|  
|**SQL CC Executions**|The number of external scripts executed using SQL Compute Context.|  
|**Streaming Executions**|The number of external scripts executed with the @r\_rowsPerRead parameter.|  
|**Total Execution Time \(ms\)**|The total time spent in executing external scripts.|  
|**Total Executions**|The number of external scripts executed.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../Topic/sys.resource_governor_external_resource_pools%20\(Transact-SQL\).md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../Topic/sys.dm_resource_governor_external_resource_pool_affinity%20\(Transact-SQL\).md)  
  
  