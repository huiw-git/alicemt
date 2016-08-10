---
title: "MSSQL_ENG020596"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG020596
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20596|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Only '%s' or members of db_owner can drop the anonymous agent.|  
  
## Explanation  
 You do not have sufficient permissions to drop the agent for the anonymous subscription. The login used when calling [sp_dropanonymousagent (Transact-SQL)](assetId:///4cb96efa-9358-44a3-a8ee-a7e181bed089) must be a member of the **sysadmin** fixed server role at the Distributor or **db_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.  
  
## User Action  
 Login with the appropriate credentials, and execute **sp_dropanonymousagent**.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)