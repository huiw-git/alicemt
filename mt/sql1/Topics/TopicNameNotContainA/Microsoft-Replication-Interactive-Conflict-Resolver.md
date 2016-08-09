---
title: "Microsoft Replication Interactive Conflict Resolver"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Microsoft Replication Interactive Conflict Resolver
The Interactive Conflict Resolver can be used for merge subscriptions that are synchronized using Windows Synchronization Manager. It allows you to view, compare, edit, and select the outcome for data conflicts. Replication also includes the Conflict Viewer, which allows you to view and modify conflict outcomes after they have been committed. The Interactive Conflict Resolver allows you to select the outcome during synchronization.  
  
> [!NOTE]  
>  Conflicts that involve logical records are not displayed in the Interactive Resolver. To view information about these conflicts, use replication stored procedures. For more information, see [View Conflict Information for Merge Publications (Replication Transact-SQL Programming)](../../Topics/TopicNameNotContainA/View-Conflict-Information-for-Merge-Publications--Replication-Transact-SQL-Programming-.md).  
  
## Options  
 **Column name**  
 The name of all columns in the table. One or more columns might have conflicting data. Regardless of which columns conflict, the entire winning row will overwrite the entire losing row.  
  
 **Suggested Resolution**  
 The suggested resolution provided by the conflict resolver for the article.  
  
 **Publisher**  
 The data value at the Publisher.  
  
 **Subscriber**  
 The data value at the Subscriber.  
  
 **Accept Suggested**, **Accept Publisher**, and **Accept Subscriber**  
 Click to accept the row that will be applied at either the Publisher or the Subscriber, depending on which one lost the conflict. If the Publisher lost the conflict, all other Subscribers will receive the winning row the next time they synchronize with the Publisher.  
  
 **Resolve remaining conflicts automatically**  
 Resolve all remaining conflicts using the suggested resolution provided by the conflict resolver for the article.  
  
 **Log the details of the conflict for later reference**  
 Logs the details of the conflict in system tables.  
  
## See Also  
 [Interactive Conflict Resolution](../../Topics/TopicNameNotContainA/Interactive-Conflict-Resolution.md)   
 [View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-and-Resolve-Data-Conflicts-for-Merge-Publications--SQL-Server-Management-Studio-.md)   
 [Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)](../../Topics/TopicNameContainA/Synchronize-a-Subscription-Using-Windows-Synchronization-Manager--Windows-Synchronization-Manager-.md)   
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics/TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)