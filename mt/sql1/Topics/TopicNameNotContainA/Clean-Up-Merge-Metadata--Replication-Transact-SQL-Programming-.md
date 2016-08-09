---
title: "Clean Up Merge Metadata (Replication Transact-SQL Programming)"
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
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Clean Up Merge Metadata (Replication Transact-SQL Programming)
Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication. This occurs at the Publisher and Subscriber in the [MSmerge_genhistory](assetId:///475d08ae-eb8b-49de-afd6-33c96ab8004d), [MSmerge_contents](assetId:///8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1), [MSmerge_tombstone](assetId:///8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38), [MSmerge_past_partition_mappings](assetId:///06d54ff5-4d29-4eeb-b8be-64d032e53134), and [MSmerge_current_partition_mappings](assetId:///a3088840-5a30-40f5-8e8a-aa03afc4905f) system tables. You can also programmatically clean up the data in these tables using replication stored procedures.  
  
### To manually clean up merge metadata  
  
1.  At the Publisher on the publication database, execute [sp_mergemetadataretentioncleanup](assetId:///4e8d6343-2a38-421d-a3f3-c37d437a0f88).  
  
2.  (Optional) Note the number of rows removed in step 1 from the [MSmerge_genhistory](assetId:///475d08ae-eb8b-49de-afd6-33c96ab8004d), [MSmerge_contents](assetId:///8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1), and [MSmerge_tombstone](assetId:///8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38) system tables, returned respectively in the **@num_genhistory_rows**, **@num_contents_rows**, and **@num_tombstone_rows** output parameters.  
  
3.  Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.  
  
## See Also  
 [Subscription Expiration and Deactivation](../../Topics/TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md)