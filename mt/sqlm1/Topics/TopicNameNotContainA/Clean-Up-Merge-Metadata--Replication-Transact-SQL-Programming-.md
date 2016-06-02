---
title: Clean Up Merge Metadata (Replication Transact-SQL Programming)
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
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
---
# Clean Up Merge Metadata (Replication Transact-SQL Programming)
  Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication. This occurs at the Publisher and Subscriber in the [MSmerge\_genhistory](../Topic/MSmerge_genhistory%20\(Transact-SQL\).md), [MSmerge\_contents](../Topic/MSmerge_contents%20\(Transact-SQL\).md), [MSmerge\_tombstone](../Topic/MSmerge_tombstone%20\(Transact-SQL\).md), [MSmerge\_past\_partition\_mappings](../Topic/MSmerge_past_partition_mappings%20\(Transact-SQL\).md), and [MSmerge\_current\_partition\_mappings](../Topic/MSmerge_current_partition_mappings.md) system tables. You can also programmatically clean up the data in these tables using replication stored procedures.  
  
### To manually clean up merge metadata  
  
1.  At the Publisher on the publication database, execute [sp\_mergemetadataretentioncleanup](../Topic/sp_mergemetadataretentioncleanup%20\(Transact-SQL\).md).  
  
2.  \(Optional\) Note the number of rows removed in step 1 from the [MSmerge\_genhistory](../Topic/MSmerge_genhistory%20\(Transact-SQL\).md), [MSmerge\_contents](../Topic/MSmerge_contents%20\(Transact-SQL\).md), and [MSmerge\_tombstone](../Topic/MSmerge_tombstone%20\(Transact-SQL\).md) system tables, returned respectively in the **@num\_genhistory\_rows**, **@num\_contents\_rows**, and **@num\_tombstone\_rows** output parameters.  
  
3.  Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.  
  
## See Also  
 [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md)  
  
  