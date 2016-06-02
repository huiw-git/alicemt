---
title: MSSQL_REPL020011
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
---
# MSSQL_REPL020011
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20011|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The process could not execute '%1' on '%2'.|  
  
## Explanation  
 This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp\_replcmds** \(The process could not execute 'sp\_replcmds' on \<ServerName\>\) or **sp\_repldone** \(The process could not execute 'sp\_repldone' on \<ServerName\>\).  
  
## User Action  
 If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp\_replrestart** if appropriate. For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../Topics\TopicNameNotContainA/Strategies-for-Backing-Up-and-Restoring-Snapshot-and-Transactional-Replication.md).  
  
 This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured. If you cannot remove replication, contact customer support for assistance.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../Topic/sp_replcmds%20\(Transact-SQL\).md)   
 [sp_repldone &#40;Transact-SQL&#41;](../Topic/sp_repldone%20\(Transact-SQL\).md)  
  
  