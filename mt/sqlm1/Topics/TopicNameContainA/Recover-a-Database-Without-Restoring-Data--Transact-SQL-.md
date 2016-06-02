---
title: Recover a Database Without Restoring Data (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
---
# Recover a Database Without Restoring Data (Transact-SQL)
  Usually, all of the data in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database is restored before the database is recovered. However, a restore operation can recover a database without actually restoring a backup; for example, when recovering a read\-only file that is consistent with the database. This is referred to as a *recovery\-only restore*. When offline data is already consistent with the database and needs only to be made available, a recovery\-only restore operation completes the recovery of the database and bring the data online.  
  
 A recovery\-only restore can occur for a whole database or for one or more a files or filegroups.  
  
## Recovery\-Only Database Restore  
 A recovery\-only database restore can be useful in the following situations:  
  
-   You did not recover the database when restoring the last backup in a restore sequence, and you now want to recover the database to bring it online.  
  
-   The database is in standby mode, and you want to make the database updatable without applying another log backup.  
  
 The [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) syntax for a recovery\-only database restore is as follows:  
  
 RESTORE DATABASE *database\_name* WITH RECOVERY  
  
> [!NOTE]  
>  The FROM **\=** \<*backup\_device\>* clause is not used for recovery\-only restores because no backup is necessary.  
  
 **Example**  
  
 The following example recovers the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] sample database in a restore operation without restoring data.  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## Recovery\-Only File Restore  
 A recovery\-only file restore can be useful in the following situation:  
  
 A database is restored piecemeal. After restore of the primary filegroup is complete, one or more of the unrestored files are consistent with the new database state, perhaps because it has been read\-only for some time. These files only have to be recovered; data copying is unnecessary.  
  
 A recovery\-only restore operation brings the data in the offline filegroup online; no data\-copy, redo, or undo phase occurs. For information about the phases of restore, see [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md).  
  
 The [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) syntax for a recovery\-only file restore is:  
  
 RESTORE DATABASE *database\_name* { FILE **\=***logical\_file\_name* | FILEGROUP **\=***logical\_filegroup\_name* }\[ **,**...*n* \] WITH RECOVERY  
  
 **Example**  
  
 The following example illustrates a recovery\-only file restore of the files in a secondary filegroup, `SalesGroup2`, in the `Sales` database. The primary filegroup has already been restored as the initial step of a piecemeal restore, and `SalesGroup2` is consistent with the restored primary filegroup. Recovering this filegroup and bringing it online requires only a single statement.  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## Examples of Completing a Piecemeal Restore Scenario with a Recovery\-Only Restore  
 **Simple recovery model**  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
 **Full recovery model**  
  
-   [Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Full%20Recovery%20Model\).md)  
  
-   [SqlRestore](assetId:///M:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore(Microsoft.SqlServer.Management.Smo.Server))  
  
## See Also  
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [File Restores &#40;Full Recovery Model&#41;](../Topic/File%20Restores%20\(Full%20Recovery%20Model\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  