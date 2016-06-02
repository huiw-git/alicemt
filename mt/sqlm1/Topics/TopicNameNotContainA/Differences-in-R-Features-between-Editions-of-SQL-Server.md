---
title: Differences in R Features between Editions of SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
---
# Differences in R Features between Editions of SQL Server
  [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] is available in the following editions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]:  
  
-   **Enterprise Edition**  
    
     Includes both R Services, for in-database analytics in SQL Server 2016, as well as R Server (Standalone) on Windows, which can be used to connect to a variety of databases and pull data for analysis at scale, but which does not run in-database. Also includes **DeployR**, which can be used to deploy R scripts and models as a Web Service.  

     No restrictions. Optimized performance and scalability through parallelization and streaming. Suopprts analysis of large datasets that do not fit in the available memory, by using the **ScaleR** functions.  
  
     In-database analytics in SQL Server supports resource governance of external scripts to customize server resource usage.  
  
-   **Developer Edition**  

    Same capabilities as Enterprise Edition; however, Developer Edition cannot be used in production environments.  

  
  
-   **Standard Edition**  
  
     Has all the capabilities of in-database analytics included with Enterprise Edition, except for the flexible resource governance. Performance and scale is also limited: the data that can be processed has to fit in server memory, and processing is limited to a single compute thread, even when using the **ScaleR** functions.
  
-   **Express Editions**  
  
     Only Express Edition with Advanced Services provides R Services. The performance limitations are similar to Standard Edition.  
  
 For more information about other product features, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  

> [!NOTE]
>
> + Microsoft R Open is included with all editions.
> + Microsoft R Client can work with all editions.
  
## Enterprise Edition  
 Performance of R solutions in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is expected to generally be better than any conventional R implementation, given the same hardware, because R can be run using server resources and sometimes distributed to multiple processes using the **ScaleR** functions.  
  
 Users can also expect to see considerable differences in performance and scalability for the same R functions if run in Enterprise Edition vs. Standard Edition. Reasons include support for parallel processing, streaming, and increased threads available for R worker processing.  
  
 However, performance even on identical hardware can be affected by many factors outside the R code, including competing demands on server resources, the type of query plan that is created, schema changes, the need to update statistics or create a new query plan, fragmentation, and more. It is possible that a stored procedure containing R code might run in seconds under one workload, but take minutes when there are other services running.  Therefore, we recommend that you monitor multiple aspects of server performance, including networking for remote compute contexts, when quantifying R job performance.  

We also recommend that you configure [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md) \(available in Enterprise Edition\) to customize the way that R jobs are prioritized or handled under heavy server workloads. You can define classifier functions to specify the source of the R job and prioritize certain workloads, limit the amount of memory used by SQL queries,  and control the number of parallel processes used on a workload basis.  
  
## Developer Edition  
 Developer Edition provides performance equivalent to that of Enterprise Edition; however, use of Developer Edition is not supported for production environments.  
  
  
## Standard Edition  
 Even Standard Edition should offer some performance benefit, in comparison to standard R packages, given the same hardware configuration.  
  
 However, Standard Edition does not support Resource Governor. Using resource governance is the best way to customize server resources to support varied R workloads such as model training and scoring.  
  
 Standard Edition also provides limited performance and scalability in comparison to Enterprise and Developer Editions. Specifically, all of the **ScaleR** functions and packages are included with Standard Edition, but the service that launches and manages R scripts is limited in the number of processes it can use. Moreover, data processed by the script must fit in memory.  
  
  
## Express Edition with Advanced Services  
 Express Edition is subject to the same limitations as Standard Edition.  
  
## See Also  
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
  