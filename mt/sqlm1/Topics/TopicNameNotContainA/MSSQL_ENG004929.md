---
title: MSSQL_ENG004929
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
---
# MSSQL_ENG004929
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|4929|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Cannot alter the %S\_MSG '%.\*ls' because it is being published for replication.|  
  
## Explanation  
 This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication. Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.  
  
## User Action  
 To drop the constraint, first drop the article associated with the table. For more information, see [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md). If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) to ensure objects in the database are not marked as replicated.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  