---
title: "MSSQL_ENG014144"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014144
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14144|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Cannot drop Subscriber '%s'. There are subscriptions for it in the publication database '%s'.|  
  
## Explanation  
 A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance that is configured as a Subscriber cannot be removed from the role of Subscriber while there are active subscriptions configured for the instance.  
  
## User Action  
 Drop all associated subscriptions before attempting to change the Subscriber status of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance:  
  
1.  Execute [sp_helpsubscription (Transact-SQL)](assetId:///ff96bcbf-e2b9-4da8-8515-d80d4ce86c16) in the publication database at the Publisher to find subscriptions.  
  
2.  Execute [sp_dropsubscription (Transact-SQL)](assetId:///7551f345-5510-4684-ab53-f9057249d13a) in the publication database to drop subscriptions.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)   
 [Subscribe to Publications](../../Topics/TopicNameNotContainA/Subscribe-to-Publications.md)