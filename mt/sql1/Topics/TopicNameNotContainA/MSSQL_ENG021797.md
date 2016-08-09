---
title: "MSSQL_ENG021797"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG021797
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21797|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|'%s' must be a valid Windows Login in the form: 'MACHINE\Login' or 'DOMAIN\Login'. Please see the documentation for '%s'.|  
  
## Explanation  
 This error is raised by the following replication stored procedures if the value specified for the **@job_login** parameter is null or not valid. This error can occur if a member of the **db_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The security model changed in [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], and these scripts must be updated.  
  
-   [sp_addlogreader_agent (Transact-SQL)](assetId:///d83096b9-96ee-4789-bde0-940d4765b9ed)  
  
-   [sp_addqreader_agent (Transact-SQL)](assetId:///dc9f591a-e67e-4ba8-bf47-defd5eda0822)  
  
-   [sp_addpublication_snapshot (Transact-SQL)](assetId:///192b6214-df6e-44a3-bdd4-9d933a981619)  
  
-   [sp_addpushsubscription_agent (Transact-SQL)](assetId:///1fdd2052-50d8-4318-8aa7-fc635d5cad18)  
  
-   [sp_addpullsubscription_agent (Transact-SQL)](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b)  
  
-   [sp_addmergepushsubscription_agent (Transact-SQL)](assetId:///808a1925-be46-4999-8d69-b3a83010ec81)  
  
-   [sp_addmergepullsubscription_agent (Transact-SQL)](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb)  
  
 These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db_owner** fixed database role in the appropriate database. The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows account under which the agent runs. For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified (if an account is specified, it must be valid); agents run under the context of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent service account at the appropriate server. Although the account is not required, it is a security best practice to specify a separate account for the agents. For more information, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## User Action  
 Ensure you specify a valid Windows account for the **@job_login** parameter of each procedure. If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)]. For more information, see [Upgrade Replication Scripts (Replication Transact-SQL Programming)](../../Topics/TopicNameNotContainA/Upgrade-Replication-Scripts--Replication-Transact-SQL-Programming-.md).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)