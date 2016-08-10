---
title: "Security Requirements for Managing Services"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Security Requirements for Managing Services
To manage the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. Manage the services on clustered servers with the Cluster Administrator.  
  
 To manage the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role. Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.  
  
> [!NOTE]  
>  To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions. For information about the required permissions, see [Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
## Windows Management Instrumentation  
 SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] use Windows Management Instrumentation (WMI) to display and modify some of the server properties. To manage services and obtain the status of the services, the user must have rights to access the WMI object. In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], the following server property pages use WMI:  
  
-   Autostart Services  
  
-   Startup Parameters  
  
-   Security  
  
-   Misc Server Settings  
  
## Related Tasks  
 [How to: Configure WMI to Show Server Status in SQL Server Tools](assetId:///7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
## Related Content  
 [WMI Provider for Configuration Management Concepts](assetId:///7e41db24-b915-4eb8-a1d6-e6948ee915b7)