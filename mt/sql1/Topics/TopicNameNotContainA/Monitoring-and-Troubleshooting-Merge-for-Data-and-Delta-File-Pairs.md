---
title: "Monitoring and Troubleshooting Merge for Data and Delta File Pairs"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
robots: noindex,nofollow
---
# Monitoring and Troubleshooting Merge for Data and Delta File Pairs
In-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically. You cannot disable merge activity.  
  
 You can monitor data and delta file pairs, as follows:  
  
-   Compare the size of in-memory storage to overall size of storage. If the storage is dis-proportionately large, then it is likely that merge is not getting triggered. For information  
  
-   Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files (Transact-SQL)](assetId:///ac8e6333-7a9f-478a-b446-5602283e81c9) to see if merge is not getting triggered when it should.  
  
## See Also  
 [Creating and Managing Storage for Memory-Optimized Objects](../../Topics/TopicNameNotContainA/Creating-and-Managing-Storage-for-Memory-Optimized-Objects.md)