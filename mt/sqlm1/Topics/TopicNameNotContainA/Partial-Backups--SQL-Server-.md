---
title: Partial Backups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
---
# Partial Backups (SQL Server)
  All [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases. However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read\-only filegroups.  
  
 Partial backups are useful whenever you want to exclude read\-only filegroups. A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups. Instead, for a read\-write database, a partial backup contains the data in the primary filegroup, every read\-write filegroup, and, optionally, one or more read\-only files. A partial backup of a read\-only database contains only the primary filegroup.  
  
> [!NOTE]  
>  If a read\-only database is changed to read\/write after a partial backup, there might be read\/write secondary filegroups that are not in the partial backup. In this case, if you try to take a differential partial backup, the backup fails. Before you can take a differential partial backup of the database, you must take another partial backup. The new partial backup contains every read\/write secondary filegroup and can serve as the base for differential partial backups.  
  
 File backups of read\-only filegroups can be combined with partial backups. For information about file backups, see [Full File Backups &#40;SQL Server&#41;](../Topic/Full%20File%20Backups%20\(SQL%20Server\).md).  
  
 A partial backup can serve as the *differential base* for differential partial backups. For more information, see [Differential Backups &#40;SQL Server&#41;](../Topic/Differential%20Backups%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
> [!NOTE]  
>  Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or the Maintenance Plan Wizard.  
  
 **To create a partial backup**  
  
-   [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md) \(READ\_WRITE\_FILEGROUPS; FILEGROUP option, if needed\)  
  
 **To use a partial backup in a restore sequence**  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
## See Also  
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  