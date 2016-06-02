---
title: Copy Databases with Backup and Restore
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
---
# Copy Databases with Backup and Restore
  In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you can create a new database by restoring a backup of a user database created by using [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or a later version. However, backups of **master**, **model** and **msdb** that were created by using an earlier version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be restored by [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. Also, [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] backups cannot be restored by any earlier version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] uses a different default path than earlier versions. Therefore, to restore backups of a database created in the default location of earlier versions you must use the MOVE option. For information about the new default path see [File Locations for Default and Named Instances of SQL Server](../../Topics\TopicNameNotContainA/File-Locations-for-Default-and-Named-Instances-of-SQL-Server.md). For more information about moving database files, see "Moving the Database Files," later in this topic.  
  
## General Steps for Using Backup and Restore to Copy a Database  
 When you use backup and restore to copy a database to another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the source and destination computers can be any platform on which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] runs.  
  
 The general steps are:  
  
1.  Back up the source database, which can reside on an instance of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or later. The computer on which this instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is running is the *source computer*.  
  
2.  On the computer to which you want to copy the database \(the *destination computer*\), connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on which you plan to restore the database. If needed, on the destination server instance, create the same backup devices as used to the backup of the source databases.  
  
3.  Restore the backup of the source database on the destination computer. Restoring the database automatically creates all of the database files.  
  
 The following topics address additional considerations that may affect this process.  
  
## Before You Restore Database Files  
 Restoring a database automatically creates the database files that are needed by the restoring database. By default, the files that are created by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] during the restoration process use the same names and paths as the backup files from the original database on the source computer.  
  
 Optionally, when restoring the database, you can specify the device mapping, file names, or path for the restoring database. This might be necessary in the following situations:  
  
-   The directory structure or drive mapping used by the database on the original computer not exist on the other computer. For example, perhaps the backup contains a file that would be restored to drive E by default, but the destination computer lacks a drive E.  
  
-   The target location might have insufficient space.  
  
-   You are reusing a database name that exists on the restore destination and any of its files is named the same as a database file in the backup set, one of the following occurs:  
  
    -   If the existing database file can be overwritten, it will be overwritten \(this would not affect a file that belongs to a different database name\).  
  
    -   If the existing file cannot be overwritten, a restore error would occur.  
  
 To avoid errors and unintended consequences, before the restore operation, you can use the [backupfile](../Topic/backupfile%20\(Transact-SQL\).md) history table to find out the database and log files in the backup you plan to restore.  
  
## Moving the Database Files  
 If the files within the database backup cannot be restored onto the destination computer because of the reasons mentioned earlier, it is necessary to move the files to a new location while they are being restored. For example:  
  
-   You want to restore a database from backups created in the default location of the earlier version.  
  
-   It may be necessary to restore some of the database files in the backup to a different drive because of capacity considerations. This is likely to be a common occurrence because most computers within an organization do not have the same number and size of disk drives or identical software configurations.  
  
-   It may be necessary to create a copy of an existing database on the same computer for testing purposes. In this case, the database files for the original database already exist, so different file names need to be specified when the database copy is created during the restore operation.  
  
 For more information, see "To restore files and filegroups to a new location," later in this topic.  
  
## Changing the Database Name  
 The name of the database can be changed as it is restored to the destination computer, without having to restore the database first and then change the name manually. For example, it may be necessary to change the database name from **Sales** to **SalesCopy** to indicate that this is a copy of a database.  
  
 The database name that is explicitly supplied when you restore a database is used automatically as the new database name. Because the database name does not already exist, a new one is created by using the files in the backup.  
  
## When Upgrading a Database by Using Restore  
 When restoring backups from an earlier version, it is helpful to know in advance whether the path \(drive and directory\) of each of the full\-text catalogs in a backup exists on the destination computer. To list the logical names and physical names, path and file name\) of every file in a backup, including the catalog files, use a RESTORE FILELISTONLY FROM *\<backup\_device\>* statement. For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md).  
  
 If the same path does not exist on the destination computer, you have two alternatives:  
  
-   Create the equivalent drive\/directory mapping on the destination computer.  
  
-   Move the catalog files to a new location during the restore operation, by using the WITH MOVE clause in your RESTORE DATABASE statement. For more information, see [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md).  
  
 For information about alternative options for upgrading full\-text indexes, see [Upgrade Full-Text Search](../../Topics\TopicNameNotContainA/Upgrade-Full-Text-Search.md).  
  
## Database Ownership  
 When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login or [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows user who initiates the restore operation becomes the owner of the new database automatically. When the database is restored, the system administrator or the new database owner can change database ownership. To prevent unauthorized restoration of a database, use media or backup set passwords.  
  
## Managing Metadata When Restoring to Another Server Instance  
 When you restore a database onto another server instance, to provide a consistent experience to users and applications, you might have to re\-create some or all of the metadata for the database, such as logins and jobs, on the other server instance. For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md).  
  
 **To view the data and log files in a backup set**  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
 **To restore files and filegroups to a new location**  
  
-   [Restore Files to a New Location &#40;SQL Server&#41;](../Topic/Restore%20Files%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
 **To restore files and filegroups over existing files**  
  
-   [Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;](../Topic/Restore%20Files%20and%20Filegroups%20over%20Existing%20Files%20\(SQL%20Server\).md)  
  
 **To restore a database with a new name**  
  
-   [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
 **To restart an interrupted restore operation**  
  
-   [Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;](../Topic/Restart%20an%20Interrupted%20Restore%20Operation%20\(Transact-SQL\).md)  
  
 **To change the owner of a database**  
  
-   [sp_changedbowner &#40;Transact-SQL&#41;](../Topic/sp_changedbowner%20\(Transact-SQL\).md)  
  
 **To copy a database by using SQL Server Management Objects \(SMO\)**  
  
-   [ReadFileList](assetId:///M:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList(Microsoft.SqlServer.Management.Smo.Server))  
  
-   [RelocateFiles](assetId:///P:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles)  
  
-   [ReplaceDatabase](assetId:///P:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase)  
  
-   [Restore](assetId:///T:Microsoft.SqlServer.Management.Smo.Restore)  
  
## See Also  
 [Copy Databases to Other Servers](../../Topics\TopicNameNotContainA/Copy-Databases-to-Other-Servers.md)   
 [File Locations for Default and Named Instances of SQL Server](../../Topics\TopicNameNotContainA/File-Locations-for-Default-and-Named-Instances-of-SQL-Server.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  