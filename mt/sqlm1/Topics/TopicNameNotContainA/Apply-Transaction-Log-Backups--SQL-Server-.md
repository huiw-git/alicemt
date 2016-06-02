---
title: Apply Transaction Log Backups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
---
# Apply Transaction Log Backups (SQL Server)
  The topic is relevant only for the full recovery model or bulk\-logged recovery model.  
  
 This topic describes applying transaction log backups as part of restoring a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.  
  
 **In this Topic:**  
  
-   [Requirements for Restoring Transaction Log Backups](#Requirements)  
  
-   [Recovery and Transaction Logs](#RecoveryAndTlogs)  
  
-   [Using Log Backups to Restore to the Point of Failure](#PITrestore)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Requirements"></a> Requirements for Restoring Transaction Log Backups  
 To apply a transaction log backup, the following requirements must be met:  
  
-   **Enough Log Backups for a Restore Sequence :** You must have enough log records backed up to complete a restore sequence. The necessary log backups, including the [tail\-log backup](../Topic/Tail-Log%20Backups%20\(SQL%20Server\).md) where required, must be available before the start of the restore sequence.  
  
-   **Correct restore order:**  The immediately previous full database backup or differential database backup must be restored first. Then, all transaction logs that are created after that full or differential database backup must be restored in chronological order. If a transaction log backup in this log chain is lost or damaged, you can restore only transaction logs before the missing transaction log.  
  
-   **Database not yet recovered:**  The database cannot be recovered until after the final transaction log has been applied. If you recover the database after restoring one of the intermediate transaction log backups, that before the end of the log chain, you cannot restore the database past that point without restarting the complete restore sequence, starting with the full database backup.  
  
    > [!TIP]  
    >  A best practice is to restore all the log backups \(RESTORE LOG *database\_name* WITH NORECOVERY\). Then, after restoring the last log backup, recover the database in a separate operation \(RESTORE DATABASE *database\_name* WITH RECOVERY\).  
  
##  <a name="RecoveryAndTlogs"></a> Recovery and Transaction Logs  
 When you finish the restore operation and recover the database, recovery rolls back all incomplete transactions. This is known as the *undo phase*. Rolling back is required to restore the integrity of the database. After rollback, the database goes online, and no more transaction log backups can be applied to the database.  
  
 For example, a series of transaction log backups contain a long\-running transaction. The start of the transaction is recorded in the first transaction log backup, but the end of the transaction is recorded in the second transaction log backup. There is no record of a commit or rollback operation in the first transaction log backup. If a recovery operation runs when the first transaction log backup is applied, the long\-running transaction is treated as incomplete, and data modifications recorded in the first transaction log backup for the transaction are rolled back. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not allow for the second transaction log backup to be applied after this point.  
  
> [!NOTE]  
>  In some circumstances, you can explicitly add a file during log restore.  
  
##  <a name="PITrestore"></a> Using Log Backups to Restore to the Point of Failure  
 Assume the following sequence of events.  
  
|Time|Event|  
|----------|-----------|  
|8:00 A.M.|Back up database to create a full database backup.|  
|Noon|Back up transaction log.|  
|4:00 P.M.|Back up transaction log.|  
|6:00 P.M.|Back up database to create a full database backup.|  
|8:00 P.M.|Back up transaction log.|  
|9:45 P.M.|Failure occurs.|  
  
> [!NOTE]  
>  For an explanation of this example sequence of backups, see [Transaction Log Backups &#40;SQL Server&#41;](../Topic/Transaction%20Log%20Backups%20\(SQL%20Server\).md).  
  
 To restore the database to its state at 9:45 P.M. \(the point of failure\), either of the following alternative procedures can be used:  
  
 **Alternative 1: Restore the database by using the most recent full database backup**  
  
1.  Create a tail\-log backup of the currently active transaction log as of the point of failure.  
  
2.  Do not restore the 8:00 A.M. full database backup. Instead, restore the more recent 6:00 P.M. full database backup, and then apply the 8:00 P.M. log backup and the tail\-log backup.  
  
 **Alternative 2: Restore the database by using an earlier full database backup**  
  
> [!NOTE]  
>  This alternative process is useful if a problem prevents you from using the 6:00 P.M. full database backup. This process takes longer than restoring from the 6:00 P.M. full database backup.  
  
1.  Create a tail\-log backup of the currently active transaction log as of the point of failure.  
  
2.  Restore the 8:00 A.M. full database backup, and then restore all four transaction log backups in sequence. This rolls forward all completed transactions up to 9:45 P.M.  
  
     This alternative points out the redundant security offered by maintaining a chain of transaction log backups across a series of full database backups.  
  
> [!NOTE]  
>  In some cases, you can also use transaction logs to restore a database to a specific point in time. For more information, [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To apply a transaction log backup**  
  
-   [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)  
  
 **To restore to your recovery point**  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20to%20the%20Point%20of%20Failure%20Under%20the%20Full%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md)  
  
-   [SqlRestore](assetId:///M:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore(Microsoft.SqlServer.Management.Smo.Server)) \(SMO\)  
  
-   [Recovery of Related  Databases That Contain Marked Transaction](../../Topics\TopicNameNotContainA/Recovery-of-Related--Databases-That-Contain-Marked-Transaction.md)  
  
-   [Recover to a Log Sequence Number &#40;SQL Server&#41;](../Topic/Recover%20to%20a%20Log%20Sequence%20Number%20\(SQL%20Server\).md)  
  
 **To recover a database after restoring backups using WITH NORECOVERY**  
  
-   [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../Topic/Recover%20a%20Database%20Without%20Restoring%20Data%20\(Transact-SQL\).md)  
  
## See Also  
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)  
  
  