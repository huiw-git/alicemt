---
title: MSSQL_ENG021798
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
---
# MSSQL_ENG021798
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21798|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The '%s' agent job must be added through '%s' before continuing. Please see the documentation for '%s'.|  
  
## Explanation  
 To create a publication, you must be a member of the **sysadmin** fixed server role on the Publisher or a member of the **db_owner** fixed database role in the publication database. If you are a member of the **db_owner** role, this error is raised if:  
  
-   You run scripts from [!INCLUDE[ssVersion2000](../../Topics/TopicNameContainA/includes/ssVersion2000_md.md)]. The security model changed in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/includes/ssVersion2005_md.md)], and these scripts must be updated.  
  
-   The stored procedure **sp_addpublication** is executed before executing [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md). This applies to all transactional publications.  
  
-   The stored procedure **sp_addpublication** is executed before executing [sp_addqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addqreader_agent%20\(Transact-SQL\).md). This applies to transactional publications that are enabled for queued updating subscriptions (a value of TRUE for the **@allow_queued_tran** parameter of **sp_addpublication**).  
  
 The stored procedures **sp_addlogreader_agent** and **sp_addqreader_agent** each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows account under which the agent runs. For users in the **sysadmin** role, agent jobs are created implicitly if **sp_addlogreader_agent** and **sp_addqreader_agent** are not executed; agents run under the context of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent service account at the Distributor. Although **sp_addlogreader_agent** and **sp_addqreader_agent** are not required for users in the **sysadmin** role, it is a security best practice to specify a separate account for the agents. For more information, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## User Action  
 Ensure you execute procedures in the correct order. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md). If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/includes/ssVersion2005_md.md)] and later versions. For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](../../Topics/TopicNameNotContainA/Upgrade-Replication-Scripts--Replication-Transact-SQL-Programming-.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)  
  
  