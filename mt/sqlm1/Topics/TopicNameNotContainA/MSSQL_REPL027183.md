---
title: MSSQL_REPL027183
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
---
# MSSQL_REPL027183
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|27183|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The merge process failed to enumerate changes in articles with parameterized row filters. If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.|  
  
## Explanation  
 This error is raised if a Merge Agent timeout occurs while processing changes in a filtered publication. The timeout might be caused by one of the following issues:  
  
-   Not using the precomputed partitions optimization.  
  
-   Index fragmentation on columns used for filtering.  
  
-   Large merge metadata tables, such as **MSmerge\_tombstone**, **MSmerge\_contents**, and **MSmerge\_genhistory**.  
  
-   Filtered tables that are not joined on a unique key and join filters that involve a large number of tables.  
  
## User Action  
 To resolve the issue:  
  
-   Increase the value of the **\-QueryTimeOut** parameter for the Merge Agent to allow processing to continue while you address the underlying issues causing the error. Agent parameters can be specified in agent profiles and on the command line. For more information, see:  
  
    -   [Work with Replication Agent Profiles](../../Topics\TopicNameNotContainA/Work-with-Replication-Agent-Profiles.md)  
  
    -   [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](../Topic/View%20and%20Modify%20Replication%20Agent%20Command%20Prompt%20Parameters%20\(SQL%20Server%20Management%20Studio\).md)  
  
    -   [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
-   Use the precomputed partitions optimization if possible. This optimization is used by default if a number of publication requirements are met. For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../../Topics\TopicNameNotContainA/Optimize-Parameterized-Filter-Performance-with-Precomputed-Partitions.md). If the publication does not meet these requirements, consider redesigning the publication.  
  
-   Specify the lowest setting possible for the publication retention period, because replication cannot clean up metadata in the publication and subscription databases until the retention period is reached. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
-   As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge\_contents**, **MSmerge\_genhistory**, and **MSmerge\_tombstone**, **MSmerge\_current\_partition\_mappings**, and **MSmerge\_past\_partition\_mappings**. Periodically re\-index these tables. For more information, see [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
-   Ensure that columns used for filtering are properly indexed and rebuild such indexes if necessary. For more information, see [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
-   Set the **join\_unique\_key** property for join filters that are based on unique columns. For more information, see [Join Filters](../../Topics\TopicNameNotContainA/Join-Filters.md).  
  
-   Limit the number of tables in the join filter hierarchy. If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables. Use join filters only between tables that must be partitioned among subscriptions.  
  
-   Make a smaller number of changes on filtered tables between synchronizations, or run the Merge Agent more frequently. For more information about setting synchronization schedules, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  