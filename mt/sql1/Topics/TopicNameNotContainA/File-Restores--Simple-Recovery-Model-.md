---
title: "File Restores (Simple Recovery Model)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
caps.latest.revision: 57
caps.handback.revision: 0
manager: jhubbard
---
# File Restores (Simple Recovery Model)
This topic is relevant only for simple-model databases that contain at least one read-only secondary filegroup.  
  
 In a file restore, the goal is to restore one or more damaged files without restoring the whole database. Under the simple recovery model, file backups are supported only for read-only files. The primary filegroup and read/write secondary filegroups are always restored together, by restoring a database or partial backup.  
  
 The file-restore scenarios are as follows:  
  
-   Offline file restore  
  
     In an *offline file restore*, the database is offline while damaged files or filegroups are restored. At the end of the restore sequence, the database comes online.  
  
     All editions of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] support offline file restore.  
  
-   Online file restore  
  
     In an *online file restore*, if database is online at restore time, it remains online during the file restore. However, each filegroup in which a file is being restored is offline during the restore operation. After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.  
  
     For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md). For more information about online restores, see [Online Restore (SQL Server)](../../Topics/TopicNameNotContainA/Online-Restore--SQL-Server-.md).  
  
    > [!TIP]  
    >  If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) statement: ALTER DATABASE *database_name* SET OFFLINE.  
  
 **In this Topic:**  
  
-   [Overview of File and Filegroup Restore Under the Simple Recovery Model](#Overview)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Overview"></a> Overview of File and Filegroup Restore Under the Simple Recovery Model  
 A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:  
  
1.  Restore each damaged file from its most recent file backup.  
  
2.  Restore the most recent differential file backup for each restored file and recover the database.  
  
### Transact-SQL Steps for File Restore Sequence (Simple Recovery Model)  
 This section shows the essential [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)][RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1) options for a simple file-restore sequence. Syntax and details that are not relevant to this purpose are omitted.  
  
 The restore sequence contains only two [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements. The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY. The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:  
  
1.  RESTORE DATABASE *database* FILE **=***name_of_file_A*  
  
     FROM *file_backup_of_file_A*  
  
     WITH NORECOVERY**;**  
  
2.  RESTORE DATABASE *database* FILE **=***name_of_file_B***,***name_of_file_C*  
  
     FROM *file_backup_of_files_B_and_C*  
  
     WITH RECOVERY**;**  
  
### Examples  
  
-   [Example: Online Restore of a Read-Only File (Simple Recovery Model)](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)](../Topic/Example:%20Offline%20Restore%20of%20Primary%20and%20One%20Other%20Filegroup%20\(Full%20Recovery%20Model\).md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To restore files and filegroups**  
  
-   [Restore Files and Filegroups over Existing Files (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups-over-Existing-Files--SQL-Server-.md)  
  
-   [Restore Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups--SQL-Server-.md)  
  
-   [Restore Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups--SQL-Server-.md)  
  
-   [Restore.SqlRestore Method (Server)](assetId:///cd44548c-3119-431d-bd85-435a7358bb39) (SMO)  
  
## See Also  
 [Backup and Restore: Interoperability and Coexistence (SQL Server)](../Topic/Backup%20and%20Restore:%20Interoperability%20and%20Coexistence%20\(SQL%20Server\).md)   
 [Differential Backups (SQL Server)](../../Topics/TopicNameNotContainA/Differential-Backups--SQL-Server-.md)   
 [Full File Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-File-Backups--SQL-Server-.md)   
 [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)   
 [Complete Database Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Simple-Recovery-Model-.md)   
 [Piecemeal Restores (SQL Server)](../../Topics/TopicNameNotContainA/Piecemeal-Restores--SQL-Server-.md)