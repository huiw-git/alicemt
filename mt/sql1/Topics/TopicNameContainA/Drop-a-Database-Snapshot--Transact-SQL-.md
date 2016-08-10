---
title: "Drop a Database Snapshot (Transact-SQL)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# Drop a Database Snapshot (Transact-SQL)
Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and deletes the sparse files that are used by the snapshot. When you drop a database snapshot, all user connections to it are terminated.  
  
## Security  
  
###  <a name="Permissions"></a> Permissions  
 Any user with DROP DATABASE permissions can drop a database snapshot.  
  
##  <a name="TsqlProcedure"></a> How to Drop a Database Snapshot (Using Transact-SQL)  
 **To drop a database snapshot**  
  
1.  Identify the database snapshot that you want to drop. You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. For more information, see [View a Database Snapshot (SQL Server)](../../Topics/TopicNameContainA/View-a-Database-Snapshot--SQL-Server-.md).  
  
2.  Issue a [DROP DATABASE](assetId:///477396a9-92dc-43c9-9b97-42c8728ede8e) statement, specifying the name of the database snapshot to be dropped. The syntax is as follows:  
  
     DROP DATABASE *database_snapshot_name* [ **,**...*n* ]  
  
     Where *database_snapshot_name* is the name of the database snapshot to be dropped.  
  
####  <a name="TsqlExample"></a> Example (Transact-SQL)  
 This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.  
  
> [!NOTE]  
>  For information about the use of sparse files by database snapshots, see [Database Snapshots (SQL Server)](../../Topics/TopicNameNotContainA/Database-Snapshots--SQL-Server-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Database Snapshot (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Snapshot--Transact-SQL-.md)  
  
-   [View a Database Snapshot (SQL Server)](../../Topics/TopicNameContainA/View-a-Database-Snapshot--SQL-Server-.md)  
  
-   [Revert a Database to a Database Snapshot](../../Topics/TopicNameContainA/Revert-a-Database-to-a-Database-Snapshot.md)  
  
   
  
## See Also  
 [DROP DATABASE](assetId:///477396a9-92dc-43c9-9b97-42c8728ede8e)   
 [Database Snapshots (SQL Server)](../../Topics/TopicNameNotContainA/Database-Snapshots--SQL-Server-.md)