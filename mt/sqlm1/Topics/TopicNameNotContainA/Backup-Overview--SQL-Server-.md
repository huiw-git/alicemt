---
title: Backup Overview (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
---
# Backup Overview (SQL Server)
  This topic introduces the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup component. Backing up your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database is essential for protecting your data. This discussion covers backup types, and backup restrictions. The topic also introduces [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup devices and backup media.  
  
 **In this Topic:**  
  
-   [Components and Concepts](#TermsAndDefinitions)  
  
-   [Backup Compression](#BackupCompression)  
  
-   [Restrictions on Backup Operations in SQL Server](#Restrictions)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="TermsAndDefinitions"></a> Components and Concepts  
 back up \[verb\]  
 Copies the data or log records from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.  
  
 backup \[noun\]  
 A copy of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data that can be used to restore and recover the data after a failure. A backup of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data is created at the level of a database or one or more of its files or filegroups. Table\-level backups cannot be created. In addition to data backups, the full recovery model requires creating backups of the transaction log.  
  
 [recovery model](../Topic/Recovery%20Models%20\(SQL%20Server\).md)  
 A database property that controls transaction log maintenance on a database. Three recovery models exist: simple, full, and bulk\-logged. The recovery model of database determines its backup and restore requirements.  
  
 [restore](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)  
 A multi\-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.  
  
 **Types of Backups**  
  
 [copy\-only backup](../Topic/Copy-Only%20Backups%20\(SQL%20Server\).md)  
 A special\-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backups.  
  
 data backup  
 A backup of data in a complete database \(a database backup\), a partial database \(a partial backup\), or a set of data files or filegroups \(a file backup\).  
  
 [database backup](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md)  
 A backup of a database. Full database backups represent the whole database at the time the backup finished. Differential database backups contain only changes made to the database since its most recent full database backup.  
  
 [differential backup](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md)  
 A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups \(the *differential base*\) and that contains only the data extents that have changed since the differential base.  
  
 A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.  
  
 full backup  
 A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.  
  
 [log backup](../Topic/Transaction%20Log%20Backups%20\(SQL%20Server\).md)  
 A backup of transaction logs that includes all log records that were not backed up in a previous log backup. \(full recovery model\)  
  
 [file backup](../Topic/Full%20File%20Backups%20\(SQL%20Server\).md)  
 A backup of one or more database files or filegroups.  
  
 [partial backup](../Topic/Partial%20Backups%20\(SQL%20Server\).md)  
 Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read\/write filegroup, and any optionally\-specified read\-only files.  
  
 **Backup Media Terms and Definitions**  
  
 [backup device](../Topic/Backup%20Devices%20\(SQL%20Server\).md)  
 A disk or tape device to which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backups are written and from which they can be restored. SQL Server backups can also be written to a Windows Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file.. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
 [backup media](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
 One or more tapes or disk files to which one or more backup have been written.  
  
 [backup set](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
 The backup content that is added to a media set by a successful backup operation.  
  
 [media family](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
 Backups created on a single nonmirrored device or a set of mirrored devices in a media set  
  
 [media set](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
 An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.  
  
 [mirrored media set](../Topic/Mirrored%20Backup%20Media%20Sets%20\(SQL%20Server\).md)  
 Multiple copies \(mirrors\) of a media set.  
  
##  <a name="BackupCompression"></a> Backup Compression  
 [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later versions can restore a compressed backup. For more information, see [Backup Compression &#40;SQL Server&#41;](../Topic/Backup%20Compression%20\(SQL%20Server\).md).  
  
##  <a name="Restrictions"></a> Restrictions on Backup Operations in SQL Server  
 Backup can occur while the database is online and being used. However, the following restrictions exist.  
  
### Offline Data Cannot Be Backed Up  
 Any backup operation that implicitly or explicitly references data that is offline fails. Some typical examples include the following:  
  
-   You request a full database backup, but one filegroup of the database is offline. Because all filegroups are implicitly included in a full database backup, this operation fails.  
  
     To back up this database, you can use a file backup and specify only the filegroups that are online.  
  
-   You request a partial backup, but a read\/write filegroup is offline. Because all read\/write filegroups are required for a partial backup, the operation fails.  
  
-   You request a file backup of specific files, but one of the files is not online. The operation fails. To back up the online files, you can omit the offline file from the file list and repeat the operation.  
  
 Typically, a log backup succeeds even if one or more data files are unavailable. However, if any file contains bulk\-logged changes made under the bulk\-logged recovery model, all the files must be online for the backup to succeed.  
  
### Concurrency Restrictions During Backup  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses an online backup process to allow for a database backup while the database is still being used. During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation. However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.  
  
 Operations that cannot run during a database backup or transaction log backup include the following:  
  
-   File\-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.  
  
-   Shrink database or shrink file operations. This includes auto\-shrink operations.  
  
-   If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.  
  
 If a backup operation overlaps with a file\-management operation or shrink operation, a conflict occurs. Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. \(The time\-out period is controlled by a session time\-out setting.\) If the lock is released during the time\-out period, the second operation continues. If the lock times out, the second operation fails.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To work with backup devices and backup media**  
  
-   [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md)  
  
-   [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Tape%20Drive%20\(SQL%20Server\).md)  
  
-   [Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;](../Topic/Specify%20a%20Disk%20or%20Tape%20As%20a%20Backup%20Destination%20\(SQL%20Server\).md)  
  
-   [Delete a Backup Device &#40;SQL Server&#41;](../Topic/Delete%20a%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Set the Expiration Date on a Backup &#40;SQL Server&#41;](../Topic/Set%20the%20Expiration%20Date%20on%20a%20Backup%20\(SQL%20Server\).md)  
  
-   [View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../Topic/View%20the%20Contents%20of%20a%20Backup%20Tape%20or%20File%20\(SQL%20Server\).md)  
  
-   [View the Data and Log Files in a Backup Set &#40;SQL Server&#41;](../Topic/View%20the%20Data%20and%20Log%20Files%20in%20a%20Backup%20Set%20\(SQL%20Server\).md)  
  
-   [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Restore a Backup from a Device &#40;SQL Server&#41;](../Topic/Restore%20a%20Backup%20from%20a%20Device%20\(SQL%20Server\).md)  
  
-   [Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service](../Topic/Tutorial:%20SQL%20Server%20Backup%20and%20Restore%20to%20Windows%20Azure%20Blob%20Storage%20Service.md)  
  
 **To create a backup**  
  
> [!NOTE]  
>  For partial or copy\-only backups, you must use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)][BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement with the PARTIAL or COPY\_ONLY option, respectively.  
  
-   [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
-   [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../Topic/Back%20Up%20the%20Transaction%20Log%20When%20the%20Database%20Is%20Damaged%20\(SQL%20Server\).md)  
  
-   [Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;](../Topic/Enable%20or%20Disable%20Backup%20Checksums%20During%20Backup%20or%20Restore%20\(SQL%20Server\).md)  
  
-   [Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;](../Topic/Specify%20Whether%20a%20Backup%20or%20Restore%20Operation%20Continues%20or%20Stops%20After%20Encountering%20an%20Error%20\(SQL%20Server\).md)  
  
-   [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md)  
  
-   [Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service](../Topic/Tutorial:%20SQL%20Server%20Backup%20and%20Restore%20to%20Windows%20Azure%20Blob%20Storage%20Service.md)  
  
## See Also  
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [Maintenance Plans](../../Topics\TopicNameNotContainA/Maintenance-Plans.md)   
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)   
 [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md)  
  
  