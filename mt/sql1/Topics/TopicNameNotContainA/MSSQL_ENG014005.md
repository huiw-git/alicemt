---
title: "MSSQL_ENG014005"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014005
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14005|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Could not drop publication. A subscription exists to it.|  
  
## Explanation  
 You have tried to drop a publication which has one or more associated subscriptions. A publication can only be dropped if there are no associated subscriptions.  
  
## User Action  
 Drop the subscriptions before dropping the publication. If you use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to drop the publication, it will give you the option to automatically drop all associated subscriptions before dropping the publication. If you use stored procedures, you must explicitly drop the subscriptions first. For more information, see [Delete a Push Subscription](../../Topics/TopicNameContainA/Delete-a-Push-Subscription.md) and [Delete a Pull Subscription](../../Topics/TopicNameContainA/Delete-a-Pull-Subscription.md).  
  
 If no subscriptions appear to exist for the publication or if you see this error when you create a publication, you might have a previous subscription that was not completely cleaned up when it was removed. Execute [sp_removedbreplication (Transact-SQL)](assetId:///cb98d571-d1eb-467b-91f7-a6e091009672) on the database to remove all objects and settings related to replication.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)