---
title: "MSSQL_ENG004929"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: 15
manager: jhubbard
---
# MSSQL_ENG004929
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|4929|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Cannot alter the %S_MSG '%.*ls' because it is being published for replication.|  
  
## Explanation  
 This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication. Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.  
  
## User Action  
 To drop the constraint, first drop the article associated with the table. For more information, see [Add Articles to and Drop Articles from Existing Publications](../../Topics/TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md). If this error occurs in a database that is not replicated, execute [sp_removedbreplication (Transact-SQL)](assetId:///cb98d571-d1eb-467b-91f7-a6e091009672) to ensure objects in the database are not marked as replicated.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)