---
title: "Specify That Deletes Should Not Be Tracked For Merge Articles (Replication Transact-SQL Programming)"
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
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 35
manager: jhubbard
---
# Specify That Deletes Should Not Be Tracked For Merge Articles (Replication Transact-SQL Programming)
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)]  
  
 By default, merge replication synchronizes DELETE commands between the Publisher and Subscriber. Merge replication enables you to retain rows in the subscription database even when they have been deleted from the publication, and vice versa. You can programmatically specify that DELETE commands be ignored when creating a new article or you can enable this functionality at a later time using replication stored procedures.  
  
> [!IMPORTANT]  
>  Enabling this functionality will result in non-convergence, which means that data present at the Subscriber will not accurately reflect data at the Publisher. You must implement your own mechanism for manually removing deleted rows.  
  
### To specify that deletes be ignored for a new merge article  
  
1.  At the Publisher on the publication database, execute [Optimizing Merge Replication Performance with Conditional Delete Tracking](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c). Specify a value of **false** for **@delete_tracking**. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  If the source table for an article is already published in another publication, the value of **delete_tracking** must be the same for both articles.  
  
### To specify that deletes be ignored for an existing merge article  
  
1.  To determine if error compensation is enabled for an article, execute [sp_helpmergearticle](assetId:///0fb9986a-3c33-46ef-87bb-297396ea5a6a) and note the value of **delete_tracking** in the result set. If this value is **0**, deletes are already being ignored.  
  
2.  If the value from step 1 is **1**, execute [sp_changemergearticle](assetId:///0dc3da5c-4af6-45be-b5f0-074da182def2) at the Publisher on the publication database. Specify a value of **delete_tracking** for **@property**, and a value of **false** for **@value**.  
  
    > [!NOTE]  
    >  If the source table for an article is already published in another publication, the value of **delete_tracking** must be the same for both articles.  
  
## See Also  
 [Optimize Merge Replication Performance with Conditional Delete Tracking](../../Topics/TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Conditional-Delete-Tracking.md)