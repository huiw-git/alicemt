---
title: Restoring From Backups Stored in Microsoft Azure
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
---
# Restoring From Backups Stored in Microsoft Azure
  This topic outlines the considerations when restoring a database using a backup stored in the Windows Azure Blob storage service. This applies to backups created either by using SQL Server Backup to URL backup or by [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)].  
  
 We recommend reviewing this topic if you have backups stored in the Windows Azure Blob storage service that you plan to restore, and then review the topics that describe the steps on how to restore a database which is the same for both on\-premises and azure backups.  
  
## Overview  
 The tools and methods that are used to restore a database from an on\-premises backup apply to restoring a database from a cloud backup.  The following sections describe these considerations and any differences you should know about when you use backups stored in the Windows Azure Blob storage service.  
  
### Using Transact\-SQL  
  
-   Since SQL Server must connect to an external source to retrieve the backup files, SQL Credential is used to authenticate to the storage account. Consequently, the RESTORE statement requires WITH CREDENTIAL option. For more information, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
-   If you are using the [!INCLUDE[ss_smartbackup](../../Token\Other/ss_smartbackup_md.md)] to manage your backups to the cloud, you can review all the available backups in the storage, by using the **smart\_admin.fn\_available\_backups** system function. This system function returns all the available backups for a database in a table. As the results are returned in a table, you can filter or sort the results. For more information, see [managed_backup.fn_available_backups &#40;Transact-SQL&#41;](../Topic/managed_backup.fn_available_backups%20\(Transact-SQL\).md).  
  
### Using SQL Server Management Studio  
  
-   The restore task is used to restore a database using the SQL Server Management Studio. The backup media page now includes the **URL** option to show backup files stored in the Windows Azure Blob storage service. You also must provide the SQL Credential that is used to authenticate to the storage account. The **Backup sets to restore** grid is then populated with the available backups in the Windows Azure Blob storage. For more information, see [Restoring from Windows Azure storage Using SQL Server Management Studio](../../Topics\TopicNameNotContainA/SQL-Server-Backup-to-URL.md).  
  
### Optimizing Restores  
 To reduce restore write time, Add **perform volume maintenance tasks** user right to the SQL Server user account. For more information, see [Database File Initialization](http://go.microsoft.com/fwlink/?LinkId=271622). If restore is still slow with instant file initialization turned on, look at the size of the log file on the instance where the database was backed up. If the log is very large in size \(multiple GBs\), it would be expected that restore would be slow. During restore the log file must be zeroed which takes a significant amount of time.  
  
 To reduce restore times it is recommended that you use compressed backups.  For backup sizes exceeding 25 GB, use [AzCopy utility](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) to download to the local drive and then perform the restore. For other backup best practices and recommendations, see [SQL Server Backup to URL Best Practices and Troubleshooting](../../Topics\TopicNameNotContainA/SQL-Server-Backup-to-URL-Best-Practices-and-Troubleshooting.md).  
  
 You can also turn on Trace Flag 3051 when doing the restore to generate a detailed log. This log file is placed in the log directory, and is named using the format: BackupToUrl\-\<instancename\>\-\<dbname\>\-action\-\<PID\>.log. The log file includes information about each round trip to Windows Azure Storage including timing that can be helpful in diagnosing the issue.  
  
### Topics on Performing Restore Operations  
  
-   [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
-   [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md)  
  
-   [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)  
  
-   [File Restores &#40;Full Recovery Model&#41;](../Topic/File%20Restores%20\(Full%20Recovery%20Model\).md)  
  
-   [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  