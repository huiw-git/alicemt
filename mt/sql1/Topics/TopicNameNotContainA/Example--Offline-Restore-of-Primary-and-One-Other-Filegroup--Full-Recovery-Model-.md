---
title: "Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)
This topic is relevant only for databases under the full recovery model that contain multiple filegroups.  
  
 In this example, a database named `adb` contains three filegroups. Filegroups `A` and `C` are read/write, and filegroup `B` is read-only. The primary filegroup and filegroup `B` are damaged, but filegroups `A` and `C` are intact. Before the disaster, all the filegroups were online.  
  
 The database administrator decides to restore and recover the primary filegroup and filegroup `B`. The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database. When the database comes on line, Filegroups `A` and `C` are automatically brought online.  
  
> [!NOTE]  
>  The offline restore sequence has fewer steps than an online restore of a read-only file. For an example, see [Example: Online Restore of a Read-Only File (Full Recovery Model)](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md). However, the whole database is offline for the duration of the sequence.  
  
## Tail-Log Backup  
 Before restoring the database, the database administrator must back up the tail of the log. Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 The tail-log backup is the last backup that is applied in the following restore sequences.  
  
## Restore Sequence  
 To restore the primary filegroup and filegroup `B`, the database administrator uses a restore sequence without the PARTIAL option, as follows:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 The files that are not restored are automatically brought online. All the filegroups are now online.  
  
## See Also  
 [Online Restore (SQL Server)](../../Topics/TopicNameNotContainA/Online-Restore--SQL-Server-.md)   
 [Piecemeal Restores (SQL Server)](../../Topics/TopicNameNotContainA/Piecemeal-Restores--SQL-Server-.md)   
 [File Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/File-Restores--Full-Recovery-Model-.md)   
 [Apply Transaction Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Apply-Transaction-Log-Backups--SQL-Server-.md)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)