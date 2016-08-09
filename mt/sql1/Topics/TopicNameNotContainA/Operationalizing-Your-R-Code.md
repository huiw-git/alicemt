---
title: "Operationalizing Your R Code"
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
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 12
caps.handback.revision: 0
manager: paulettm
---
# Operationalizing Your R Code
Database developers are tasked with integrating multiple technologies and bringing together the results so that they can be shared throughout the enterprise. The database developer works with application developers, SQL developers, and data scientists to design solutions, recommend data management methods, and architect and deploy solutions. [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] provides many benefits to developers who work with data scientists.  
  
-   **Interact with R scripts using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].** Application and database developers as well as analysts authoring reports can invoke an R script by calling it from a system stored procedure.  
  
     For more information, see [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df).  
  
     Integration with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] also means that you can execute R scripts using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] and embed the results in your application. For example, you can create a [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] report that runs an R script and then display the plots along with the predictions in the report.  
  
-   **Performance and scale.** Although the open source R language is known to have limitations, the RevoScaleR package APIs provided by [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] can operate on large datasets and benefit from multi-threaded, multi-core, multi-process in-database computations.  
  
     If your R solution uses complex aggregations or involves large datasets, you can leverage SQL’s highly efficient in-memory aggregations and columnstore indexes, and let the R code handle the statistical computations and scoring.  
  
-   **Standard development and management tools.** No additional tools for administration or deployment required -- all R jobs can be called by invoking a stored procedure.  
  
     Moreover, the same R code that you run against [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data can be used against other data sources, such as Hadoop.  
  
 This section describes the concepts you need to understand to successfully convert R solutions and deploy them to production using [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)].  
  
##  <a name="bkmk_RelatedTasks"></a> Related Tasks  
  
> [!NOTE]  
>  This section is under construction.  
  
-   Deploy an R script to production  
  
-   Troubleshoot R scripts using logs  
  
-   Use the caller's context when executing an R script from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]  
  
-   Use the try-catch construct in [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] to catch errors returned from an R script  
  
-   Invoke multiple instances and distribute data to each R process  
  
## See Also  
 [SQL Server R Services Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)   
 [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df)