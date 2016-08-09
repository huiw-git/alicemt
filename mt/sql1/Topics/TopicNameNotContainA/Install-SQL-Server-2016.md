---
title: "Install SQL Server 2016"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-03-01
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 44
caps.handback.revision: 0
manager: jhubbard
---
# Install SQL Server 2016
This topic provides an overview of different installation options we have for installing [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. For more information about the various [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] components that can be installed, and the installation process, see [Installation for SQL Server 2016](../../Topics/TopicNameNotContainA/Installation-for-SQL-Server-2016.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is a 64-bit application. Editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] are installed either through the Installation Wizard, a command prompt, or through sysprep. For more information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] components, see [Editions and Components of SQL Server 2016](../../Topics/TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md) and [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup. To install sample databases and sample code for non-Express editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see the [CodePlex Web site](http://go.microsoft.com/fwlink/?LinkId=87843). To read about support for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)], see [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391).  
  
 Before you install [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], review installation requirements, system configuration checks, and security considerations. For more information, see [Planning a SQL Server Installation](../../Topics/TopicNameContainA/Planning-a-SQL-Server-Installation.md). Review the topics in the next section for information about various installation scenarios for [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
## In This Section  
  
### Installing [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] Components  
  
|Topic|Description|  
|-----------|-----------------|  
|[Install SQL Server Database Engine](../../Topics/TopicNameNotContainA/Install-SQL-Server-Database-Engine.md)|Describes how to install and configure the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)].|  
|[Install SQL Server Replication](../../Topics/TopicNameNotContainA/Install-SQL-Server-Replication.md)|Describes how to install and configure [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Replication.|  
|[Install Distributed Replay - Overview](../../Topics/TopicNameNotContainA/Install-Distributed-Replay---Overview.md)|Lists down the topics to install the Distributed Replay feature.|  
|[Install SQL Server Management Tools with SSMS](../../Topics/TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md)|Describes how to install and configure [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] management tools.|  
|[Install SQL Server PowerShell](../../Topics/TopicNameNotContainA/Install-SQL-Server-PowerShell.md)|Describes the considerations for installing [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell components.|  
  
### Installing [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]  
  
|Title|Description|  
|-----------|-----------------|  
|[Install SQL Server 2016 on Server Core](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md)|Review this topic to install [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] on Windows Server Core.|  
|[Check Parameters for the System Configuration Checker](../../Topics/TopicNameNotContainA/Check-Parameters-for-the-System-Configuration-Checker.md)|Discusses the function of the System Configuration Checker (SCC).|  
|[Install SQL Server 2016 from the Installation Wizard (Setup)](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Installation-Wizard--Setup-.md)|Procedural topic for a typical [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation by using the Installation Wizard.|  
|[Install SQL Server 2016 from the Command Prompt](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)|Procedural topic that provides sample syntax and installation parameters for running unattended Setup.|  
|[Install SQL Server 2016 Using a Configuration File](../../Topics/TopicNameContainA/Install-SQL-Server-2016-Using-a-Configuration-File.md)|Procedural topic that provides sample syntax and installation parameters for running Setup through a configuration file.|  
|[Install SQL Server 2016 Using SysPrep](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-Using-SysPrep.md)|Procedural topic that provides sample syntax and installation parameters for running Setup through SysPrep.|  
|[Add Features to an Instance of SQL Server 2016 (Setup)](../../Topics/TopicNameNotContainA/Add-Features-to-an-Instance-of-SQL-Server-2016--Setup-.md)|Procedural topic for updating components of an existing instance of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].|  
|[Repair a Failed SQL Server 2016 Installation](../../Topics/TopicNameContainA/Repair-a-Failed-SQL-Server-2016-Installation.md)|Procedural topic for repairing a corrupt [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] installation.|  
|[Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../../Topics/TopicNameContainA/Rename-a-Computer-that-Hosts-a-Stand-Alone-Instance-of-SQL-Server.md)|Procedural topic for updating system metadata that is stored in sys.servers.|  
|[Install SQL Server 2016 Servicing Updates](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-Servicing-Updates.md)|Procedural topic for installing updates for SQL Server 2016.|  
|[View and Read SQL Server Setup Log Files](../../Topics/TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md)|Procedural topic for checking errors in setup log files.|  
|[Validate a SQL Server Installation](../../Topics/TopicNameContainA/Validate-a-SQL-Server-Installation.md)|Review the use of the SQL Discovery report to verify the version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] features installed on the computer.|  
  
### Configuration Topics  
  
|Topic|Description|  
|-----------|-----------------|  
|[Configure the Windows Firewall to Allow SQL Server Access](../../Topics/TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md)|This topic provides an overview of firewall configuration and how to configure the Windows firewall.|  
|[Configure a Multi-Homed Computer for SQL Server Access](../../Topics/TopicNameContainA/Configure-a-Multi-Homed-Computer-for-SQL-Server-Access.md)|This topic describes how to configure [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows Firewall with Advanced Security to provide for network connections to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in a multi-homed environment.|  
|[Configure the Windows Firewall to Allow Analysis Services Access](../../Topics/TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-Analysis-Services-Access.md)|You can follow the steps provided in this topic to configure both port and firewall settings to allow access to [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] or [!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] for SharePoint.|  
  
## Related Sections  
 [Install SQL Server 2016 Business Intelligence Features](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-Business-Intelligence-Features.md)  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] features that are part of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] BI platform include [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)], [!INCLUDE[ssDQSnoversion](../../Topics/TopicNameContainA/tokens/ssDQSnoversion_md.md)], and several client applications used for creating or working with analytical data. This section of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup documentation explains how to install [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)], [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], [!INCLUDE[ssDQSnoversion](../../Topics/TopicNameContainA/tokens/ssDQSnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)].  
  
 [SQL Server Failover Cluster Installation](../../Topics/TopicNameNotContainA/SQL-Server-Failover-Cluster-Installation.md)  
 This section of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] failover cluster.  
  
## See Also  
 [Planning a SQL Server Installation](../../Topics/TopicNameContainA/Planning-a-SQL-Server-Installation.md)   
 [Upgrade to SQL Server 2016](../../Topics/TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)   
 [Uninstall SQL Server 2016](../../Topics/TopicNameNotContainA/Uninstall-SQL-Server-2016.md)   
 [High Availability Solutions (SQL Server)](../../Topics/TopicNameNotContainA/High-Availability-Solutions--SQL-Server-.md)