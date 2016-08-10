---
title: "MSSQL_ENG003165"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG003165
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|3165|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Database '%ls' was restored; however, an error was encountered while replication was being restored/removed. The database has been left offline. See the topic MSSQL_ENG003165 in SQL Server Books Online.|  
  
## Explanation  
 This error is raised if a problem occurs restoring a backup of a replicated database:  
  
-   If the backup is being restored to the same database and server on which it was taken, the error indicates that replication settings could not be restored properly.  
  
-   If the backup is being restored to a different database or server, the error indicates that replication settings could not be removed properly (by default, replication settings are removed if the database or server is different).  
  
 The error is probably the result of a mismatch between the state of the restored database and one or more system databases that contain replication metadata: **msdb**, **master**, or the distribution database.  
  
## User Action  
 To resolve this issue:  
  
1.  Execute ALTER DATABASE to bring the database online; for example: `ALTER DATABASE AdventureWorks SET ONLINE`. For more information, see [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da). If you want to preserve replication settings, go to step 2. If not, go to step 3.  
  
2.  Execute [sp_restoredbreplication (Transact-SQL)](assetId:///a2c5ee32-e6d9-46e9-8031-8ff13c20acf7). If this stored procedure executes successfully, the restore is complete. If it does not execute successfully, go to step 3.  
  
3.  Execute [sp_removedbreplication (Transact-SQL)](assetId:///cb98d571-d1eb-467b-91f7-a6e091009672) to remove all replication settings.  
  
     Reconfigure replication if necessary. If you have scripted the replication topology as recommended, use scripts to reconfigure the topology.  
  
## See Also  
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Back Up and Restore Replicated Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)