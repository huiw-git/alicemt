---
title: Surface Area Configuration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
---
# Surface Area Configuration
  In the default configuration of new installations of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], many features are not enabled. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] selectively installs and starts only key services and features, to minimize the number of features that can be attacked by a malicious user. A system administrator can change these defaults at installation time and also selectively enable or disable features of a running instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Additionally, some components may not be available when connecting from other computers until protocols are configured.  
  
> [!NOTE]  
>  Unlike new installations, no existing services or features are turned off during an upgrade, but additional surface area configuration options can be applied after the upgrade is completed.  
  
## Protocols, Connection, and Startup Options  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to start and stop services, configure the startup options, and enable protocols and other connection options.  
  
#### To start SQL Server Configuration Manager  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
    -   Use the **SQL Server Services** area to start components and configure the automatic starting options.  
  
    -   Use the **SQL Server Network Configuration** area to enable connection protocols, and connection options such as fixed TCP\/IP ports, or forcing encryption.  
  
 For more information, see [SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md). Remote connectivity can also depend upon the correct configuration of a firewall. For more information, see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
## Enabling and Disabling Features  
 Enabling and disabling [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features can be configured using facets in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
#### To configure surface area using facets  
  
1.  In [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] connect to a component of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
2.  In Object Explorer, right\-click the server, and then click **Facets**.  
  
3.  In the **View Facets** dialog box, expand the **Facet** list, and select the appropriate **Surface Area Configuration** facet \(**Surface Area Configuration**, **Surface Area Configuration for Analysis Services**, or **Surface Area Configuration for Reporting Services**\).  
  
4.  In the **Facet properties** area, select the values that you want for each property.  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
 To periodically check the configuration of a facet, use Policy\-Based Management. For more information about Policy\-Based Management, see [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md).  
  
 You can also set [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] options using the **sp\_configure** stored procedure. For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
 To change the **EnableIntegrated Security** property of [!INCLUDE[ssRS](../../Token\Other/ssRS_md.md)], use the property settings in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. To change the **Schedule events and report delivery** property and the **Web service and HTTP access** property, edit the **RSReportServer.config** configuration file.  
  
## Command\-prompt Options  
 Use the **Invoke\-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell cmdlet to invoke Surface Area Configuration Policies. For more information, see [Use the Database Engine cmdlets](../../Topics\TopicNameNotContainA/Use-the-Database-Engine-cmdlets.md).  
  
## SOAP and Service Broker Endpoints  
 To turn endpoints off, use Policy\-Based Management. To create and alter the properties of endpoints, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md) and [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md).  
  
## Related Content  
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  