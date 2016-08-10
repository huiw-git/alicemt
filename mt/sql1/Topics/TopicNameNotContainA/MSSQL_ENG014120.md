---
title: "MSSQL_ENG014120"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014120
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14120|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Could not drop the distribution database '%s'. This distributor database is associated with a Publisher.|  
  
## Explanation  
 The distribution database stores metadata and history data for all types of replication and transactions for transactional replication. This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.  
  
## User Action  
 To drop a distribution database you must first drop the association between the Distributor and the Publisher. For more information, see [sp_dropdistpublisher (Transact-SQL)](assetId:///c0bdd3de-3be0-455c-898a-98d4660e7ce3).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)   
 [Configure Distribution](../../Topics/TopicNameNotContainA/Configure-Distribution.md)