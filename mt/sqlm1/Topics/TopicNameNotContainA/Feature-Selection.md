---
title: Feature Selection
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73182088-153b-4634-a060-d14d1fd23b70
---
# Feature Selection
  Use the check boxes on the **Feature Selection** page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation wizard to select components for your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation.  
  
## Installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Features  
 On the **Feature Selection** page, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features are separated into two main sections: **Instance Features** and **Shared Features**.  
  
 **Instance Features** refers to the components that are installed once for each instance so that you have multiple copies of them \(one for each instance\). Each instance can be a separate version that has a different patch level. When you install a patch, whether it is a service pack, a hotfix, or a cumulative update, it updates only the files for one instance on a given machine, plus the shared features if they have not already been updated.  
  
 **Shared Features** refers to features that are common across all instances on a given machine. Each of these shared features is designed to be backward compatible with supported [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions \(service packs, cumulative updates, and hotfixes\) that can install side by side.  
  
> [!NOTE]  
>  **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Failover Clusters:** The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] components are the only [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] features that support failover clustering. You can install other components, like [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] or [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], on a failover cluster node, but they are not cluster\-aware, and their services do not fail over if the failover cluster node goes offline. For more information, see [AlwaysOn Failover Cluster Instances &#40;SQL Server&#41;](../Topic/AlwaysOn%20Failover%20Cluster%20Instances%20\(SQL%20Server\).md).  
  
### Instance Features  
 A description for each component group appears in the **Description** pane when you select it. You can select any combination of check boxes. To continue, you must make a selection.  
  
|Features|Description|  
|--------------|-----------------|  
|[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Services|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] includes the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], the core service for storing, processing, and securing data, replication, full\-text search, tools for managing relational and XML data, and the [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) server.<br /><br /> <br /><br /> The **[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]** is the core service for storing, processing, and securing data.<br /><br /> **Replication**: Optional. Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.<br /><br /> **Full\-Text Search**: Optional. Full\-Text Search provides functionality to issue full\-text queries against plain character\-based data in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tables.<br /><br /> **[!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)]** : Optional. [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) is a data\-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides computer\-assisted and interactive ways to cleanse your data. Select this check box to install DQS server. After the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation completes, you have to run the DQSInstaller.exe file to *complete* the DQS server installation. If you installed the default instance of SQL server, this file is available at C:\\Program Files\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn.<br /><br /> <br /><br /> **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Failover Clusters:** Replication and Full\-Text Search components are required, and automatically selected by Setup for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover clustering installations when you select Database Engine Services.|  
|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] includes the tools for creating and managing online analytical processing \(OLAP\) and data mining applications.|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] –Native|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free\-form reports. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is also an extensible platform that you can use to develop report applications.|  
  
> [!IMPORTANT]  
>  Setup does not configure load\-balancing and single\-URL addressing for multiple nodes in a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] scale\-out deployment. To complete a scale\-out deployment, you must use Windows Server, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Application Center, or third\-party cluster management software. For more information about setting up Web farm deployment, see [Configuring Reporting Services for Scale\-Out Deployment](http://go.microsoft.com/fwlink/?LinkId=199448) \(http:\/\/go.microsoft.com\/fwlink\/?LinkId\=199448\).  
>   
>  For browser requirements of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components, see [Browser Support for Reporting Services and Power View](../../Topics\TopicNameNotContainA/Browser-Support-for-Reporting-Services-and-Power-View.md).  
>   
>  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is not supported in side\-by\-side configurations on the 64\-bit platform and on the 32\-bit subsystem \(WOW64\) of a 64\-bit server at the same time.  
  
### Shared Features  
 Features shared by all instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a single computer are installed to a single directory. They include the following:  
  
|Feature|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] – SharePoint|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode is a server based application for creating, managing, and delivering reports to email, multiple file formats, and interactive Web\-based formations. SharePoint mode integrates the report viewing and report management experience with SharePoint products. For more information, see [Reporting Services Report Server &#40;SharePoint Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(SharePoint%20Mode\).md).|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Add\-in for SharePoint Products|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Add\-in for SharePoint products includes management and user interface components to integrate a SharePoint product with an [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server in SharePoint mode. For more information, see [Where to find the Reporting Services add-in for SharePoint Products](../../Topics\TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md).|  
|Data Quality Client|Data Quality Client is a standalone application that connects to the DQS server, and provides an intuitive graphical user interface to perform data\-cleansing and data\-matching operations, and to perform administrative tasks in DQS.|  
|Client Tools Connectivity|Client Tools includes components for communication between clients and servers, including network libraries for DB\-Library, OLEDB for OLAP, ODBC, ADODB, and ADOMD\+.|  
|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is a set of graphical tools and programmable objects for moving, copying, and transforming data.|  
|Client Tools Backward Compatibility|Client Tools Backward Compatibility includes the following components:<br /><br /> SQL Distributed Management Objects \(SQL\-DMO\). For more information, see [Discontinued SQL Server Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Discontinued-SQL-Server-Features-in-SQL-Server-2016.md).<br /><br /> Decision Support Objects \(DSO\). For more information, see [Breaking Changes to Analysis Services Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Breaking-Changes-to-Analysis-Services-Features-in-SQL-Server-2016.md).|  
|Client Tools SDK|Includes the software development kit containing resources for programmers.|  
|Documentation Components|Documentation components include the components to view and manage help content.|  
|Management Tools \- Basic|**Management Tools – Basic :** This includes the following:<br /><br /> [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] support for the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)], **sqlcmd** utility, and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell provider<br /><br /> <br /><br /> **Management Tools – Complete :** This includes the following components in addition to the components in the basic version:<br /><br /> [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] support for [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]<br /><br /> [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)]<br /><br /> Database Engine Tuning Advisor<br /><br /> [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility management|  
|Distributed Replay Controller|The Distributed Replay controller orchestrates the actions of the distributed replay clients. There can only be one controller instance in each Distributed Replay environment. For more information, see [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md).|  
|Distributed Replay Client|The Distributed Replay clients work together to simulate workloads against an instance of SQL Server. There can be one or more clients in each Distributed Replay environment. For more information, see [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md).|  
|SQL Client Connectivity SDK|Includes [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client \(ODBC\/OLE DB\) SDK for database application development.|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is a platform for integrating data from disparate systems across an organization into a single source of master data for accuracy and auditing purposes. The [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] option installs [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], assemblies, a Windows PowerShell snap\-in, and folders and files for Web applications and services.|  
  
 By default, shared components are installed to %Program Files%Microsoft SQL Server\\. To change the installation path, click the **Browse** button. If you change the installation path for one shared component, you also change it for other shared components. Subsequent installations will install shared components to the same location as the original installation.  
  
 **Instance root directory** \- By default, the instance root directory is C:\\Program Files\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\. To specify a non\-default root directory, click the **Browse** button, or provide a path name.  
  
 On x64\-based operating systems, you can specify where 64\-bit components will be installed, and where on the WOW64 subsystem 32\-bit components will be installed.  
  
## Disk Space Requirements  
 Use the Disk Cost Summary page to examine disk space requirements for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features that you selected for your installation.  
  
### Options  
 If required disk space is too high, consider the following options:  
  
-   Change installation directories to a drive with more disk space.  
  
-   Change the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features for your installation.  
  
-   Create more free space on the specified drive by moving other files or applications.  
  
## Installing AdventureWorks Sample Databases  
 By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. For more information about installing sample databases and sample code, see the [Microsoft SQL Server Community Projects & Samples](http://go.microsoft.com/fwlink/?LinkId=87843) \(http:\/\/go.microsoft.com\/fwlink\/?LinkId\=87843\).  
  
 Additional information about samples is available after [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] has been installed. From the **Start** menu, click **All Programs**, click **[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]**, click **Documentation and Tutorials**, and then click **[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Samples Overview**.  
  
## See Also  
 [Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md)  
  
  