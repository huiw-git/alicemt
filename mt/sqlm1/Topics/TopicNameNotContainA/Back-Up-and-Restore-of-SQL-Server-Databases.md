---
title: Back Up and Restore of SQL Server Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
---
# Back Up and Restore of SQL Server Databases
  This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup and restore.  
  
 The SQL Server backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases. To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis. A well\-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures. Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.  
  
 In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Windows Azure Blob Storage Service. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md). For database files stored using the Microsoft Azure Blob storage service, [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] provides the option to use Azure snapshots for nearly instantaneous backups and faster restores. For more information, see [File-Snapshot Backups for Database Files in Azure](../../Topics\TopicNameNotContainA/File-Snapshot-Backups-for-Database-Files-in-Azure.md).  
  
##  Why back up?  
-   Backing up your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off\-site location protects you from potentially catastrophic data loss. **Backing up is the only way to proctect your data.**

     With valid backups of a database, you can recover your data from many failures, such as:  
  
    -   Media failure.  
  
    -   User errors, for example, dropping a table by mistake.  
  
    -   Hardware failures, for example, a damaged disk drive or permanent loss of a server.  
  
    -   Natural disasters. By using SQL Server Backup to Windows Azure Blob storage service, you can create an off\-site backup in a different region than your on\-premises location, to use in the event of a natural disaster affecting your on\-premises location.  
  
-   Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] or database mirroring, and archiving.  
  
##  Glossary of backup terms
 **back up** \[verb\]  
 Copies the data or log records from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.  
  
 **backup** \[noun\]  
 A copy of data that can be used to restore and recover the data after a failure. Backups of a database can also be used to restore a copy the database to a new location.  
  
**backup** device  
 A disk or tape device to which SQL Server backups are written and from which they can be restored. SQL Server backups can also be written to a Windows Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file.. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
**backup media**  
 One or more tapes or disk files to which one or more backup have been written.  
  
**data backup**  
 A backup of data in a complete database \(a database backup\), a partial database \( a partial backup\), or a set of data files or filegroups \(a file backup\).  
  
**database backup**  
 A backup of a database. Full database backups represent the whole database at the time the backup finished. Differential database backups contain only changes made to the database since its most recent full database backup.  
  
**differential backup**  
 A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups \(the differential base\) and that contains only the data that has changed since that base.  
  
**full backup**  
 A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.  
  
**log backup**  
 A backup of transaction logs that includes all log records that were not backed up in a previous log backup. \(full recovery model\)  
  
**recover**  
 To return a database to a stable and consistent state.  
  
**recovery**  
 A phase of database startup or of a restore with recovery that brings the database into a transaction\-consistent state.  
  
**recovery model**  
 A database property that controls transaction log maintenance on a database. Three recovery models exist: simple, full, and bulk\-logged. The recovery model of database determines its backup and restore requirements.  
  
**restore**  
 A multi\-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.  
  
 ##  Backup and restore strategies  
 Backing up and restoring data must be customized to a particular environment and must work with the available resources. Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy. A well\-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.  
  
#### Important! 
**Place the database and backups on separate devices. Otherwise, if the device containing the database fails, your backups will be unavailable. Placing the data and backups on separate devices also enhances the I\/O performance for both writing backups and the production use of the database.**  
  
 A backup and restore strategy contains a backup portion and a restore portion. The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored \(including security considerations\). The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss. We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.  
  
 Designing an effective backup and restore strategy requires careful planning, implementation, and testing. Testing is required. You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy. You must consider a variety of factors. These include the following:  
  
-   The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.  
  
-   The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.  
  
-   Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.  

### Impact of the recovery model on backup and restore  
 Backup and restore operations occur within the context of a recovery model. A recovery model is a database property that controls how the transaction log is managed. Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database. Typically a database uses either the simple recovery model or the full recovery model. The full recovery model can be supplemented by switching to the bulk\-logged recovery model before bulk operations. For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log (SQL Server)](https://msdn.microsoft.com/library/ms190925(SQL.130).aspx)  
  
 The best choice of recovery model for the database depends on your business requirements. To avoid transaction log management and simplify backup and restore, use the simple recovery model. To minimize work\-loss exposure, at the cost of administrative overhead, use the full recovery model. For information about the effect of recovery models on backup and restore, see [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md).  
  
### Design your backup strategy  
 After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy. The optimal backup strategy depends on a variety of factors, of which the following are especially significant:  
  
-   How many hours a day do applications have to access the database?  
  
     If there is a predictable off\-peak period, we recommend that you schedule full database backups for that period.  
  
-   How frequently are changes and updates likely to occur?  
  
     If changes are frequent, consider the following:  
  
    -   Under the simple recovery model, consider scheduling differential backups between full database backups. A differential backup captures only the changes since the last full database backup.  
  
    -   Under the full recovery model, you should schedule frequent log backups. Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.  
  
-   Are changes likely to occur in only a small part of the database or in a large part of the database?  
  
     For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful. For more information, see [Partial Backups &#40;SQL Server&#41;](../Topic/Partial%20Backups%20\(SQL%20Server\).md) and [Full File Backups &#40;SQL Server&#41;](../Topic/Full%20File%20Backups%20\(SQL%20Server\).md).  
  
-   How much disk space will a full database backup require?  
  
 ### Estimate the size of a full database backup  
 Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use. The backup operation copies the data in the database to the backup file. The backup contains only the actual data in the database and not any unused space. Therefore, the backup is usually smaller than the database itself. You can estimate the size of a full database backup by using the **sp\_spaceused** system stored procedure. For more information, see [sp_spaceused &#40;Transact-SQL&#41;](../Topic/sp_spaceused%20\(Transact-SQL\).md).  
  
### Schedule backups  
 Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations. You can perform a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup with minimal effect on production workloads.  
   
>  For information about concurrency restrictions during backup, see [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md).  
  
 After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database. For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md).  
  
### Test your backups!  
 You do not have a restore strategy until you have tested your backups. It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system. You must test restoring every type of backup that you intend to use.  
  
 We recommend that you maintain an operations manual for each database. This operations manual should document the location of the backups, backup device names \(if any\), and the amount of time that is required to restore the test backups.  
  
## More about backup tasks  
-   [Create a Maintenance Plan](../../Topics\TopicNameContainA/Create-a-Maintenance-Plan.md)  
  
-   [Create a Job](../Topic/Create%20a%20Job.md)  
  
-   [Schedule a Job](../Topic/Schedule%20a%20Job.md)  
  
## Working with backup devices and backup media  
-   [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md)  
  
-   [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Tape%20Drive%20\(SQL%20Server\).md)  
  
-   [Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;](../Topic/Specify%20a%20Disk%20or%20Tape%20As%20a%20Backup%20Destination%20\(SQL%20Server\).md)  
  
-   [Delete a Backup Device &#40;SQL Server&#41;](../Topic/Delete%20a%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Set the Expiration Date on a Backup &#40;SQL Server&#41;](../Topic/Set%20the%20Expiration%20Date%20on%20a%20Backup%20\(SQL%20Server\).md)  
  
-   [View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../Topic/View%20the%20Contents%20of%20a%20Backup%20Tape%20or%20File%20\(SQL%20Server\).md)  
  
-   [View the Data and Log Files in a Backup Set &#40;SQL Server&#41;](../Topic/View%20the%20Data%20and%20Log%20Files%20in%20a%20Backup%20Set%20\(SQL%20Server\).md)  
  
-   [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Restore a Backup from a Device &#40;SQL Server&#41;](../Topic/Restore%20a%20Backup%20from%20a%20Device%20\(SQL%20Server\).md)  
  
## Creating backups  
**Note!** For partial or copy\-only backups, you must use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)][BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement with the PARTIAL or COPY\_ONLY option, respectively.  
  
 ### Using SSMS   
-   [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
-   [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
 ### Using T-SQL  
-   [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md)  
  
-   [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../Topic/Back%20Up%20the%20Transaction%20Log%20When%20the%20Database%20Is%20Damaged%20\(SQL%20Server\).md)  
  
-   [Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;](../Topic/Enable%20or%20Disable%20Backup%20Checksums%20During%20Backup%20or%20Restore%20\(SQL%20Server\).md)  
  
-   [Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;](../Topic/Specify%20Whether%20a%20Backup%20or%20Restore%20Operation%20Continues%20or%20Stops%20After%20Encountering%20an%20Error%20\(SQL%20Server\).md)  
  
## Restore data backups 
### Using SSMS 
-   [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
-   [Restore a Database to a New Location &#40;SQL Server&#41;](../Topic/Restore%20a%20Database%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [Restore a Differential Database Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Restore Files and Filegroups &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
### Using T-SQL
-   [Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20Backup%20Under%20the%20Simple%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20to%20the%20Point%20of%20Failure%20Under%20the%20Full%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20over%20Existing%20Files%20\(SQL%20Server\).md)  
  
-   [Restore Files to a New Location &#40;SQL Server&#41;](../Topic/Restore%20Files%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [Restore the master Database &#40;Transact-SQL&#41;](../Topic/Restore%20the%20master%20Database%20\(Transact-SQL\).md)  

## Restore transaction logs \(Full Recovery Model\)
### Using SSMS  
-   [Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;](../Topic/Restore%20a%20Database%20to%20a%20Marked%20Transaction%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)  
  
-   [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md)  
  
 ### Using T-SQL 
-   [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md)  
 
-   [Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;](../Topic/Restart%20an%20Interrupted%20Restore%20Operation%20\(Transact-SQL\).md)  
  
-   [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../Topic/Recover%20a%20Database%20Without%20Restoring%20Data%20\(Transact-SQL\).md)  
 
## More information and resources
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)   
 [Back Up and Restore Full-Text Catalogs and Indexes](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Full-Text-Catalogs-and-Indexes.md)   
 [Back Up and Restore Replicated Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)   
 [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md)   
 [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
  
  