---
title: MSSQL_ENG021797
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
---
# MSSQL_ENG021797
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21797|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|'%s' must be a valid Windows Login in the form: 'MACHINE\\Login' or 'DOMAIN\\Login'. Please see the documentation for '%s'.|  
  
## Explanation  
 This error is raised by the following replication stored procedures if the value specified for the **@job\_login** parameter is null or not valid. This error can occur if a member of the **db\_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The security model changed in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], and these scripts must be updated.  
  
-   [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md)  
  
-   [sp_addqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addqreader_agent%20\(Transact-SQL\).md)  
  
-   [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md)  
  
-   [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpushsubscription_agent%20\(Transact-SQL\).md)  
  
-   [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md)  
  
-   [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepushsubscription_agent%20\(Transact-SQL\).md)  
  
-   [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md)  
  
 These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db\_owner** fixed database role in the appropriate database. The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the agent runs. For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified \(if an account is specified, it must be valid\); agents run under the context of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service account at the appropriate server. Although the account is not required, it is a security best practice to specify a separate account for the agents. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## User Action  
 Ensure you specify a valid Windows account for the **@job\_login** parameter of each procedure. If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]. For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](../Topic/Upgrade%20Replication%20Scripts%20\(Replication%20Transact-SQL%20Programming\).md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  