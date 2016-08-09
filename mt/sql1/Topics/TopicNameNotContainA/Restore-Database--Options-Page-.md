---
title: "Restore Database (Options Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
caps.latest.revision: 69
caps.handback.revision: 0
manager: jhubbard
---
# Restore Database (Options Page)
Use the **Options** page of the **Restore Database** dialog box to modify the behavior and outcome of the restore operation.  
  
 **To use SQL Server Management Studio to restore a database backup**  
  
-   [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)  
  
-   [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md)  
  
> [!NOTE]  
>  When you specify a restore task by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], you can generate a corresponding [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script containing the RESTORE statements for this restore operation. To generate the script, click **Script** and then select a destination for the script. For information about the RESTORE syntax, see [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1).  
  
## Options  
  
### Restore options  
 To modify aspects of the behavior of the restore operation, use the options of the **Restore options** panel.  
  
 **Overwrite the existing database [WITH REPLACE]**  
 The restore operation will overwrite the files of any database that is currently using the database name that you are specifying in the **Restore to**field on the [General](../../Topics/TopicNameNotContainA/Restore-Database--General-Page-.md) page of the **Restore Database** dialog box. The files of the existing database will be overwritten even if you are restoring backups from a different database to the existing database name. Selecting this option is equivalent to using the REPLACE option in a [RESTORE](assetId:///4bfe5734-3003-4165-afd4-b1131ea26e2b) statement ([!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]).  
  
> [!CAUTION]  
>  Use this option only after careful consideration. For more information, see [RESTORE Arguments (Transact-SQL)](assetId:///4bfe5734-3003-4165-afd4-b1131ea26e2b).  
  
 **Preserve the replication settings [WITH KEEP_REPLICATION]**  
 Preserves the replication settings when restoring a published database to a server other than the server where the database was created. This option is relevant only if the database was replicated when the backup was created.  
  
 This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions** option (described later in this table), which is equivalent to restoring a backup with the RECOVERY option.  
  
 Selecting this option is equivalent to using the KEEP_REPLICATION option in a [RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1) statement.  
  
 For more information, see [Back Up and Restore Replicated Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md).  
  
 **Restrict access to the restored database [WITH RESTRICTED_USER]**  
 Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.  
  
 Selecting this option is synonymous to using the RESTRICTED_USER option in a RESTORE statement.  
  
### Recovery state  
 To determine the state of the database after the store operation, you must select one of the options of the **Recovery state** panel.  
  
 **RESTORE WITH RECOVERY**  
 Recovers the database after restoring the final backup checked in the **Backup sets to restore**grid on the [General page](../../Topics/TopicNameNotContainA/Restore-Database--General-Page-.md). This is the default option and is equivalent to specifying WITH RECOVERY in a [RESTORE](assetId:///4bfe5734-3003-4165-afd4-b1131ea26e2b) statement ([!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]).  
  
> [!NOTE]  
>  Under the full recovery model or bulk-logged recovery model, choose this option only if you are restoring all the log files now.  
  
 **RESTORE WITH NORECOVERY**  
 Leaves the database in the restoring state. This allows you to restore additional backups in the current recovery path. To recover the database, you will have to perform a restore operation by using the RESTORE WITH RECOVERY option (see the preceding option).  
  
 This option is equivalent to specifying WITH NORECOVERY in a RESTORE statement.  
  
 If you select this option, the **Preserve replication settings** option is unavailable.  
  
 **RESTORE WITH STANDBY**  
 Leaves the database in a standby state, in which the database is available for limited read-only access. This option is equivalent to specifying WITH STANDBY in a RESTORE statement.  
  
 Choosing this option requires that you specify a standby file in the **Standby file** text box. The standby file allows the recovery effects to be undone.  
  
 **Standby file**  
 Specifies a standby file. You can browse for the standby file or enter its pathname directly in the text box.  
  
### Tail-Log backup  
 Allows you to designate that a tail-log backup be performed along with the database restore.  
  
 **Take tail-Log backup before restoring**  
 Check this box to designate that a tail-log backup should be performed.  
  
> [!NOTE]  
>  If the point-in-time you have selected in the [Backup Timeline](../../Topics/TopicNameNotContainA/Backup-Timeline.md) dialog box requires a tail-log backup, this box will be selected and you will not be able to edit it.  
  
 **Backup file**  
 Specifies a backup file for the tail of the log. You can browse for the backup file or enter its name directly in the text box.  
  
### Server connections  
 Allows you to close existing database connections.  
  
 **Close existing connections**  
 Restore operations may fail if there are active connections to the database. Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] and the database are closed. This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.  
  
### Prompt  
 **Prompt before restoring each backup**  
 Specifies that after each backup is restored, the **Continue with Restore** dialog box will be displayed to inquire whether you want to continue the restore sequence. This dialog box displays the name of the next media set (if known) and the name and description of the next backup set.  
  
 This option allows you to pause a restore sequence after restoring any of the backups. This option is particularly useful when you must swap tapes for different media sets; for example, when your server has only one tape device. When you are ready to proceed, click **OK**.  
  
 You can interrupt a restore sequence by clicking **No**. This leaves the database is in the restoring state. At your convenience, you can later continue the restore sequence by resuming with the next backup described in the **Continue with Restore** dialog box. The procedure restoring the next backup depends on whether it contains data or transaction log, as follows:  
  
-   If the next backup is a full or differential backup, use the **Restore Database** task again.  
  
-   If the next backup is a file backup, use the **Restore Files and Filegroup**s task. For more information, see [Restore Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups--SQL-Server-.md).  
  
-   If the next backup is a log backup, use the **Restore Transaction Log** task. For information about resuming a restore sequence by restoring a transaction log, see [Restore a Transaction Log Backup (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Transaction-Log-Backup--SQL-Server-.md).  
  
## See Also  
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)   
 [Restore a Backup from a Device (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Backup-from-a-Device--SQL-Server-.md)   
 [Restore a Transaction Log Backup (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Transaction-Log-Backup--SQL-Server-.md)   
 [Media Sets, Media Families, and Backup Sets (SQL Server)](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)   
 [Apply Transaction Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Apply-Transaction-Log-Backups--SQL-Server-.md)   
 [Restore Database (General Page)](../../Topics/TopicNameNotContainA/Restore-Database--General-Page-.md)