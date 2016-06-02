---
title: File Restores (Simple Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
---
# File Restores (Simple Recovery Model)
  This topic is relevant only for simple\-model databases that contain at least one read\-only secondary filegroup.  
  
 In a file restore, the goal is to restore one or more damaged files without restoring the whole database. Under the simple recovery model, file backups are supported only for read\-only files. The primary filegroup and read\/write secondary filegroups are always restored together, by restoring a database or partial backup.  
  
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
  
-   [Overview of File and Filegroup Restore Under the Simple Recovery Model](#Overview)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Overview"></a> Overview of File and Filegroup Restore Under the Simple Recovery Model  
 A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:  
  
1.  Restore each damaged file from its most recent file backup.  
  
2.  Restore the most recent differential file backup for each restored file and recover the database.  
  
### Transact\-SQL Steps for File Restore Sequence \(Simple Recovery Model\)  
 This section shows the essential [!INCLUDE[tsql](../../Token\Other/tsql_md.md)][RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) options for a simple file\-restore sequence. Syntax and details that are not relevant to this purpose are omitted.  
  
 The restore sequence contains only two [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements. The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY. The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:  
  
1.  RESTORE DATABASE *database* FILE **\=***name\_of\_file\_A*  
  
     FROM *file\_backup\_of\_file\_A*  
  
     WITH NORECOVERY**;**  
  
2.  RESTORE DATABASE *database* FILE **\=***name\_of\_file\_B***,***name\_of\_file\_C*  
  
     FROM *file\_backup\_of\_files\_B\_and\_C*  
  
     WITH RECOVERY**;**  
  
### Examples  
  
-   [Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;](../Topic/Example:%20Offline%20Restore%20of%20Primary%20and%20One%20Other%20Filegroup%20\(Full%20Recovery%20Model\).md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To restore files and filegroups**  
  
-   [Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20over%20Existing%20Files%20\(SQL%20Server\).md)  
  
-   [Restore Files and Filegroups &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Restore Files and Filegroups &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Restore.SqlRestore Method \(Server\)](../Topic/SqlRestore%20Method.md) \(SMO\)  
  
## See Also  
 [Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](../Topic/Backup%20and%20Restore:%20Interoperability%20and%20Coexistence%20\(SQL%20Server\).md)   
 [Differential Backups &#40;SQL Server&#41;](../Topic/Differential%20Backups%20\(SQL%20Server\).md)   
 [Full File Backups &#40;SQL Server&#41;](../Topic/Full%20File%20Backups%20\(SQL%20Server\).md)   
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  