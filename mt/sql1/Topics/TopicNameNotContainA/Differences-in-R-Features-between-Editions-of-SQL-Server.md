---
title: "Differences in R Features between Editions of SQL Server"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
manager: paulettm
---
# Differences in R Features between Editions of SQL Server
[!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] is available in the following editions of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]:  
  
-   **Enterprise Edition**  
  
     No restrictions. Optimized performance and scalability through parallelization and streaming.  
  
     Includes setup of Microsoft R Server (Standalone), which can be used to set up a client computer.  
  
     Supports resource governance of external scripts to customize server resource usage.  
  
-   **Developer Edition**  
  
     No performance restrictions. However, model deployment for production is not supported.  
  
     Microsoft R Server (Standalone) can be installed on a client computer to develop and test scenarios using remote compute context.  
  
     Additionally, the End-User License Agreement permits one R Services Client to connect to a production instance of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], for developing and testing solutions.  
  
-   **Standard Edition**  
  
     Microsoft R Open is available across all editions.   
    However, R script execution is single-threaded, like that of conventional packages.  Data that can be processed is limited to the data that can fit in server memory.  
  
     You cannot install Microsoft R Server (Standalone). You can install Microsoft R Client, which has some limitations, such as single-threaded execution and memory.  
  
-   **Express Editions**  
  
     Only Express Edition with Advanced Services provides R Services.  
  
 For more information about other product features, see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
## Enterprise Edition  
 Performance of R solutions in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is expected to generally be better than any conventional R implementation, given the same hardware, because R can be run using server resources and sometimes distributed to multiple processes. Depending on the input data and the processing of it, queries can be distributed across multiple partitions for faster processing.  
  
 Users can also expect to see considerable differences in performance and scalability for the same R functions if run in Enterprise Edition vs. Standard Edition. Reasons include support for parallel processing, streaming, and increased threads available for R worker processing.  
  
 However, performance even on identical hardware can be affected by many factors outside the R code, including competing demands on server resources, the type of query plan that is created, schema changes, the need to update statistics or create a new query plan, fragmentation and so on. It is possible that a stored procedure containing R code might run in seconds under one workload, but take minutes when there are other services running.  
We recommend that you monitor multiple aspects of server performance, including networking for remote compute contexts, when quantifying R job performance.  
  
 We also recommend that you configure Resource Governor, a feature available only in Enterprise Edition, to customize they way that R jobs are prioritized or handled under heavy server workloads. You can define classifier functions to specify the source of the R job and prioritize certain workloads, limit the amount of memory used by SQL queries,  and control the number of parallel processes used on a workload basis.  
  
## Developer Edition  
 Developer Edition provides performance equivalent to that of Enterprise Edition; however, use of Developer Editions is not supported for production environments.  
  
 While developing solutions, you can install Microsoft R Server (Standalone) on a remote client computer for use in developing and testing the solution.  
  
 For systems in production, you can use Microsoft R Client to connect to any production instance.  
  
## Standard Edition  
 Even Standard Edition should offer some performance benefit, in comparison to standard R packages, given the same hardware configuration.  
  
 However, Standard Edition does not support Resource Governor. Using resource governance is the best way to customize server resources to support varied R workloads such as model training and scoring.  
  
 Standard Edition also provides limited performance and scalability in comparison to Enterprise and Developer Editions. Specifically, all of the ScaleR functions and packages are included with Standard Edition, but the service that launches and manages R scripts is limited in the number of processes it can use. Moreover, data processed by the script must fit in memory.  
  
 Express Edition is subject to the same limitations as Standard Edition.  
  
## Express Edition with Advanced Services  
 Express Edition is subject to the same limitations as Standard Edition.  
  
## See Also  
 [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)