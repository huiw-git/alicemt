---
title: "Copy-Only Backups (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
caps.latest.revision: 46
caps.handback.revision: 0
manager: jhubbard
---
# Copy-Only Backups (SQL Server)
A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backups. Usually, taking a backup changes the database and affects how later backups are restored. However, occasionally, it is useful to take a backup for a special purpose without affecting the overall backup and restore procedures for the database. Copy-only backups serve this purpose.  
  
 The types of copy-only backups are as follows:  
  
-   Copy-only full backups (all recovery models)  
  
     A copy-only backup cannot serve as a differential base or differential backup and does not affect the differential base.  
  
     Restoring a copy-only full backup is the same as restoring any other full backup.  
  
-   Copy-only log backups (full recovery model and bulk-logged recovery model only)  
  
     A copy-only log backup preserves the existing log archive point and, therefore, does not affect the sequencing of regular log backups. Copy-only log backups are typically unnecessary. Instead, you can create a new routine log backup (using WITH NORECOVERY) and use that backup together with any previous log backups that are required for the restore sequence. However, a copy-only log backup can sometimes be useful for performing an online restore. For an example of this, see [Example: Online Restore of a Read-Write File (Full Recovery Model)](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md).  
  
     The transaction log is never truncated after a copy-only backup.  
  
 Copy-only backups are recorded in the **is_copy_only** column of the [backupset](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943) table.  
  
## To Create a Copy-Only Backup  
 You can create a copy-only backup by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], or PowerShell.  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
1.  On the **General** page of the **Back Up Database** dialog box, select the **Copy Only Backup** option.  
  
###  <a name="TsqlProcedure"></a> Using Transact-SQL  
 The essential [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] syntax is as follows:  
  
-   For a copy-only full backup:  
  
     BACKUP DATABASE *database_name* TO <backup_device*>* … WITH COPY_ONLY …  
  
    > [!NOTE]  
    >  COPY_ONLY has no effect when specified with the DIFFERENTIAL option.  
  
-   For a copy-only log backup:  
  
     BACKUP LOG *database_name* TO *<*backup_device*>* … WITH COPY_ONLY …  
  
###  <a name="PowerShellProcedure"></a> Using PowerShell  
  
1.  Use the **Backup-SqlDatabase** cmdlet with the **-CopyOnly** parameter.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To create a full or log backup**  
  
-   [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
-   [Back Up a Transaction Log (SQL Server)](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)  
  
 **To view copy-only backups**  
  
-   [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics/TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md)   
 [Recovery Models (SQL Server)](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)   
 [Copy Databases with Backup and Restore](../../Topics/TopicNameNotContainA/Copy-Databases-with-Backup-and-Restore.md)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)