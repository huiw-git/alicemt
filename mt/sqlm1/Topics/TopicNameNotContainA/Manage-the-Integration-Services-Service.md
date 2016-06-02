---
title: Manage the Integration Services Service
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
---
# Manage the Integration Services Service
    
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 When you install the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] component of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is also installed. By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is started and the startup type of the service is set to automatic. However, you must also install [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to use the service to manage stored and running [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages.  
  
> [!NOTE]  
>  You cannot connect to an instance of the [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service from the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] version of [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]. That is, in the **Connect to Server** dialog box, you cannot enter the name of a server on which only the [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] version of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is running. However, you can edit the configuration file for the service and thereby manage packages that are stored in an instance of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] from the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] version of [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]. For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
 You can only install a single instance of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service on a computer. The service is not specific to a particular instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. You connect to the service by using the name of the computer on which it is running.  
  
 You can manage the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service by using one of the following Microsoft Management Console \(MMC\) snap\-ins: SQL Server Configuration Manager or Services. Before you can manage packages in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you must make sure that the service is started.  
  
 By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is configured to manage packages in the msdb database of the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] that is installed at the same time as [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. If an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is not installed at the same time, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is configured to manage packages in the msdb database of the local, default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. To manage packages that are stored in a named or remote instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], or in multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], you have to modify the configuration file for the service. For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
 By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is configured to stop running packages when the service is stopped. However, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service does not wait for packages to stop and some packages may continue running after the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is stopped.  
  
 If the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is stopped, you can continue to run packages using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard, the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, the Execute Package Utility, and the **dtexec** command prompt utility \(dtexec.exe\). However, you cannot monitor the running packages.  
  
 By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service runs in the context of the NETWORK SERVICE account.  
  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service writes to the Windows event log. You can view service events in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. You can also view service events by using the Windows Event Viewer.  
  
### To set properties of Integration Services service using the Services snap\-in  
  
-   [Set the Properties of the Integration Services Service](../../Topics\TopicNameNotContainA/Set-the-Properties-of-the-Integration-Services-Service.md)  
  
### To view service events for Integration Services service  
  
-   [View Events for the Integration Services Service](../../Topics\TopicNameNotContainA/View-Events-for-the-Integration-Services-Service.md)  
  
## See Also  
 [Integration Services Service &#40;SSIS Service&#41;](../Topic/Integration%20Services%20Service%20\(SSIS%20Service\).md)   
 [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md)   
 [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md)   
 [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md)   
 [Execution of Projects and Packages](../../Topics\TopicNameNotContainA/Execution-of-Projects-and-Packages.md)  
  
  