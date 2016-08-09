---
title: "Backup Overview (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
caps.latest.revision: 83
caps.handback.revision: 0
manager: jhubbard
---
# Backup Overview (SQL Server)
This topic introduces the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup component. Backing up your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database is essential for protecting your data. This discussion covers backup types, and backup restrictions. The topic also introduces [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup devices and backup media.  
  
 **In this Topic:**  
  
-   [Components and Concepts](#TermsAndDefinitions)  
  
-   [Backup Compression](#BackupCompression)  
  
-   [Restrictions on Backup Operations in SQL Server](#Restrictions)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="TermsAndDefinitions"></a> Components and Concepts  
 back up [verb]  
 Copies the data or log records from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.  
  
 backup [noun]  
 A copy of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data that can be used to restore and recover the data after a failure. A backup of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data is created at the level of a database or one or more of its files or filegroups. Table-level backups cannot be created. In addition to data backups, the full recovery model requires creating backups of the transaction log.  
  
 [recovery model](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)  
 A database property that controls transaction log maintenance on a database. Three recovery models exist: simple, full, and bulk-logged. The recovery model of database determines its backup and restore requirements.  
  
 [restore](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)  
 A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.  
  
 **Types of Backups**  
  
 [copy-only backup](../../Topics/TopicNameNotContainA/Copy-Only-Backups--SQL-Server-.md)  
 A special-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backups.  
  
 data backup  
 A backup of data in a complete database (a database backup), a partial database (a partial backup), or a set of data files or filegroups (a file backup).  
  
 [database backup](../../Topics/TopicNameNotContainA/Full-Database-Backups--SQL-Server-.md)  
 A backup of a database. Full database backups represent the whole database at the time the backup finished. Differential database backups contain only changes made to the database since its most recent full database backup.  
  
 [differential backup](../../Topics/TopicNameNotContainA/Full-Database-Backups--SQL-Server-.md)  
 A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the *differential base*) and that contains only the data extents that have changed since the differential base.  
  
 A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.  
  
 full backup  
 A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.  
  
 [log backup](../../Topics/TopicNameNotContainA/Transaction-Log-Backups--SQL-Server-.md)  
 A backup of transaction logs that includes all log records that were not backed up in a previous log backup. (full recovery model)  
  
 [file backup](../../Topics/TopicNameNotContainA/Full-File-Backups--SQL-Server-.md)  
 A backup of one or more database files or filegroups.  
  
 [partial backup](../../Topics/TopicNameNotContainA/Partial-Backups--SQL-Server-.md)  
 Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read/write filegroup, and any optionally-specified read-only files.  
  
 **Backup Media Terms and Definitions**  
  
 [backup device](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)  
 A disk or tape device to which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backups are written and from which they can be restored. SQL Server backups can also be written to a Windows Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file.. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics/TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
 [backup media](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)  
 One or more tapes or disk files to which one or more backup have been written.  
  
 [backup set](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)  
 The backup content that is added to a media set by a successful backup operation.  
  
 [media family](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)  
 Backups created on a single nonmirrored device or a set of mirrored devices in a media set  
  
 [media set](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)  
 An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.  
  
 [mirrored media set](../../Topics/TopicNameNotContainA/Mirrored-Backup-Media-Sets--SQL-Server-.md)  
 Multiple copies (mirrors) of a media set.  
  
##  <a name="BackupCompression"></a> Backup Compression  
 [!INCLUDE[ssEnterpriseEd10](../../Topics/TopicNameContainA/tokens/ssEnterpriseEd10_md.md)] and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later versions can restore a compressed backup. For more information, see [Backup Compression (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Compression--SQL-Server-.md).  
  
##  <a name="Restrictions"></a> Restrictions on Backup Operations in SQL Server  
 Backup can occur while the database is online and being used. However, the following restrictions exist.  
  
### Offline Data Cannot Be Backed Up  
 Any backup operation that implicitly or explicitly references data that is offline fails. Some typical examples include the following:  
  
-   You request a full database backup, but one filegroup of the database is offline. Because all filegroups are implicitly included in a full database backup, this operation fails.  
  
     To back up this database, you can use a file backup and specify only the filegroups that are online.  
  
-   You request a partial backup, but a read/write filegroup is offline. Because all read/write filegroups are required for a partial backup, the operation fails.  
  
-   You request a file backup of specific files, but one of the files is not online. The operation fails. To back up the online files, you can omit the offline file from the file list and repeat the operation.  
  
 Typically, a log backup succeeds even if one or more data files are unavailable. However, if any file contains bulk-logged changes made under the bulk-logged recovery model, all the files must be online for the backup to succeed.  
  
### Concurrency Restrictions During Backup  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses an online backup process to allow for a database backup while the database is still being used. During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation. However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.  
  
 Operations that cannot run during a database backup or transaction log backup include the following:  
  
-   File-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.  
  
-   Shrink database or shrink file operations. This includes auto-shrink operations.  
  
-   If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.  
  
 If a backup operation overlaps with a file-management operation or shrink operation, a conflict occurs. Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. (The time-out period is controlled by a session time-out setting.) If the lock is released during the time-out period, the second operation continues. If the lock times out, the second operation fails.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To work with backup devices and backup media**  
  
-   [Define a Logical Backup Device for a Disk File (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Disk-File--SQL-Server-.md)  
  
-   [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md)  
  
-   [Specify a Disk or Tape As a Backup Destination (SQL Server)](../../Topics/TopicNameContainA/Specify-a-Disk-or-Tape-As-a-Backup-Destination--SQL-Server-.md)  
  
-   [Delete a Backup Device (SQL Server)](../../Topics/TopicNameContainA/Delete-a-Backup-Device--SQL-Server-.md)  
  
-   [Set the Expiration Date on a Backup (SQL Server)](../../Topics/TopicNameContainA/Set-the-Expiration-Date-on-a-Backup--SQL-Server-.md)  
  
-   [View the Contents of a Backup Tape or File (SQL Server)](../../Topics/TopicNameContainA/View-the-Contents-of-a-Backup-Tape-or-File--SQL-Server-.md)  
  
-   [View the Data and Log Files in a Backup Set (SQL Server)](../../Topics/TopicNameContainA/View-the-Data-and-Log-Files-in-a-Backup-Set--SQL-Server-.md)  
  
-   [View the Properties and Contents of a Logical Backup Device (SQL Server)](../../Topics/TopicNameContainA/View-the-Properties-and-Contents-of-a-Logical-Backup-Device--SQL-Server-.md)  
  
-   [Restore a Backup from a Device (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Backup-from-a-Device--SQL-Server-.md)  
  
-   [Tutorial: Getting Started with SQL Server Backup and Restore to Windows Azure Blob Storage Service](assetId:///9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4)  
  
 **To create a backup**  
  
> [!NOTE]  
>  For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)][BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1) statement with the PARTIAL or COPY_ONLY option, respectively.  
  
-   [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
-   [Back Up a Transaction Log (SQL Server)](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)  
  
-   [Back Up Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-Files-and-Filegroups--SQL-Server-.md)  
  
-   [Create a Differential Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Differential-Database-Backup--SQL-Server-.md)  
  
-   [Back Up the Transaction Log When the Database Is Damaged (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-the-Transaction-Log-When-the-Database-Is-Damaged--SQL-Server-.md)  
  
-   [Enable or Disable Backup Checksums During Backup or Restore (SQL Server)](../../Topics/TopicNameNotContainA/Enable-or-Disable-Backup-Checksums-During-Backup-or-Restore--SQL-Server-.md)  
  
-   [Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)](../../Topics/TopicNameContainA/Specify-Whether-a-Backup-or-Restore-Operation-Continues-or-Stops-After-Encountering-an-Error--SQL-Server-.md)  
  
-   [Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)](../../Topics/TopicNameNotContainA/Use-Resource-Governor-to-Limit-CPU-Usage-by-Backup-Compression--Transact-SQL-.md)  
  
-   [Tutorial: Getting Started with SQL Server Backup and Restore to Windows Azure Blob Storage Service](assetId:///9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4)  
  
## See Also  
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)   
 [Maintenance Plans](../../Topics/TopicNameNotContainA/Maintenance-Plans.md)   
 [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md)   
 [Recovery Models (SQL Server)](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)