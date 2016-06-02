---
title: Change Database Wizard (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
robots: noindex,nofollow
---
# Change Database Wizard (Configuration Manager)
  The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager provides the Change Database Wizard to guide you through the steps of creating a new report server database or selecting an existing report server database to use with the current report server instance.  
  
 If you select a report server database from an earlier version, it will be upgraded to match the version of the report server instance to which it is connected. When the service starts, it checks the database version and upgrades it to the current schema automatically.  
  
 To start the wizard, click **Change Database** on the Database page in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. For instructions on how to start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
## Options  
 **Action**  
 Select the task you want to perform. You can create a new database in native or SharePoint integrated mode. Or, you can select an existing report server database to use with the current report server instance.  
  
 **Database Server**  
 Specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance that hosts the report server database. You can use a default or named instance on a local or remote computer. If you are connecting to a named instance, enter the server name in this format: \<*server*\>\\\<*instance*\>.  
  
 To connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance, you must use credentials that have permission to log on to the server and update database information. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you must specify a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login. You cannot specify different Windows credentials. If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager.  
  
 Connecting to a remote instance requires that you first enable that instance for remote connections. Some versions and editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] do not enable remote connections by default. To confirm whether remote connections are allowed, use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager and confirm that the TCP\/IP and Named Pipes protocols are enabled. If the remote instance is also a named instance, verify that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service is enabled and running on the target server. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser provides the port number that is used by the named instance to the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager.  
  
 **Database**  
 Specifies the name of the report server database that stores server data. You can specify an existing database or create a new database.  
  
 Properties that are used to create a new database appear in the Wizard when you select **Create new database** on the Actions page. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager creates two databases that are bound by name: a database to contain static data and a temporary database for storing session and work data. For more information, see [Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 You can also choose an existing report server database. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager does not filter out invalid databases. Valid databases are based on the report server database schema \(you cannot select a database that is missing the necessary tables, views, or stored procedures\). If you choose a database that was created for an earlier version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], the database will be upgraded to the current format.  
  
 **Language**  
 This value is set only when you are creating a new report server database.  
  
 With this value, you specify the language in which role definitions and descriptions are created. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides a role\-based authorization model that includes a set of predefined roles. These roles are created once in the language you specify. Role names and descriptions never appear in other languages, even if you connect to the report server using a browser that has culture or language settings that are supported by the server. The language that you specify also determines the language used to create the name of the My Reports folder and the Users folders that are part of the My Reports feature.  
  
 **Server Mode**  
 A report server database supports either native mode or SharePoint integrated mode. The modes are mutually exclusive.  
  
 If you are creating a new report server database, you must specify a mode. The mode you select determines the structure of the report server database and sets the **SharePointIntegrated** report server system property to **true** or **false**.  
  
 If you are selecting a different report server database, the mode of the current database is displayed so that you know how the current database is used.  
  
 **Credentials**  
 Specifies the account by which the report server connects to the report server database. Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login defined on the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance you are using to host the report server, or a Windows account. If you are using a Windows account, you can specify a local account \(*\<computername\>\\\<username\>*\) if the report server and the database are on the same computer, or a domain user account \(*\<domain\>\\\<username\>*\) if they are on different computers in the same domain.  
  
 The report server will create a database login and assign database permissions for the account you specify.  
  
 The report server does not create the account itself. The account you specify must already exist and it must be valid for your deployment configuration. Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.  
  
 If the computer is in a different or non\-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login. For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
 **Summary**  
 Verify the settings before Setup configures the connection.  
  
 **Progress and Finish**  
 Monitor the progress of each task.  
  
## See Also  
 [Database  - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/Database%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)   
 [Change Credentials Wizard &#40;Configuration Manager&#41;](../Topic/Change%20Credentials%20Wizard%20\(Configuration%20Manager\).md)   
 [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Reporting Services Configuration Manager Help Topics](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)  
  
  