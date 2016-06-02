---
title: Recovery Models (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cfea566-8f89-4581-b30d-c53f1f2c79eb
---
# Recovery Models (SQL Server)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup and restore operations occur within the context of the recovery model of the database. Recovery models are designed to control transaction log maintenance. A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires \(and allows\) backing up, and what kinds of restore operations are available. Three recovery models exist: simple, full, and bulk\-logged. Typically, a database uses the full recovery model or simple recovery model. A database can be switched to another recovery model at any time.  
  
 **In this Topic:**  
  
-   [Recovery Model Overview](#RMov)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="RMov"></a> Recovery Model Overview  
 The following table summarizes the three recovery models.  
  
|Recovery model|Description|Work loss exposure|Recover to point in time?|  
|--------------------|-----------------|------------------------|-------------------------------|  
|**Simple**|No log backups.<br /><br /> Automatically reclaims log space to keep space requirements small, essentially eliminating the need to manage the transaction log space. For information about database backups under the simple recovery model, see [Full Database Backups &#40;SQL Server&#41;](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md).<br /><br /> Operations that require transaction log backups are not supported by the simple recovery model. The following features cannot be used in simple recovery mode:<br /><br /> \-Log shipping<br /><br /> \-Always On or Database mirroring<br /><br /> \-Media recovery without data loss<br /><br /> \-Point\-in\-time restores|Changes since the most recent backup are unprotected. In the event of a disaster, those changes must be redone.|Can recover only to the end of a backup. For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md).|  
|**Full**|Requires log backups.<br /><br /> No work is lost due to a lost or damaged data file.<br /><br /> Can recover to an arbitrary point in time \(for example, prior to application or user error\). For information about database backups under the full recovery model, see [Full Database Backups &#40;SQL Server&#41;](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md) and [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md).|Normally none.<br /><br /> If the tail of the log is damaged, changes since the most recent log backup must be redone.|Can recover to a specific point in time, assuming that your backups are complete up to that point in time. For information about using log backups to restore to the point of failure, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md).<br /><br /> Note: If you have two or more full\-recovery\-model databases that must be logically consistent, you may have to implement special procedures to make sure the recoverability of these databases. For more information, see [Recovery of Related  Databases That Contain Marked Transaction](../../Topics\TopicNameNotContainA/Recovery-of-Related--Databases-That-Contain-Marked-Transaction.md).|  
|**Bulk logged**|Requires log backups.<br /><br /> An adjunct of the full recovery model that permits high\-performance bulk copy operations.<br /><br /> Reduces log space usage by using minimal logging for most bulk operations. For information about operations that can be minimally logged, see [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md).<br /><br /> For information about database backups under the bulk\-logged recovery model, see [Full Database Backups &#40;SQL Server&#41;](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md) and [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md).|If the log is damaged or bulk\-logged operations occurred since the most recent log backup, changes since that last backup must be redone.<br /><br /> Otherwise, no work is lost.|Can recover to the end of any backup. Point\-in\-time recovery is not supported.|  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md)  
  
-   [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../Topic/Troubleshoot%20a%20Full%20Transaction%20Log%20\(SQL%20Server%20Error%209002\).md)  
  
## See Also  
 [backupset &#40;Transact-SQL&#41;](../Topic/backupset%20\(Transact-SQL\).md)   
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)   
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)   
 [Automated Administration Tasks &#40;SQL Server Agent&#41;](../Topic/Automated%20Administration%20Tasks%20\(SQL%20Server%20Agent\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)  
  
  