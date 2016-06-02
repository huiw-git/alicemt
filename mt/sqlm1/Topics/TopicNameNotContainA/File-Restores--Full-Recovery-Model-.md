---
title: File Restores (Full Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2236a2a-4cf1-4c3f-b542-f73f6096e15c
---
# File Restores (Full Recovery Model)
  This topic is relevant only for databases that contain multiple files or filegroups under the full or bulk\-load recovery model.  
  
 In a file restore, the goal is to restore one or more damaged files without restoring the whole database. A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data  
  
 If the filegroup that is being restored is read\/write, an unbroken chain of log backups must be applied after the last data or differential backup is restored. This brings the filegroup forward to the log records in the current active log records in the log file. The recovery point is typically near the end of log, but not necessarily.  
  
 If the filegroup that is being restored is read\-only, usually applying log backups is unnecessary and is skipped. If the backup was taken after the file became read\-only, that is the last backup to restore. Roll forward stops at the target point.  
  
 The file\-restore scenarios are as follows:  
  
-   Offline file restore  
  
     In an *offline file restore*, the database is offline while damaged files or filegroups are restored. At the end of the restore sequence, the database comes online.  
  
     All editions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] support offline file restore.  
  
-   Online file restore  
  
     In an *online file restore*, if database is online at restore time, it remains online during the file restore. However, each filegroup in which a file is being restored is offline during the restore operation. After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.  
  
     For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md). For more information about online restores, see [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md).  
  
    > [!TIP]  
    >  If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) statement: ALTER DATABASE *database\_name* SET OFFLINE.  
  
 **In this Topic:**  
  
-   [Restoring Damaged Files from File Backups](#Overview)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Overview"></a> Restoring Damaged Files from File Backups  
  
1.  Before restoring one or more damaged files, attempt to create a [tail\-log backup](../Topic/Tail-Log%20Backups%20\(SQL%20Server\).md).  
  
     If the log has been damaged, a tail\-log backup cannot be created, and you must restore the whole database.  
  
     For information about how to back up a transaction log, see [Transaction Log Backups &#40;SQL Server&#41;](../Topic/Transaction%20Log%20Backups%20\(SQL%20Server\).md).  
  
    > [!IMPORTANT]  
    >  For an offline file restore, you must always take a tail\-log backup before the file restore. For an online file restore, you must always take the log backup after the file restore. This log backup is necessary to allow for the file to be recovered to a state consistent with the rest of the database.  
  
2.  Restore each damaged file from the most recent file backup of that file.  
  
3.  Restore the most recent differential file backup, if any, for each restored file.  
  
4.  Restore transaction log backups in sequence, starting with the backup that covers the oldest of the restored files and ending with the tail\-log backup created in step 1.  
  
     You must restore the transaction log backups that were created after the file backups to bring the database to a consistent state. The transaction log backups can be rolled forward quickly, because only the changes that apply to the restored files are applied. Restoring individual files can be better than restoring the whole database, because undamaged files are not copied and then rolled forward. However, the whole chain of log backups still has to be read.  
  
5.  Recover the database.  
  
> [!NOTE]  
>  File backups can be used to restore the database to an earlier point in time. To do this, you must restore a complete set of file backups, and then restore transaction log backups in sequence to reach a target point that is after the end of the most recent restored file backup. For more information about point\-in\-time recovery, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md).  
  
## Transact\-SQL Restore Sequence for an Offline File Restore \(Full Recovery Model\)  
 A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data.  
  
 This section shows the essential [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) options for a file\-restore sequence. Syntax and details that are not relevant to this purpose are omitted.  
  
 The following sample restore sequence shows an offline restore of two secondary files, `A` and `B`, using WITH NORECOVERY. Next, two log backups are applied with NORECOVERY, followed with the tail\-log backup, and this is restored using WITH RECOVERY.  
  
> [!NOTE]  
>  The following sample restore sequence starts by taking the file offline and then creates a tail\-log backup.  
  
```  
--Take the file offline.  
ALTER DATABASE database_name MODIFY FILE SET OFFLINE;  
-- Back up the currently active transaction log.  
BACKUP LOG database_name  
   TO <tail_log_backup>  
   WITH NORECOVERY;  
GO   
-- Restore the files.  
RESTORE DATABASE database_name FILE=name   
   FROM <file_backup_of_file_A>   
   WITH NORECOVERY;  
RESTORE DATABASE database_name FILE=<name> ......  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
-- Restore the log backups.  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <tail_log_backup>   
   WITH RECOVERY;  
```  
  
## Examples  
  
-   [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;](../Topic/Example:%20Offline%20Restore%20of%20Primary%20and%20One%20Other%20Filegroup%20\(Full%20Recovery%20Model\).md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To restore files and filegroups**  
  
-   [Restore Files to a New Location &#40;SQL Server&#41;](../Topic/Restore%20Files%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [Restore Files and Filegroups &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [SqlRestore](assetId:///M:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore(Microsoft.SqlServer.Management.Smo.Server)) \(SMO\)  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](../Topic/Backup%20and%20Restore:%20Interoperability%20and%20Coexistence%20\(SQL%20Server\).md)   
 [Differential Backups &#40;SQL Server&#41;](../Topic/Differential%20Backups%20\(SQL%20Server\).md)   
 [Full File Backups &#40;SQL Server&#41;](../Topic/Full%20File%20Backups%20\(SQL%20Server\).md)   
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  