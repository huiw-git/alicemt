---
title: Report Server Status  - Reporting Services Native mode (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
robots: noindex,nofollow
---
# Report Server Status  - Reporting Services Native mode (Configuration Manager)
  Use this page to view information about the report server instance to which you are currently connected. This page is the start page for report server configuration. Additional pages are available to configure URLs, the service account, the report server database, report server e\-mail delivery, scale\-out deployment, and encryption keys.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
 To open this page, start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager and connect to the report server instance. For more information, see [Reporting Services Configuration Manager \(SSRS Native Mode\)](assetId:///63519ef4-e68a-42fb-9cf7-31228ea4e434).  
  
> [!TIP]  
>  The[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager \(RSConfigTool.exe\) is installed with a privilege level of “highestAvailable”. This behavior is by design. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] WMI APIs. Some of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] WMI communication requires a higher level or administrative of privileges.  
  
 If you connect to the report server and all of the page links are grayed out, verify that the Report Server service is started. The **Report Service Status:** Should be “Started”. You can also use the Services console application in Administrator Tools to check service status.  
  
## Options  
 **SQL Server Instance**  
 Displays information about the report server instance to which you are currently connected. Report server instance names are based on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] named instances. The default instance is MSSQLSERVER. A named instance will be a value that you specified during setup. For more information about instances, see [Work with Multiple Versions and Instances of SQL Server](../../Topics\TopicNameNotContainA/Work-with-Multiple-Versions-and-Instances-of-SQL-Server.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
> [!NOTE]  
>  In SQL Server Express with Advanced Services, the default instance is SQLExpress.  
  
 **Instance ID**  
 Corresponds to a folder on the file system that stores program files for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance to which you are connected. The **Instance ID** value is assigned by Setup in the format *component*.*instance*, where *component* is a value that signifies a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] component and *instance* is an instance name. The default instance name is MSSQLSERVER. For example, if you install default instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components, the corresponding folder names are the following:  
  
-   MSSQL13.MSSQLSERVER  
  
-   MSAS13.MSSQLSERVER  
  
-   MSRS13.MSSQLSERVER  
  
 If you install a second instance of a component that you already installed, such as the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], and you name the instance Contoso, the **Instance ID** is MSSQL13.Contoso.  
  
 **Edition**  
 Displays edition information. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Product Version**  
 Displays the version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] that you installed.  
  
 **Report Server Database**  
 Displays the name of the report server database that stores application data for the current report server instance.  
  
 **Report Server Mode**  
 This should always show a value of **Native**. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] configuration manager only supports Native mode report servers. If you see a value of **SharePoint integrated mode**, it may indicate your Native mode deployment is not configured correctly, and you need to connect to a Native mode report catalog. Use the **Database** page of Configuration Manager to change the database and either create a new database or connect to an existing native mode report server database catalog.  
  
 **Server Status**  
 Shows whether the Report Server service is running.  
  
 **Start**  
 Starts the Report Server service. Restarting the service is necessary after some configuration changes \(for example, when reconfiguring a report server after a computer name change\). If you reconfigure the URL reservations, the service will restart automatically. The restart is required to pick up the changes.  
  
 **Stop**  
 Stops the Report Server service. Stopping the service causes the report server to stop working. For more information, see [Start and Stop the Report Server Service](../../Topics\TopicNameNotContainA/Start-and-Stop-the-Report-Server-Service.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
## See Also  
 [Reporting Services Configuration Manager Help Topics](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)   
 [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md)   
 [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../Topic/Initialize%20a%20Report%20Server%20\(SSRS%20Configuration%20Manager\).md)  
  
  