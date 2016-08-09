---
title: "Partial Backups (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
caps.latest.revision: 47
caps.handback.revision: 0
manager: jhubbard
---
# Partial Backups (SQL Server)
All [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases. However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read-only filegroups.  
  
 Partial backups are useful whenever you want to exclude read-only filegroups. A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups. Instead, for a read-write database, a partial backup contains the data in the primary filegroup, every read-write filegroup, and, optionally, one or more read-only files. A partial backup of a read-only database contains only the primary filegroup.  
  
> [!NOTE]  
>  If a read-only database is changed to read/write after a partial backup, there might be read/write secondary filegroups that are not in the partial backup. In this case, if you try to take a differential partial backup, the backup fails. Before you can take a differential partial backup of the database, you must take another partial backup. The new partial backup contains every read/write secondary filegroup and can serve as the base for differential partial backups.  
  
 File backups of read-only filegroups can be combined with partial backups. For information about file backups, see [Full File Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-File-Backups--SQL-Server-.md).  
  
 A partial backup can serve as the *differential base* for differential partial backups. For more information, see [Differential Backups (SQL Server)](../../Topics/TopicNameNotContainA/Differential-Backups--SQL-Server-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
> [!NOTE]  
>  Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or the Maintenance Plan Wizard.  
  
 **To create a partial backup**  
  
-   [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1) (READ_WRITE_FILEGROUPS; FILEGROUP option, if needed)  
  
 **To use a partial backup in a restore sequence**  
  
-   [Example: Piecemeal Restore of Database (Simple Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
## See Also  
 [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md)   
 [File Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/File-Restores--Simple-Recovery-Model-.md)   
 [Piecemeal Restores (SQL Server)](../../Topics/TopicNameNotContainA/Piecemeal-Restores--SQL-Server-.md)