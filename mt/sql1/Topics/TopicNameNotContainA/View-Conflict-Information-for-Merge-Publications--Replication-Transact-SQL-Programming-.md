---
title: "View Conflict Information for Merge Publications (Replication Transact-SQL Programming)"
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
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# View Conflict Information for Merge Publications (Replication Transact-SQL Programming)
When a conflict is resolved in merge replication, the data from the losing row is written to a conflict table. This conflict data can be viewed programmatically by using replication stored procedures. For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../../Topics/TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md).  
  
### To view conflict information and losing row data for all types of conflicts  
  
1.  At the Publisher on the publication database, execute [sp_helpmergepublication](assetId:///dfe1e1e1-9a65-406a-aced-6385a078e135). Note the values of the following columns in the result set:  
  
    -   **centralized_conflicts** - 1 indicates that conflict rows are stored at the Publisher, and 0 indicates that conflict rows are not stored at the Publisher.  
  
    -   **decentralized_conflicts** - 1 indicates that conflict rows are stored at the Subscriber, and 0 indicates that conflict rows are not stored at the Subscriber.  
  
        > [!NOTE]  
        >  The conflict logging behavior of a merge publication is set by using the **@conflict_logging** parameter of [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a). Use of the **@centralized_conflicts** parameter has been deprecated.  
  
     The following table describes the values of these columns based on the value specified for **@conflict_logging**.  
  
    |@conflict_logging value|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**subscriber**|0|1|  
    |**both**|1|1|  
  
2.  At either the Publisher on the publication database or at the Subscriber on the subscription database, execute [sp_helpmergearticleconflicts](assetId:///4678a2b9-9a5f-4193-a20d-2e11fc896c3a). Specify a value for **@publication** to only return conflict information for articles that belong to a specific publication. This returns conflict table information for articles with conflicts. Note the value of **conflict_table** for any articles of interest. If the value of **conflict_table** for an article is NULL, only delete conflicts have occurred in this article.  
  
3.  (Optional) Review conflict rows for articles of interest. Depending on the values of **centralized_conflicts** and **decentralized_conflicts** from step 1, do one of the following:  
  
    -   At the Publisher on the publication database, execute [sp_helpmergeconflictrows](assetId:///131395a5-cb18-4795-a7ae-fa09d8ff347f). Specify a conflict table for the article (from step 1) for **@conflict_table**. (Optional) Specify a value of **@publication** to restrict returned conflict information to a specific publication. This returns row data and other information for the losing row.  
  
    -   At the Subscriber on the subscription database, execute [sp_helpmergeconflictrows](assetId:///131395a5-cb18-4795-a7ae-fa09d8ff347f). Specify a conflict table for the article (from step 1) for **@conflict_table**. This returns row data and other information for the losing row.  
  
### To view information only on conflicts where the delete failed  
  
1.  At the Publisher on the publication database, execute [sp_helpmergepublication](assetId:///dfe1e1e1-9a65-406a-aced-6385a078e135). Note the values of the following columns in the result set:  
  
    -   **centralized_conflicts** - 1 indicates that conflict rows are stored at the Publisher, and 0 indicates that conflict rows are not stored at the Publisher.  
  
    -   **decentralized_conflicts** - 1 indicates that conflict rows are stored at the Subscriber, and 0 indicates that conflict rows are not stored at the Subscriber.  
  
        > [!NOTE]  
        >  The conflict logging behavior of a merge publication is set using the **@conflict_logging** parameter of [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a). Use of the **@centralized_conflicts** parameter has been deprecated.  
  
2.  At either the Publisher on the publication database or at the Subscriber on the subscription database, execute [sp_helpmergearticleconflicts](assetId:///4678a2b9-9a5f-4193-a20d-2e11fc896c3a). Specify a value for **@publication** to only return conflict table information for articles that belong to a specific publication. This returns conflict table information for articles with conflicts. Note the value of **source_object** for any articles of interest. If the value of **conflict_table** for an article is NULL, only delete conflicts have occurred in this article.  
  
3.  (Optional) Review conflict information for delete conflicts. Depending on the values of **centralized_conflicts** and **decentralized_conflicts** from step 1, do one of the following:  
  
    -   At the Publisher on the publication database, execute [sp_helpmergedeleteconflictrows](assetId:///222be651-5690-4341-9dfb-f9ec1d80c970). Specify the name of the source table (from step 1) on which the conflict occurred for **@source_object**. (Optional) Specify a value of **@publication** to restrict returned conflict information to a specific publication. This returns delete conflict information stored at the Publisher.  
  
    -   At the Subscriber on the subscription database, execute [sp_helpmergedeleteconflictrows](assetId:///222be651-5690-4341-9dfb-f9ec1d80c970). Specify the name of the source table (from step 1) on which the conflict occurred for **@source_object**. (Optional) Specify a value of **@publication** to restrict returned conflict information to a specific publication. This returns delete conflict information stored at the Subscriber.  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics/TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)