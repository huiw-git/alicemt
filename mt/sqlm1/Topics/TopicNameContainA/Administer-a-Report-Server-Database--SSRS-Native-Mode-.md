---
title: Administer a Report Server Database (SSRS Native Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97b2e1b5-3869-4766-97b9-9bf206b52262
---
# Administer a Report Server Database (SSRS Native Mode)
  A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] deployment uses two [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] relational databases for internal storage. By default, the databases are named ReportServer and ReportServerTempdb. ReportServerTempdb is created with the primary report server database and is used to store temporary data, session information, and cached reports.  
  
 In [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], database administration tasks include backing up and restoring the report server databases and managing the encryption keys that are used to encrypt and decrypt sensitive data.  
  
 To administer the report server databases, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a variety of tools.  
  
-   To back up or restore the report server database, move a report server database, or recover a report server database, you can use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] commands, or the database command prompt utilities. For instructions, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../Topic/Moving%20the%20Report%20Server%20Databases%20to%20Another%20Computer%20\(SSRS%20Native%20Mode\).md) in SQL Server Books Online.  
  
-   To copy existing database content to another report server database, you can attach a copy of a report server database and use it with a different report server instance. Or, you can create and run a script that uses SOAP calls to recreate report server content in a new database. You can use the **rs** utility to run the script.  
  
-   To manage connections between the report server and report server database, and to find out which database is used for a particular report server instance, you can use Database Setup page in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]Configuration tool. To learn more about the report server connection to the report server database, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
## SQL Server Login and Database Permissions  
 The report server databases are used internally by the report server. Connections to either database are made by the Report Server service. You use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration tool to configure the report server connection to the report server database.  
  
 Credentials for the report server connection to the database can be the service account, a Windows local or domain user account, or a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database user. You must choose an existing account for the connection; [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] does not create accounts for you.  
  
 A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to the report server database is created for you automatically for the account you specify.  
  
 Permissions to the database are also configured automatically. The Reporting Services Configuration tool will assign the account or database user to the **Public** and **RSExecRole** roles for the report server databases. The **RSExecRole** provides permissions for accessing the database tables and for executing stored procedures. The **RSExecRole** is created in master and msdb when you create the report server database. The **RSExecRole** is a member of the **db\_owner** role for the report server databases, allowing the report server to update its own schema in support of an auto\-upgrade process.  
  
## Naming Conventions for the Report Server Databases  
 When creating the primary database, the name of the database must follow the rules specified for [Database Identifiers](../../Topics\TopicNameNotContainA/Database-Identifiers.md). The temporary database name always uses the same name as the primary report server database but with a Tempdb suffix. You cannot choose a different name for the temporary database.  
  
 Renaming a report server database is not supported because the report server databases are considered internal components. Renaming the report server databases causes errors to occur. Specifically, if you rename the primary database, an error message explains that the database names are out of sync. If you rename the ReportServerTempdb database, the following internal error occurs later when you run reports:  
  
 "An internal error occurred on the report server. See the error log for more details. \(rsInternalError\)  
  
 Invalid object name 'ReportServerTempDB.dbo.PersistedStream'."  
  
 This error occurs because the ReportServerTempdb name is stored internally and used by stored procedures to perform internal operations. Renaming the temporary database will prevent the stored procedures from working properly.  
  
## Enabling Snapshot Isolation on the Report Server Database  
 You cannot enable snapshot isolation on the report server database. If snapshot isolation is turned on, you will encounter the following error: "The selected report is not ready for viewing. The report is still being rendered or a report snapshot is not available."  
  
 If you did not purposely enable snapshot isolation, the attribute might have been set by another application or the **model** database might have snapshot isolation enabled, causing all new databases to inherit the setting.  
  
 To turn off snapshot isolation on the report server database, start Management Studio, open a new query window, paste and then run the following script:  
  
```  
ALTER DATABASE ReportServer  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServerTempdb  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServer  
SET READ_COMMITTED_SNAPSHOT OFF  
ALTER DATABASE ReportServerTempDb  
SET READ_COMMITTED_SNAPSHOT OFF  
```  
  
## About Database Versions  
 In [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], explicit information about the database version is not available. However, because database versions are always synchronized to product versions, you can use product version information to tell when the database version has changed. Product version information for [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is indicated through file version information that appears in the log files, in the headers of all SOAP calls, and when you connect to the report server URL \(for example, when you open a browser to http:\/\/localhost\/reportserver\).  
  
## See Also  
 [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md)   
 [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Report%20Server%20Service%20Account%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Backup and Restore Operations for Reporting Services](../../Topics\TopicNameNotContainA/Backup-and-Restore-Operations-for-Reporting-Services.md)   
 [Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md)   
 [Reporting Services Report Server &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(Native%20Mode\).md)   
 [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../Topic/Store%20Encrypted%20Report%20Server%20Data%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md)  
  
  