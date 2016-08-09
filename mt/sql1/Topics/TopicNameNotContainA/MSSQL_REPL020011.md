---
title: "MSSQL_REPL020011"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_REPL020011
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20011|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The process could not execute '%1' on '%2'.|  
  
## Explanation  
 This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp_replcmds** (The process could not execute 'sp_replcmds' on <ServerName\>) or **sp_repldone** (The process could not execute 'sp_repldone' on <ServerName\>).  
  
## User Action  
 If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp_replrestart** if appropriate. For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../Topics/TopicNameNotContainA/Strategies-for-Backing-Up-and-Restoring-Snapshot-and-Transactional-Replication.md).  
  
 This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured. If you cannot remove replication, contact customer support for assistance.  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)   
 [sp_replcmds (Transact-SQL)](assetId:///7e932f80-cc6e-4109-8db4-2b7c8828df73)   
 [sp_repldone (Transact-SQL)](assetId:///045d3cd1-712b-44b7-a56a-c9438d4077b9)