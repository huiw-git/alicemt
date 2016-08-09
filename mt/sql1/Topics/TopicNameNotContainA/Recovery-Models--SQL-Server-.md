---
title: "Recovery Models (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cfea566-8f89-4581-b30d-c53f1f2c79eb
caps.latest.revision: 70
caps.handback.revision: 0
manager: jhubbard
---
# Recovery Models (SQL Server)
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup and restore operations occur within the context of the recovery model of the database. Recovery models are designed to control transaction log maintenance. A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires (and allows) backing up, and what kinds of restore operations are available. Three recovery models exist: simple, full, and bulk-logged. Typically, a database uses the full recovery model or simple recovery model. A database can be switched to another recovery model at any time.  
  
 **In this Topic:**  
  
-   [Recovery Model Overview](#RMov)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="RMov"></a> Recovery Model Overview  
 The following table summarizes the three recovery models.  
  
|Recovery model|Description|Work loss exposure|Recover to point in time?|  
|--------------------|-----------------|------------------------|-------------------------------|  
|**Simple**|No log backups.<br /><br /> Automatically reclaims log space to keep space requirements small, essentially eliminating the need to manage the transaction log space. For information about database backups under the simple recovery model, see [Full Database Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-Database-Backups--SQL-Server-.md).<br /><br /> Operations that require transaction log backups are not supported by the simple recovery model. The following features cannot be used in simple recovery mode:<br /><br /> -Log shipping<br /><br /> -Always On or Database mirroring<br /><br /> -Media recovery without data loss<br /><br /> -Point-in-time restores|Changes since the most recent backup are unprotected. In the event of a disaster, those changes must be redone.|Can recover only to the end of a backup. For more information, see [Complete Database Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Simple-Recovery-Model-.md).|  
|**Full**|Requires log backups.<br /><br /> No work is lost due to a lost or damaged data file.<br /><br /> Can recover to an arbitrary point in time (for example, prior to application or user error). For information about database backups under the full recovery model, see [Full Database Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-Database-Backups--SQL-Server-.md) and [Complete Database Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Full-Recovery-Model-.md).|Normally none.<br /><br /> If the tail of the log is damaged, changes since the most recent log backup must be redone.|Can recover to a specific point in time, assuming that your backups are complete up to that point in time. For information about using log backups to restore to the point of failure, see [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md).<br /><br /> Note: If you have two or more full-recovery-model databases that must be logically consistent, you may have to implement special procedures to make sure the recoverability of these databases. For more information, see [Recovery of Related  Databases That Contain Marked Transaction](../../Topics/TopicNameNotContainA/Recovery-of-Related--Databases-That-Contain-Marked-Transaction.md).|  
|**Bulk logged**|Requires log backups.<br /><br /> An adjunct of the full recovery model that permits high-performance bulk copy operations.<br /><br /> Reduces log space usage by using minimal logging for most bulk operations. For information about operations that can be minimally logged, see [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md).<br /><br /> For information about database backups under the bulk-logged recovery model, see [Full Database Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-Database-Backups--SQL-Server-.md) and [Complete Database Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Full-Recovery-Model-.md).|If the log is damaged or bulk-logged operations occurred since the most recent log backup, changes since that last backup must be redone.<br /><br /> Otherwise, no work is lost.|Can recover to the end of any backup. Point-in-time recovery is not supported.|  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [View or Change the Recovery Model of a Database (SQL Server)](../../Topics/TopicNameContainA/View-or-Change-the-Recovery-Model-of-a-Database--SQL-Server-.md)  
  
-   [Troubleshoot a Full Transaction Log (SQL Server Error 9002)](../../Topics/TopicNameContainA/Troubleshoot-a-Full-Transaction-Log--SQL-Server-Error-9002-.md)  
  
## See Also  
 [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)   
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)   
 [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)   
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md)   
 [Automating Administrative Tasks (SQL Server Agent)](assetId:///541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)