---
title: Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)
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
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
---
# Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)
  Merge replication uses triggers as part of the replication process; when an update is made to published table, an update trigger fires. In some cases, data can be updated without the trigger firing, such as during the WRITETEXT and UPDATETEXT operations. In these cases, you need to add a dummy UPDATE statement explicitly to replicate the change. You can add a dummy UPDATE statement using replication stored procedures.  
  
### To add a dummy UPDATE statement  
  
1.  Execute the operation \(for example, UPDATETEXT\) on a row in a merge published table  that requires a dummy update.  
  
2.  At the server \(Publisher or Subscriber\) on the database where the change was made, execute [sp_mergedummyupdate &#40;Transact-SQL&#41;](../Topic/sp_mergedummyupdate%20\(Transact-SQL\).md). Specify the table on which the change was made for **@source\_object**, and the unique identifier of the changed row for **@rowguid**.  
  
3.  Synchronize the subscription to replicate the changed row.  
  
  