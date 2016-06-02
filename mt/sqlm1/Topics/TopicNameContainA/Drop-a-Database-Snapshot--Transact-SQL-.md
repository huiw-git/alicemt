---
title: Drop a Database Snapshot (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
---
# Drop a Database Snapshot (Transact-SQL)
  Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and deletes the sparse files that are used by the snapshot. When you drop a database snapshot, all user connections to it are terminated.  
  
## Security  
  
###  <a name="Permissions"></a> Permissions  
 Any user with DROP DATABASE permissions can drop a database snapshot.  
  
##  <a name="TsqlProcedure"></a> How to Drop a Database Snapshot \(Using Transact\-SQL\)  
 **To drop a database snapshot**  
  
1.  Identify the database snapshot that you want to drop. You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information, see [View a Database Snapshot &#40;SQL Server&#41;](../Topic/View%20a%20Database%20Snapshot%20\(SQL%20Server\).md).  
  
2.  Issue a [DROP DATABASE](../Topic/DROP%20DATABASE%20\(Transact-SQL\).md) statement, specifying the name of the database snapshot to be dropped. The syntax is as follows:  
  
     DROP DATABASE *database\_snapshot\_name* \[ **,**...*n* \]  
  
     Where *database\_snapshot\_name* is the name of the database snapshot to be dropped.  
  
####  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.  
  
> [!NOTE]  
>  For information about the use of sparse files by database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
-   [View a Database Snapshot &#40;SQL Server&#41;](../Topic/View%20a%20Database%20Snapshot%20\(SQL%20Server\).md)  
  
-   [Revert a Database to a Database Snapshot](../../Topics\TopicNameContainA/Revert-a-Database-to-a-Database-Snapshot.md)  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [&#91;Top&#93;](#Top)  
  
## See Also  
 [DROP DATABASE &#40;Transact-SQL&#41;](../Topic/DROP%20DATABASE%20\(Transact-SQL\).md)   
 [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)  
  
  