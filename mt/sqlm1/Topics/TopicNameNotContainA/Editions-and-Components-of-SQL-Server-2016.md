---
title: Editions and Components of SQL Server 2016
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5186f02-dd91-47d0-8fa4-de3f41c76903
---
# Editions and Components of SQL Server 2016
  Installation requirements vary based on your application needs. The different editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] accommodate the unique performance, runtime, and price requirements of organizations and individuals. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components that you install also depend on your specific requirements. The following sections help you understand how to make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Editions  
 The following table describes the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Features Supported by Edition of SQL Server](../../Topics\TopicNameNotContainA/Features-Supported-by-Edition-of-SQL-Server.md)  
  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition|Definition|  
|---------------------------------------|----------------|  
|Enterprise|The premium offering, [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise edition delivers comprehensive high\-end datacenter capabilities with blazing\-fast performance, unlimited virtualization, and end\-to\-end business intelligence — enabling high service levels for mission\-critical workloads and end user access to data insights.|  
|Standard|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard edition delivers basic data management and business intelligence database for departments and small organizations to run their applications and supports common development tools for on\-premise and cloud — enabling effective database management with minimal IT resources.|  
|Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web edition is a low total\-cost\-of\-ownership option for Web hosters and Web VAPs to provide scalability, affordability, and manageability capabilities for small to large scale Web properties.|  
|Developer|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer edition lets developers build any kind of application on top of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. It includes all the functionality of Enterprise edition, but is licensed for use as a development and test system, not as a production server. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Developer is an ideal choice for people who build<br />                [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and test applications.|  
|Express editions|Express edition is the entry\-level, free database and is ideal for learning and building desktop and small server data\-driven applications. It is the best choice for independent software vendors, developers, and hobbyists building client applications. If you need more advanced database features, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Express can be seamlessly upgraded to other higher end versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Express LocalDB, a lightweight version of Express that has all of its programmability features, yet runs in user mode and has a fast, zero\-configuration installation and a short list of prerequisites.|  
  
## Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with an Internet Server  
 On an Internet server, such as a server that is running Internet Information Services \(IIS\), you will typically install the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client tools. Client tools include the client connectivity components used by an application connecting to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  Although you can install an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a computer that is running IIS, this is typically done only for small Web sites that have a single server computer. Most Web sites have their middle\-tier IIS systems on one server or a cluster of servers, and their databases on a separate server or federation of servers.  
  
## Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with Client\/Server Applications  
 You can install just the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client components on a computer that is running client\/server applications that connect directly to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. A client components installation is also a good option if you administer an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a database server, or if you plan to develop [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] applications.  
  
 The client tools option installs the following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features: backward compatibility components, [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], connectivity components, management tools, software development kit, and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online components. For more information, see  [Install SQL Server 2016](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016.md).  
  
## Deciding Among [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Components  
 Use the Feature Selection page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to select the components to include in an installation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, none of the features in the tree are selected.  
  
 Use the information in the following tables to determine the set of features that best fits your needs.  
  
|Server components|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] includes the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], the core service for storing, processing, and securing data, replication, full\-text search, tools for managing relational and XML data,   in database analytics integration, and Polybase integration for access to Hadoop and other heterogeneous data sources, and the [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) server.|  
|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] includes the tools for creating and managing online analytical processing \(OLAP\) and data mining applications.|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free\-form reports. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is also an extensible platform that you can use to develop report applications.|  
|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is a set of graphical tools and programmable objects for moving, copying, and transforming data. It also includes the [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) component for [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)].|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] \(MDS\) is the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] solution for master data management. MDS can be configured to manage any domain \(products, customers, accounts\) and includes hierarchies, granular security, transactions, data versioning, and business rules, as well as an [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] that can be used to manage data.|  
|[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]|[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] supports distributed, scalable R solutions on multiple platforms and using multiple enterprise data sources, including Linux, Hadoop, and Teradata.|  
  
|Management tools|Description|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]|[!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] is an integrated environment to access, configure, manage, administer, and develop components of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] lets developers and administrators of all skill levels use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].<br /><br /> Download and install <br />                [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] from  [Download SQL Server Management Studio](http://msdn.microsoft.com/library/mt238290.aspx)|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager provides basic configuration management for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services, server protocols, client protocols, and client aliases.|  
|[!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)]|[!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] provides a graphical user interface to monitor an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] or [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].|  
|[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor|[!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor helps create optimal sets of indexes, indexed views, and partitions.|  
|Data Quality Client|Provides a highly simple and intuitive graphical user interface to connect to the DQS server, and perform data cleansing operations. It also allows you to centrally monitor various activities performed during the data cleansing operation.|  
|[!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)]|[!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] provides an IDE for building solutions for the Business Intelligence components: [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], and [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)].<br /><br /> \(Formerly called Business Intelligence Development Studio\).<br /><br /> [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] also includes "Database Projects", which provides an integrated environment for database developers to carry out all their database design work for any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] platform \(both on and off premise\) within Visual Studio. Database developers can use the enhanced Server Explorer in Visual Studio to easily create or edit database objects and data, or execute queries.|  
|Connectivity Components|Installs components for communication between clients and servers, and network libraries for DB\-Library, ODBC, and OLE DB.|  
  
|Documentation|Description|  
|-------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online|Core documentation for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
  
  