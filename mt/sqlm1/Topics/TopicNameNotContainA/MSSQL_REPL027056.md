---
title: MSSQL_REPL027056
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
---
# MSSQL_REPL027056
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|27056|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The merge process was unable to change generation history at the '%1'. When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.|  
  
## Explanation  
 This error is typically raised as a result of contention in merge replication system tables that have grown excessively large. Large system tables are typically caused by a long publication retention period, because metadata must be stored in these tables until the retention period is reached.  
  
## User Action  
 **To resolve the issue:**  
  
1.  Decrease the value of the \-**DownloadGenerationsPerBatch** and **\-UploadGenerationsPerBatch** parameters for the Merge Agent to allow processing to continue while you address the underlying issue causing the error. Agent parameters can be specified in agent profiles and on the command line. For more information, see:  
  
    -   [Work with Replication Agent Profiles](../../Topics\TopicNameNotContainA/Work-with-Replication-Agent-Profiles.md)  
  
    -   [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](../Topic/View%20and%20Modify%20Replication%20Agent%20Command%20Prompt%20Parameters%20\(SQL%20Server%20Management%20Studio\).md)  
  
    -   [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
2.  Specify the lowest setting possible for the publication retention period. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
3.  As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge\_contents**, **MSmerge\_genhistory**, and **MSmerge\_tombstone**, **MSmerge\_current\_partition\_mappings**, and **MSmerge\_past\_partition\_mappings**. Periodically re\-index these tables. For more information, see [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  