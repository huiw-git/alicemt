---
title: Security Requirements for Managing Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
---
# Security Requirements for Managing Services
  To manage the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Manage the services on clustered servers with the Cluster Administrator.  
  
 To manage the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role. Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.  
  
> [!NOTE]  
>  To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions. For information about the required permissions, see [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
## Windows Management Instrumentation  
 SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] use Windows Management Instrumentation \(WMI\) to display and modify some of the server properties. To manage services and obtain the status of the services, the user must have rights to access the WMI object. In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], the following server property pages use WMI:  
  
-   Autostart Services  
  
-   Startup Parameters  
  
-   Security  
  
-   Misc Server Settings  
  
## Related Tasks  
 [Configure WMI to Show Server Status in SQL Server Tools](../Topic/Configure%20WMI%20to%20Show%20Server%20Status%20in%20SQL%20Server%20Tools.md)  
  
## Related Content  
 [WMI Provider for Configuration Management Concepts](../Topic/WMI%20Provider%20for%20Configuration%20Management%20Concepts.md)  
  
  