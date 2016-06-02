---
title: Database  - Reporting Services Native mode (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
robots: noindex,nofollow
---
# Database  - Reporting Services Native mode (Configuration Manager)
  Use the Database page to create and configure the report server databases that provide internal storage for one or more report server instances. If you are configuring a report server to use a remote report server database, you must use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to create the database.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
 Creating a report server database and configuring the connection is a multi\-step process. To guide you through the steps, this page provides Wizards for each type of task. Permissions and logins are created or updated for you. You can monitor the status of each step in the Progress page. If an error occurs, you can click the error for information on how to resolve it.  
  
 A report server database must support a specific server mode. The default mode is native mode, but you can also create a report server database for SharePoint integrated mode if you are running a report server in a larger deployment of a SharePoint product or technology. For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md).  
  
 To open this page, start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager and click **Database** in the navigation pane. For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
## Options  
 **SQL Server Name**  
 In Current Report Server Database, **SQL Server Name** specifies the name of the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] that runs the report server database. You can use a default or named instance on a local or remote computer.  
  
 **Database Name**  
 Specifies the name of the report server database that stores server data.  
  
 **Report Server Mode**  
 Indicates whether the report server database supports native mode or SharePoint integrated mode. For more information, see [Reporting Services Report Server](../../Topics\TopicNameNotContainA/Reporting-Services-Report-Server.md).  
  
 **Change Database**  
 Start a wizard that guides you through all of the steps required for creating or selecting a report server database.  
  
 **Credential Type**  
 Specifies credentials that the report server uses to connect to the report server database. Credential types you can specify include the service account, a Windows domain user, Windows local user, or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login. For more information about selecting credentials, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
 **User Name**  
 Specifies a domain user account if you are using Windows credentials, or a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login if you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credentials. If you are using Windows credentials, specify them in this format: *\<domain\>\\\<account\>*.  
  
 **Password**  
 Specifies the password for the account.  
  
 **Change Credentials**  
 Start a wizard that guides you through all of the steps required for selecting a different account or updating the password on the account that is used to connect to the report server database.  
  
## See Also  
 [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Reporting Services Configuration Manager Help Topics](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)   
 [Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)  
  
  