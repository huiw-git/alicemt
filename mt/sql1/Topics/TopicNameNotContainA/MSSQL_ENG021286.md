---
title: "MSSQL_ENG021286"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG021286
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21286|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Conflict table '%s' does not exist.|  
  
## Explanation  
 This error is raised if the conflict table for an article listed in [sysmergearticles (Transact-SQL)](assetId:///e9b1648e-4660-4688-9f56-18b2baf7228c) does not actually exist. The error can occur when you attempt to add a column to or drop a column from a table published for merge replication.  
  
## User Action  
 Execute [DBCC CHECKDB (Transact-SQL)](assetId:///2c506167-0b69-49f7-9282-241e411910df) on the database with the missing conflict table to verify there are no data consistency issues.  
  
 If the conflict table is missing on a Subscriber, drop the subscription and recreate it. If the conflict table is missing on a Publisher, drop all subscriptions, drop the publication, and then recreate the publication and all subscriptions. For more information, see [Publish Data and Database Objects](../../Topics/TopicNameNotContainA/Publish-Data-and-Database-Objects.md) and [Subscribe to Publications](../../Topics/TopicNameNotContainA/Subscribe-to-Publications.md).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)