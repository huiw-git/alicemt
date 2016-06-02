---
title: What&#39;s New in SQL Server R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
---
# What&#39;s New in SQL Server R Services
  [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] is a new feature in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that supports enterprise\-scale data science. [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] helps you embrace the highly popular open source R language in your business. R is the most popular programming language for advanced analytics, and offers an incredibly rich set of packages and a vibrant and fast\-growing developer community.  
  
||  
|-|  
|**Get it now\!**<br /><br /> For more information about how to install the latest version of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], see [Set up SQL Server R Services &#40;In-Database&#41;](../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md).|  
  
## What's New in RTM  
  
The [Microsoft R Client](http://go.microsoft.com/fwlink/?LinkId=799768) is the preferred tool for developing R solutions that use Microsoft R Open and the ScaleR libraries.
  
## What's New in RC2  
  
-   New, easier integrated setup of   all components. The unified installer can install either **SQL Server R Services \(In\-Database\)** or, in Enterprise Edition, the new **Microsoft R Server \(Standalone\)**.  
  
     When you run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, just choose the service type to install, and all required R components are installed automatically.  
  
     For more information on these setup options, see [Set up SQL Server R Services &#40;In-Database&#41;](../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md) or [Create a Standalone R Server](../../Topics\TopicNameContainA/Create-a-Standalone-R-Server.md).  
  
-   Integrated authentication is now supported.  
  
-   Manage the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service from SQL Server Configuration Manager.  
  
## What's New in RC1  
  
-   Significant performance improvements based on optimization of the SQL satellite processes that connect R and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   [sp_execute_external_script &#40;Transact-SQL&#41;](../Topic/sp_execute_external_script%20\(Transact-SQL\).md) now supports returning multiple output parameters, in addition to returning a dataset.  
  
-   A new resource pool mechanism for managing external processes.  The external pool can be used to allocate resources used by R Services to ensure that the R runtime and processes managed by the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] \(including rterm.exe and BxlServer.exe\) have sufficient resources.  
  
     For more information see [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20RESOURCE%20POOL%20\(Transact-SQL\).md).  
  
-   Support for paging of data to enable high\-volume data usage. You can easily work with billions of rows because they are loaded as needed, rather than being read into memory before R can work.  
  
-   Support for streaming. If you are processing  a billion rows with a batch size of one million rows, the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] interface will start returning results as soon as the first batch has been processed.  
  
-   Support for implied authentication allows you to call the R ROBC or RJDBC packages without embedding your credentials in R script; R script running under the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)]account will be run as if with the credentials of the logged in user.  
  
## What's New in RC0  
  
-   A new tutorial is available for SQL developers who want to create R solutions using nothing but [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and the familiar environment of [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. See [In-Database Advanced Analytics for SQL Developers &#40;Tutorial&#41;](../Topic/In-Database%20Advanced%20Analytics%20for%20SQL%20Developers%20\(Tutorial\).md).  
  
-   R Tools for Visual Studio is in public preview. This new plug\-in for Visual Studio supports an R interactive window, Intellisense for R functions, debugging, and R Markdown, complete with export to Word and HTML\!  
  
     For more information, see [Welcome to R Tools for Visual Studio Preview](http://microsoft.github.io/RTVS-docs).  
  
-   For [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC0, continue to use the version of the R libraries provided for CTP 3.0 and higher.  The next significant update for [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] will be Release Candidate 1 \(RC1\).  
  
     If you are installing [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] for the first time, start here: [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)  
  
-   For **RC0**, the default location for the post\-installation configuration script has changed: `C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`.  
  
-   If you need to uninstall a previous version of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)], be sure to uninstall [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] first, and then uninstall [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  
  
## What's New in CTP 3.3  
  
-   If you are upgrading from an earlier version of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], be sure to download the latest version of the post\-installation configuration script, and run the script using the *\/UNINSTALL* option to remove older components.  for more information, see [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md).  
  
## What's New in CTP 3.2  
  
-   Microsoft has announced the public availability of [!INCLUDE[rsql_platform](../../Token\Other/rsql_platform_md.md)], which adds enterprise scale and performance, easy operationalization, and multi\-platform support to the popular open source R language. [!INCLUDE[rsql_platform](../../Token\Other/rsql_platform_md.md)] runs on a wide variety of platforms, and supports multi\-threaded and distributed execution of scripts. R scripts built for the [!INCLUDE[rsql_platform](../../Token\Other/rsql_platform_md.md)] platform can work on data much larger than physical memory and process millions of observations with only a slight linear increase in time.  For details, see[R Server &#40;Standalone&#41;](../Topic/R%20Server%20\(Standalone\).md)  
  
-   Want to learn more about the enhanced R functions in the **ScaleR** package? To get started and learn more about using remote and local compute contexts, see [Data Science Deep Dive: Overview &#40;SQL Server R Services&#41;deleted](../Topic/Data%20Science%20Deep%20Dive:%20Overview%20\(SQL%20Server%20R%20Services\)deleted.md).  
  
-   Some changes will be required in setup if you are upgrading from an earlier version of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. See the Release Notes for details. If you are installing [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] for the first time, start here: [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)  
  
## What's New in CTP 3.1  
  
-   Check out the data science walkthrough, available here:  [Data Exploration and Predictive Modeling &#40;Tutorial: SQL Server R Services&#41;](../Topic/Data%20Exploration%20and%20Predictive%20Modeling%20\(Tutorial:%20SQL%20Server%20R%20Services\).md)  
  
-   Sample R scripts are available on the Microsoft Download Center with the [SQL Server product samples](https://www.microsoft.com/download/details.aspx?id=49502).  
  
     To get just the R samples, click **Download**, and then select the file SQLServer2016CTP3Samples.zip. After extracting the samples file, open the folder **Advanced Analytics**.  
  
-   Troubleshoot your R sessions using Extended Events. For more information, see [Extended Events for SQL Server R Services](../../Topics\TopicNameNotContainA/Extended-Events-for-SQL-Server-R-Services.md).  
  
## What's New in CTP 3  
 This technical preview marks the initial release of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. The development tools and enhanced R packages provided in these downloads were originally developed by Revolution Analytics. After acquisition by Microsoft, improvements have been made to make it  easier to integrate R with enterprise database and data warehousing products, including the ability to run R code directly from [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
## See Also  
[What's New in SQL Server 2016 ](../../Topics\TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md)  
  
  