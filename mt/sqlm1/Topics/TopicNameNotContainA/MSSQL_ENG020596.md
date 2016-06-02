---
title: MSSQL_ENG020596
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
---
# MSSQL_ENG020596
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20596|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Only '%s' or members of db\_owner can drop the anonymous agent.|  
  
## Explanation  
 You do not have sufficient permissions to drop the agent for the anonymous subscription. The login used when calling [sp_dropanonymousagent &#40;Transact-SQL&#41;](../Topic/sp_dropanonymousagent%20\(Transact-SQL\).md) must be a member of the **sysadmin** fixed server role at the Distributor or **db\_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.  
  
## User Action  
 Login with the appropriate credentials, and execute **sp\_dropanonymousagent**.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  