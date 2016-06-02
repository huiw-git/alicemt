---
title: Monitoring and Troubleshooting Merge for Data and Delta File Pairs
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
robots: noindex,nofollow
---
# Monitoring and Troubleshooting Merge for Data and Delta File Pairs
  In\-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically. You cannot disable merge activity.  
  
 You can monitor data and delta file pairs, as follows:  
  
-   Compare the size of in\-memory storage to overall size of storage. If the storage is dis\-proportionately large, then it is likely that merge is not getting triggered. For information  
  
-   Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../Topic/sys.dm_db_xtp_checkpoint_files%20\(Transact-SQL\).md) to see if merge is not getting triggered when it should.  
  
## See Also  
 [Creating and Managing Storage for Memory-Optimized Objects](../../Topics\TopicNameNotContainA/Creating-and-Managing-Storage-for-Memory-Optimized-Objects.md)  
  
  