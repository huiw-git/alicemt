---
title: Report Server Database (SSRS Native Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fc5c033-3fe1-4cea-86c7-66ea5e424d65
---
# Report Server Database (SSRS Native Mode)
  A report server is a stateless server that uses the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to store metadata and object definitions. A native mode [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation uses two databases to separate persistent data storage from temporary storage requirements. The databases are created together and bound by name. By default, the database names are **reportserver** and **reportservertempdb**, respectively.  
  
 A SharePoint mode [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation will also create a database for the data alerting feature. The three databases in SharePoint mode are associated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications. For more information, see [Manage a Reporting Services SharePoint Service Application](../../Topics\TopicNameContainA/Manage-a-Reporting-Services-SharePoint-Service-Application.md)  
  
 The databases can run on a local or remote [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance. Choosing a local instance is useful if you have sufficient system resources or want to conserve software licenses, but running the databases on a remote computer can improve performance.  
  
 You can port or reuse an existing report server database from previous installation or a different instance with another report server instance. The schema of the report server database must be compatible with the report server instance. If the database is in an older format, you will be prompted to upgrade it to the current format. Newer versions cannot be down graded to an older version. If you have a newer report server database, you cannot use it with an earlier version of a report server instances. For more information about how report server databases are upgraded to newer formats, see [Upgrade a Report Server Database](../../Topics\TopicNameContainA/Upgrade-a-Report-Server-Database.md).  
  
> [!IMPORTANT]  
>  The table structure for the databases is optimized for server operations and should not be modified or tuned. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] might change the table structure from one release to the next. If you modify or extend the database, you might limit or prevent the capability to perform future upgrades or apply service packs. You might also introduce changes that impair report server operations. For example if you turn on READ\_COMMITTED\_SNAPSHOT on the ReportServer database, you will break the interactive sorting feature.  
  
 All access to a report server database must be handled through the report server. To access content in a report server database, you can use report server management tools, \(such as Report Manager and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]\), or programmatic interfaces such as URL access, Report Server Web service, or the Windows Management Instrumentation \(WMI\) provider.  
  
 The connection to the report server database is usually defined through the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. However, it can be defined during setup if you choose to install the default configuration. For more information about the report server connection to the database, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
## Report Server Database  
 The report server database is a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database that stores the following content:  
  
-   Items managed by a report server \(reports and linked reports, shared data sources, report models, folders, resources\) and all of the properties and security settings that are associated with those items.  
  
-   Subscription and schedule definitions.  
  
-   Report snapshots \(which include query results\) and report history.  
  
-   System properties and system\-level security settings.  
  
-   Report execution log data.  
  
-   Symmetric keys and encrypted connection and credentials for report data sources.  
  
 Because the report server database stores application state and persistent data, you should create a backup schedule for this database to prevent data loss. For recommendations and instructions on how to back up the database, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../Topic/Moving%20the%20Report%20Server%20Databases%20to%20Another%20Computer%20\(SSRS%20Native%20Mode\).md).  
  
## Report Server Temporary Database  
 Each report server database uses a related temporary database to store session and execution data, cached reports, and work tables that are generated by the report server. Background server processes will periodically remove older and unused items from the tables in the temporary database.  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] does not re\-create the temporary database if it is missing, nor does it repair missing or modified tables. Although the temporary database does not contain persistent data, you should back up a copy of the database anyway so that you can avoid having to re\-create it as part of a failure recovery operation.  
  
 If you back up the temporary database and subsequently restore it, you should delete the contents. Generally, it is safe to delete the contents of the temporary database at any time. However, you must restart the Report Server Windows service after you delete the contents.  
  
## See Also  
 [Host a Report Server Database in a SQL Server Failover Cluster](../../Topics\TopicNameContainA/Host-a-Report-Server-Database-in-a-SQL-Server-Failover-Cluster.md)   
 [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../Topic/Store%20Encrypted%20Report%20Server%20Data%20\(SSRS%20Configuration%20Manager\).md)   
 [Reporting Services Report Server](../../Topics\TopicNameNotContainA/Reporting-Services-Report-Server.md)   
 [Administer a Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Administer%20a%20Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md)   
 [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Backup and Restore Operations for Reporting Services](../../Topics\TopicNameNotContainA/Backup-and-Restore-Operations-for-Reporting-Services.md)  
  
  