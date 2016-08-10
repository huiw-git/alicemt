---
title: "MSSQL_ENG003724"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 14
manager: jhubbard
---
# MSSQL_ENG003724
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|3724|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Cannot %S_MSG the %S_MSG '%.*ls' because it is being used for replication.|  
  
## Explanation  
 When objects in a database are replicated, they are marked as replicated in the system table **sysarticles** (for snapshot and transactional publications) or **sysmergearticles** (for merge publications). If you attempt drop a replicated object, this error is raised.  
  
## User Action  
 Ensure the database object is not replicated before attempting to drop it. For example:  
  
-   If the error occurs in the publication database, drop the article from the publication before dropping the object. For more information, see [Add Articles to and Drop Articles from Existing Publications](../../Topics/TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md).  
  
-   If the error occurs in the subscription database, drop the subscription before dropping the object. For more information, see [Subscribe to Publications](../../Topics/TopicNameNotContainA/Subscribe-to-Publications.md). For subscriptions to transactional publications, it is possible to drop the subscription to an individual article rather than the entire publication. For more information, see [sp_dropsubscription (Transact-SQL)](assetId:///7551f345-5510-4684-ab53-f9057249d13a).  
  
 If this error occurs in a database that is not replicated, execute [sp_removedbreplication (Transact-SQL)](assetId:///cb98d571-d1eb-467b-91f7-a6e091009672) to ensure objects in the database are not marked as replicated.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)