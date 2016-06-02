---
title: View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
---
# View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)
  When using transactional replication, transaction commands are stored in the distribution database until the Distribution Agent propagates them to all Subscribers or a Distribution Agent at the Subscriber pulls the changes. These pending commands in the distribution database can be viewed programmatically using replication stored procedures. For more information, see [Replication Stored Procedures &#40;Transact-SQL&#41;](../Topic/Replication%20Stored%20Procedures%20\(Transact-SQL\).md).  
  
### To view replicated commands from all transactional publications in the distribution database  
  
1.  At the Distributor on the distribution database, execute [sp\_browsereplcmds](../Topic/sp_browsereplcmds%20\(Transact-SQL\).md).  
  
### To view replicated commands in the distribution database from a specific article or from a specific database published using transactional replication  
  
1.  \(Optional\) At the Publisher on the publication database, execute [sp\_helparticle](../Topic/sp_helparticle%20\(Transact-SQL\).md). Specify **@publication** and **@article**. Note the value of **article id** in the result set.  
  
2.  At the Distributor on the distribution database, execute [sp\_browsereplcmds](../Topic/sp_browsereplcmds%20\(Transact-SQL\).md). \(Optional\) Specify the article ID from step 2 for **@article\_id**. \(Optional\) Specify the ID of the publication database for **@publisher\_database\_id**, which can be obtained from the **database\_id** column in the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view.  
  
## See Also  
 [Programmatically Monitor Replication](../../Topics\TopicNameNotContainA/Programmatically-Monitor-Replication.md)  
  
  