---
title: "What&#39;s New in SQL Server R Services"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 21
caps.handback.revision: 0
manager: paulettm
---
# What&#39;s New in SQL Server R Services
[!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] is a new feature in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] that supports enterprise-scale data science. [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] helps you embrace the highly popular open source R language in your business. R is the most popular programming language for advanced analytics, and offers an incredibly rich set of packages and a vibrant and fast-growing developer community.  
  
||  
|-|  
|**Get it now!**<br /><br /> For more information about how to install the latest version of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], see [Set up SQL Server R Services (In-Database)](../../Topics/TopicNameNotContainA/Set-up-SQL-Server-R-Services--In-Database-.md).|  
  
 To review what is new in the other [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] components, see [What's New in SQL Server 2016](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md).  
  
## What's New in RC2  
  
-   New, easier integrated setup of   all components. The unified installer can install either **SQL Server R Services (In-Database)** or the new **Microsoft R Server (Standalone)**.  
  
     When you run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup, just choose the service type to install, and all required R components are installed automatically.  
  
     For more information on these setup options, see [Set up SQL Server R Services (In-Database)](../../Topics/TopicNameNotContainA/Set-up-SQL-Server-R-Services--In-Database-.md) or [Create a Standalone R Server](../../Topics/TopicNameContainA/Create-a-Standalone-R-Server.md).  
  
     With Enterprise Edition, you can also  use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup to install a matching version of the R components on a client computer used for data science development.  
  
-   Integrated authentication is now supported.  
  
-   Manage the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service from SQL Server Configuration Manager.  
  
## What's New in RC1  
  
-   Significant performance improvements based on optimization of the SQL satellite processes that connect R and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df) now supports returning multiple output parameters, in addition to returning a dataset.  
  
-   A new resource pool mechanism for managing external processes.  The external pool can be used to allocate resources used by R Services to ensure that the R runtime and processes managed by the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] (including rterm.exe and BxlServer.exe) have sufficient resources.  
  
     For more information see [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808).  
  
-   Support for paging of data to enable high-volume data usage. You can easily work with billions of rows because they are loaded as needed, rather than being read into memory before R can work.  
  
-   Support for streaming. If you are processing  a billion rows with a batch size of one million rows, the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] interface will start returning results as soon as the first batch has been processed.  
  
-   Support for implied authentication allows you to call the R ROBC or RJDBC packages without embedding your credentials in R script; R script running under the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)]account will be run as if with the credentials of the logged in user.  
  
## What's New in RC0  
  
-   A new tutorial is available for SQL developers who want to create R solutions using nothing but [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] and the familiar environment of [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. See [In-Database Advanced Analytics for SQL Developers (Tutorial)](assetId:///c18cb249-2146-41b7-8821-3a20c5d7a690).  
  
-   R Tools for Visual Studio is in public preview. This new plug-in for Visual Studio supports an R interactive window, Intellisense for R functions, debugging, and R Markdown, complete with export to Word and HTML!  
  
     For more information, see [Welcome to R Tools for Visual Studio Preview](http://microsoft.github.io/RTVS-docs).  
  
-   For [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] RC0, continue to use the version of the R libraries provided for CTP 3.0 and higher.  The next significant update for [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] will be Release Candidate 1 (RC1).  
  
     If you are installing [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] for the first time, start here: [Installing Previous Versions of SQL Server R Services](../../Topics/TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)  
  
-   For **RC0**, the default location for the post-installation configuration script has changed: `C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`.  
  
-   If you need to uninstall a previous version of [!INCLUDE[rsql_rro-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)], be sure to uninstall [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)] first, and then uninstall [!INCLUDE[rsql_rro-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rro-noversion_md.md)].  
  
## What's New in CTP 3.3  
  
-   If you are upgrading from an earlier version of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], be sure to download the latest version of the post-installation configuration script, and run the script using the */UNINSTALL* option to remove older components.  for more information, see [Upgrade and Installation FAQ (SQL Server R Services)](../../Topics/TopicNameNotContainA/Upgrade-and-Installation-FAQ--SQL-Server-R-Services-.md).  
  
## What's New in CTP 3.2  
  
-   Microsoft has announced the public availability of [!INCLUDE[rsql_platform](../../Topics/TopicNameNotContainA/tokens/rsql_platform_md.md)], which adds enterprise scale and performance, easy operationalization, and multi-platform support to the popular open source R language. [!INCLUDE[rsql_platform](../../Topics/TopicNameNotContainA/tokens/rsql_platform_md.md)] runs on a wide variety of platforms, and supports multi-threaded and distributed execution of scripts. R scripts built for the [!INCLUDE[rsql_platform](../../Topics/TopicNameNotContainA/tokens/rsql_platform_md.md)] platform can work on data much larger than physical memory and process millions of observations with only a slight linear increase in time.  For details, see[R Server (Standalone)](../../Topics/TopicNameNotContainA/R-Server--Standalone-.md)  
  
-   Want to learn more about the enhanced R functions in the **ScaleR** package? To get started and learn more about using remote and local compute contexts, see [Data Science Deep Dive: Overview (SQL Server R Services)](assetId:///4817b973-7ee4-4843-88ff-637665e44bd2).  
  
-   Some changes will be required in setup if you are upgrading from an earlier version of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)]. See the Release Notes for details. If you are installing [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] for the first time, start here: [Installing Previous Versions of SQL Server R Services](../../Topics/TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)  
  
## What's New in CTP 3.1  
  
-   Check out the data science walkthrough, available here:  [Tutorial: Data Exploration and Predictive Modeling (SQL Server R Services)](assetId:///65589d17-bd34-4baa-8ba1-998f60d0344f)  
  
-   Sample R scripts are available on the Microsoft Download Center with the [SQL Server product samples](https://www.microsoft.com/download/details.aspx?id=49502).  
  
     To get just the R samples, click **Download**, and then select the file SQLServer2016CTP3Samples.zip. After extracting the samples file, open the folder **Advanced Analytics**.  
  
-   Troubleshoot your R sessions using Extended Events. For more information, see [Extended Events for SQL Server R Services](../../Topics/TopicNameNotContainA/Extended-Events-for-SQL-Server-R-Services.md).  
  
## What's New in CTP 3  
 This technical preview marks the initial release of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)]. The development tools and enhanced R packages provided in these downloads were originally developed by Revolution Analytics. After acquisition by Microsoft, improvements have been made to make it  easier to integrate R with enterprise database and data warehousing products, including the ability to run R code directly from [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
## See Also  
 [What's New in SQL Server 2016](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md)   
 [SQL Server 2016 Release Notes](../../Topics/TopicNameNotContainA/SQL-Server-2016-Release-Notes.md)