---
title: "Back Up and Restore of SQL Server Databases"
ms.custom: na
ms.date: 2016-05-27
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
caps.latest.revision: 91
caps.handback.revision: 0
manager: jhubbard
---
# Back Up and Restore of SQL Server Databases
This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup and restore.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases. To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis. A well-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures. Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.  
  
 In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Windows Azure Blob Storage Service. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics/TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md). For database files stored using the Microsoft Azure Blob storage service, [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] provides the option to use Azure snapshots for nearly instantaneous backups and faster restores. For more information, see [File-Snapshot Backups for Database Files in Azure](../../Topics/TopicNameNotContainA/File-Snapshot-Backups-for-Database-Files-in-Azure.md).  
  
 **In this Topic:**  
  
-   [Benefits](#Benefits)  
  
-   [Components and Concepts](#TermsAndDefinitions)  
  
-   [Introduction to Backup and Restore Strategies](#BnrStrategies)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Benefits"></a> Benefits  
  
-   Backing up your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off-site location protects you from potentially catastrophic data loss.  
  
    > [!IMPORTANT]  
    >  This is the only way to reliably protect your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] data.  
  
     With valid backups of a database, you can recover your data from many failures, such as:  
  
    -   Media failure.  
  
    -   User errors, for example, dropping a table by mistake.  
  
    -   Hardware failures, for example, a damaged disk drive or permanent loss of a server.  
  
    -   Natural disasters. By using SQL Server Backup to Windows Azure Blob storage service, you can create an off-site backup in a different region than your on-premises location, to use in the event of a natural disaster affecting your on-premises location.  
  
-   Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] or database mirroring, and archiving.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="TermsAndDefinitions"></a> Components and Concepts  
 back up [verb]  
 Copies the data or log records from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.  
  
 backup [noun]  
 A copy of data that can be used to restore and recover the data after a failure. Backups of a database can also be used to restore a copy the database to a new location.  
  
 backup device  
 A disk or tape device to which SQL Server backups are written and from which they can be restored. SQL Server backups can also be written to a Windows Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file.. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics/TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
 backup media  
 One or more tapes or disk files to which one or more backup have been written.  
  
 data backup  
 A backup of data in a complete database (a database backup), a partial database ( a partial backup), or a set of data files or filegroups (a file backup).  
  
 database backup  
 A backup of a database. Full database backups represent the whole database at the time the backup finished. Differential database backups contain only changes made to the database since its most recent full database backup.  
  
 differential backup  
 A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the differential base) and that contains only the data that has changed since that base.  
  
 full backup  
 A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.  
  
 log backup  
 A backup of transaction logs that includes all log records that were not backed up in a previous log backup. (full recovery model)  
  
 recover  
 To return a database to a stable and consistent state.  
  
 recovery  
 A phase of database startup or of a restore with recovery that brings the database into a transaction-consistent state.  
  
 recovery model  
 A database property that controls transaction log maintenance on a database. Three recovery models exist: simple, full, and bulk-logged. The recovery model of database determines its backup and restore requirements.  
  
 restore  
 A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="BnrStrategies"></a> Introduction to Backup and Restore Strategies  
 Backing up and restoring data must be customized to a particular environment and must work with the available resources. Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy. A well-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.  
  
> [!IMPORTANT]  
>  Place the database and backups on separate devices. Otherwise, if the device containing the database fails, your backups will be unavailable. Placing the data and backups on separate devices also enhances the I/O performance for both writing backups and the production use of the database.  
  
 A backup and restore strategy contains a backup portion and a restore portion. The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored (including security considerations). The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss. We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.  
  
 Designing an effective backup and restore strategy requires careful planning, implementation, and testing. Testing is required. You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy. You must consider a variety of factors. These include the following:  
  
-   The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.  
  
-   The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.  
  
-   Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.  
  
 [&#91;Top&#93;](#Top)  
  
### Impact of the Recovery Model on Backup and Restore  
 Backup and restore operations occur within the context of a recovery model. A recovery model is a database property that controls how the transaction log is managed. Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database. Typically a database uses either the simple recovery model or the full recovery model. The full recovery model can be supplemented by switching to the bulk-logged recovery model before bulk operations. For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md).  
  
 The best choice of recovery model for the database depends on your business requirements. To avoid transaction log management and simplify backup and restore, use the simple recovery model. To minimize work-loss exposure, at the cost of administrative overhead, use the full recovery model. For information about the effect of recovery models on backup and restore, see [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md).  
  
### Design the Backup Strategy  
 After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy. The optimal backup strategy depends on a variety of factors, of which the following are especially significant:  
  
-   How many hours a day do applications have to access the database?  
  
     If there is a predictable off-peak period, we recommend that you schedule full database backups for that period.  
  
-   How frequently are changes and updates likely to occur?  
  
     If changes are frequent, consider the following:  
  
    -   Under the simple recovery model, consider scheduling differential backups between full database backups. A differential backup captures only the changes since the last full database backup.  
  
    -   Under the full recovery model, you should schedule frequent log backups. Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.  
  
-   Are changes likely to occur in only a small part of the database or in a large part of the database?  
  
     For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful. For more information, see [Partial Backups (SQL Server)](../../Topics/TopicNameNotContainA/Partial-Backups--SQL-Server-.md) and [Full File Backups (SQL Server)](../../Topics/TopicNameNotContainA/Full-File-Backups--SQL-Server-.md).  
  
-   How much disk space will a full database backup require?  
  
     For more information, see [Estimating the Size of a Full Database Backup](#EstimateDbBuSize), later in this section.  
  
####  <a name="EstimateDbBuSize"></a> Estimate the Size of a Full Database Backup  
 Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use. The backup operation copies the data in the database to the backup file. The backup contains only the actual data in the database and not any unused space. Therefore, the backup is usually smaller than the database itself. You can estimate the size of a full database backup by using the **sp_spaceused** system stored procedure. For more information, see [sp_spaceused (Transact-SQL)](assetId:///c6253b48-29f5-4371-bfcd-3ef404060621).  
  
### Schedule Backups  
 Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations. You can perform a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup with minimal effect on production workloads.  
  
> [!NOTE]  
>  For information about concurrency restrictions during backup, see [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md).  
  
 After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database. For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../../Topics/TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md).  
  
### Test Your Backups  
 You do not have a restore strategy until you have tested your backups. It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system. You must test restoring every type of backup that you intend to use.  
  
 We recommend that you maintain an operations manual for each database. This operations manual should document the location of the backups, backup device names (if any), and the amount of time that is required to restore the test backups.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
### Scheduling Backup Jobs  
  
-   [Create a Maintenance Plan](../../Topics/TopicNameContainA/Create-a-Maintenance-Plan.md)  
  
-   [How to: Create a Job (SQL Server Management Studio)](assetId:///b35af2b6-6594-40d1-9861-4d5dd906048c)  
  
-   [How to: Schedule a Job (SQL Server Management Studio)](assetId:///f626390a-a3df-4970-b7a7-a0529e4a109c)  
  
### Working with Backup Devices and Backup Media  
  
-   [Define a Logical Backup Device for a Disk File (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Disk-File--SQL-Server-.md)  
  
-   [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md)  
  
-   [Specify a Disk or Tape As a Backup Destination (SQL Server)](../../Topics/TopicNameContainA/Specify-a-Disk-or-Tape-As-a-Backup-Destination--SQL-Server-.md)  
  
-   [Delete a Backup Device (SQL Server)](../../Topics/TopicNameContainA/Delete-a-Backup-Device--SQL-Server-.md)  
  
-   [Set the Expiration Date on a Backup (SQL Server)](../../Topics/TopicNameContainA/Set-the-Expiration-Date-on-a-Backup--SQL-Server-.md)  
  
-   [View the Contents of a Backup Tape or File (SQL Server)](../../Topics/TopicNameContainA/View-the-Contents-of-a-Backup-Tape-or-File--SQL-Server-.md)  
  
-   [View the Data and Log Files in a Backup Set (SQL Server)](../../Topics/TopicNameContainA/View-the-Data-and-Log-Files-in-a-Backup-Set--SQL-Server-.md)  
  
-   [View the Properties and Contents of a Logical Backup Device (SQL Server)](../../Topics/TopicNameContainA/View-the-Properties-and-Contents-of-a-Logical-Backup-Device--SQL-Server-.md)  
  
-   [Restore a Backup from a Device (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Backup-from-a-Device--SQL-Server-.md)  
  
### Creating Backups  
  
> [!NOTE]  
>  For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)][BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1) statement with the PARTIAL or COPY_ONLY option, respectively.  
  
 **Using SQL Server Management Studio**  
  
-   [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
-   [Back Up a Transaction Log (SQL Server)](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)  
  
-   [Back Up Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-Files-and-Filegroups--SQL-Server-.md)  
  
-   [Create a Differential Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Differential-Database-Backup--SQL-Server-.md)  
  
 **Using Transact-SQL**  
  
-   [Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)](../../Topics/TopicNameNotContainA/Use-Resource-Governor-to-Limit-CPU-Usage-by-Backup-Compression--Transact-SQL-.md)  
  
-   [Back Up the Transaction Log When the Database Is Damaged (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-the-Transaction-Log-When-the-Database-Is-Damaged--SQL-Server-.md)  
  
-   [Enable or Disable Backup Checksums During Backup or Restore (SQL Server)](../../Topics/TopicNameNotContainA/Enable-or-Disable-Backup-Checksums-During-Backup-or-Restore--SQL-Server-.md)  
  
-   [Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)](../../Topics/TopicNameContainA/Specify-Whether-a-Backup-or-Restore-Operation-Continues-or-Stops-After-Encountering-an-Error--SQL-Server-.md)  
  
 [&#91;Top&#93;](#Top)  
  
### Restoring Data Backups  
 **Using SQL Server Management Studio**  
  
-   [Restore a Database Backup Using SSMS](../../Topics/TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
-   [Restore a Database to a New Location (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Database-to-a-New-Location--SQL-Server-.md)  
  
-   [Restore a Differential Database Backup (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Differential-Database-Backup--SQL-Server-.md)  
  
-   [Restore Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups--SQL-Server-.md)  
  
 **Using Transact-SQL**  
  
-   [Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)](../../Topics/TopicNameContainA/Restore-a-Database-Backup-Under-the-Simple-Recovery-Model--Transact-SQL-.md)  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)](../../Topics/TopicNameContainA/Restore-a-Database-to-the-Point-of-Failure-Under-the-Full-Recovery-Model--Transact-SQL-.md)  
  
-   [Restore Files and Filegroups over Existing Files (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Files-and-Filegroups-over-Existing-Files--SQL-Server-.md)  
  
-   [Restore Files to a New Location (SQL Server)](../../Topics/TopicNameContainA/Restore-Files-to-a-New-Location--SQL-Server-.md)  
  
-   [Restore the master Database (Transact-SQL)](../../Topics/TopicNameNotContainA/Restore-the-master-Database--Transact-SQL-.md)  
  
 [&#91;Top&#93;](#Top)  
  
### Restoring Transaction Logs (Full Recovery Model)  
 **Using SQL Server Management Studio**  
  
-   [Restore a Database to a Marked Transaction (SQL Server Management Studio)](../../Topics/TopicNameContainA/Restore-a-Database-to-a-Marked-Transaction--SQL-Server-Management-Studio-.md)  
  
-   [Restore a Transaction Log Backup (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Transaction-Log-Backup--SQL-Server-.md)  
  
-   [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md)  
  
 **Using Transact-SQL**  
  
-   [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md)  
  
 [&#91;Top&#93;](#Top)  
  
### Additional Restore Tasks  
 **Using Transact-SQL**  
  
-   [Restart an Interrupted Restore Operation (Transact-SQL)](../../Topics/TopicNameNotContainA/Restart-an-Interrupted-Restore-Operation--Transact-SQL-.md)  
  
-   [Recover a Database Without Restoring Data (Transact-SQL)](../../Topics/TopicNameContainA/Recover-a-Database-Without-Restoring-Data--Transact-SQL-.md)  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Backup Overview (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Overview--SQL-Server-.md)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)   
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)   
 [Backup and Restore of Analysis Services Databases](../../Topics/TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)   
 [Back Up and Restore Full-Text Catalogs and Indexes](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Full-Text-Catalogs-and-Indexes.md)   
 [Back Up and Restore Replicated Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md)   
 [Recovery Models (SQL Server)](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)   
 [Media Sets, Media Families, and Backup Sets (SQL Server)](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)