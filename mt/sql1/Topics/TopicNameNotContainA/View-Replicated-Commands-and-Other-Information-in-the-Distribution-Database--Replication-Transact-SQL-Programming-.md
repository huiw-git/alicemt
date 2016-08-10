---
title: "View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 08/09/2016
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
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)
When using transactional replication, transaction commands are stored in the distribution database until the Distribution Agent propagates them to all Subscribers or a Distribution Agent at the Subscriber pulls the changes. These pending commands in the distribution database can be viewed programmatically using replication stored procedures. For more information, see [Replication Stored Procedures (Transact-SQL)](assetId:///10996a2a-3be4-4f66-9fc4-815d43fc6e52).  
  
### To view replicated commands from all transactional publications in the distribution database  
  
1.  At the Distributor on the distribution database, execute [sp_browsereplcmds](assetId:///30abcb41-1d18-4f43-a692-4c80914c0450).  
  
### To view replicated commands in the distribution database from a specific article or from a specific database published using transactional replication  
  
1.  (Optional) At the Publisher on the publication database, execute [sp_helparticle](assetId:///9c4a1a88-56f1-45a0-890c-941b8e0f0799). Specify **@publication** and **@article**. Note the value of **article id** in the result set.  
  
2.  At the Distributor on the distribution database, execute [sp_browsereplcmds](assetId:///30abcb41-1d18-4f43-a692-4c80914c0450). (Optional) Specify the article ID from step 2 for **@article_id**. (Optional) Specify the ID of the publication database for **@publisher_database_id**, which can be obtained from the **database_id** column in the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view.  
  
## See Also  
 [Programmatically Monitor Replication](../../Topics/TopicNameNotContainA/Programmatically-Monitor-Replication.md)