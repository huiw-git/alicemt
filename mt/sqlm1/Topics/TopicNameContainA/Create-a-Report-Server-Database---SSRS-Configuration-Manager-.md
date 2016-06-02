---
title: Create a Report Server Database  (SSRS Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
---
# Create a Report Server Database  (SSRS Configuration Manager)
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] **Native mode** uses two [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] relational databases to store report server metadata and objects. One database is used for primary storage, and the second one stores temporary data. The databases are created together and bound by name. With a default [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, the databases are named **reportserver** and **reportservertempdb**. Collectively, the two databases are referred to as the "report server database" or "report server catalog".  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] **SharePoint mode** includes a third database that is used for data alerting metadata. The three databases are created for each [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application and the database names by default include a guid that represents the service application. The following are example names of the three SharePoint mode databases:  
  
-   ReportingService\_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService\_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService\_90a9f37075544f22953c4a62e4a9f370\_Alerting  
  
> [!IMPORTANT]  
>  Do not write applications that run queries against the report server database. The report server database is not a public schema. The table structure might change from one release to the next. If you write an application that requires access to the report server database, always use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] APIs to access the report server database.  
>   
>  The exception to this are the execution log views. For more information, see [Report Server ExecutionLog and the ExecutionLog3 View](../../Topics\TopicNameNotContainA/Report-Server-ExecutionLog-and-the-ExecutionLog3-View.md)  
  
## Ways to Create the Report Server Database  
 **Native Mode:** You can create the Native mode report server database in the following ways:  
  
-   Automatically: Use SQL Server Setup Wizard, if you choose the default configuration installation option. In the SQL Server Installation Wizard, this is the **Install and configure** in the Report Server Installation Options page. If you chose the **Install only** option, you must use the Reporting Services Configuration Manager to create the database.  
  
-   Manually: Use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. You must create the report server database manually if you are using a remote [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] to host the database. For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md).  
  
 **SharePoint Mode:** The Report Server Installation Options page only has one option for SharePoint mode of **Install Only**. This option installs all the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] files and the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] shared service. The next step is to create at least one [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application in one of the following ways:  
  
-   Use SharePoint Central Administration to create a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application. For more information see the “Service Application” section of [Step 3: Create a Reporting Services Service Application](../../Topics\TopicNameNotContainA/Install-The-First-Report-Server-in-SharePoint-Mode.md).  
  
-   Use [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] PowerShell cmdlets to create a service application and the report server databases. For more information see the sample for creating service applications in the topic [PowerShell cmdlets for Reporting Services SharePoint Mode](../../Topics\TopicNameNotContainA/PowerShell-cmdlets-for-Reporting-Services-SharePoint-Mode.md).  
  
## Database Server Version Requirements  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is used to host the report server databases. The [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] instance can be a local or remote instance. The following are the supported versions of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] that can be used to host the report server databases:  
  
-   [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]  
  
-   [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]  
  
 Creating the report server database on a remote computer requires that you configure the connection to use a domain user account or a service account that has network access. If you decide to use a remote [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, consider carefully which credentials the report server should use to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. For more information, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
> [!IMPORTANT]  
>  Report Server and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance hosting the report server database can be in different domains. For Internet deployment, it is common practice to use a server that is behind a firewall. If you are configuring a report server for Internet access, use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credentials to connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is behind the firewall and use IPSEC to secure the connection.  
  
## Database Server Edition Requirements  
 When creating a report server database, be aware that not all editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can be used to host the database. For more information, see the “Report Server Database Server Edition Requirements” section of [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## See Also  
 [Reporting Services Configuration Manager \(SSRS Native Mode\)](assetId:///63519ef4-e68a-42fb-9cf7-31228ea4e434)  
  
  