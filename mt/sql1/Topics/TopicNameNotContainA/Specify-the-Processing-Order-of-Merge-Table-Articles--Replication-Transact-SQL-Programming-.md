---
title: "Specify the Processing Order of Merge Table Articles (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 06/29/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Specify the Processing Order of Merge Table Articles (Replication Transact-SQL Programming)
Merge replication enables you to specify the order in which articles are processed by the Merge Agent during the synchronization process. You can assign an order to each article programmatically when creating an article using replication stored procedures. Articles are processed in order from lowest to highest value. If two articles have the same value, they are processed concurrently. For more information, see [Specify the Processing Order of Merge Articles](../../Topics/TopicNameNotContainA/Specify-the-Processing-Order-of-Merge-Articles.md).  
  
### To specify the processing order for a new merge article  
  
1.  At the Publisher on the publication database, execute [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c). Specify an integer value that represents the processing order for the article for **@processing_order**. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  When creating ordered articles, you should leave gaps between the article order values. This makes it easier to set new values in the future. For example, if you have three articles for which you need to specify a fixed processing order, set the value of **@processing_order** to 10, 20, and 30 rather than 1, 2, and 3, respectively.  
  
### To change the processing order of a merge article  
  
1.  To determine processing order of an article, execute [sp_helpmergearticle](assetId:///0fb9986a-3c33-46ef-87bb-297396ea5a6a) and note the value of **processing_order** in the result set.  
  
2.  At the Publisher on the publication database, execute [sp_changemergearticle](assetId:///0dc3da5c-4af6-45be-b5f0-074da182def2). Specify a value of **processing_order** for **@property** and an integer value that represents the processing order for **@value**.  
  
## See Also  
 [Specify the Processing Order of Merge Articles](../../Topics/TopicNameNotContainA/Specify-the-Processing-Order-of-Merge-Articles.md)