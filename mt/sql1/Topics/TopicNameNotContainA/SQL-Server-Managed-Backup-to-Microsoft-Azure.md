---
title: "SQL Server Managed Backup to Microsoft Azure"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afa01165-39e0-4efe-ac0e-664edb8599fd
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Managed Backup to Microsoft Azure
[!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] manages and automates SQL Server backups to Microsoft Azure Blob storage. You can choose to allow SQL Server to determine the backup schedule based on the transaction workload of your database. Or you can use advanced options to define a schedule. The retention settings determine how long the backups are stored in Azure Blob storage. [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] supports point in time restore for the retention time period specified.  
  
 Beginning with [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], the procedures and underlying behavior of [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] has changed. For more information, see [Migrate SQL Server 2014 Managed Backup Settings to SQL Server 2016](../../Topics/TopicNameNotContainA/Migrate-SQL-Server-2014-Managed-Backup-Settings-to-SQL-Server-2016.md).  
  
> [!TIP]  
>  [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] is recommended for SQL Server instances running on Microsoft Azure virtual machines.  
  
## Benefits  
 Currently automating backups for multiple databases requires developing a backup strategy, writing custom code, and scheduling backups. Using [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)], you can create a backup plan by specifying only the retention period and storage location. Although advanced settings are available, they are not required. [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] schedules, performs, and maintains the backups.  
  
 [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] can be configured at the database level or at the SQL Server instance level. When configuring at the instance level, any new databases are also backed up automatically. Settings at the database level can be used to override instance level defaults on an individual case.  
  
 You can also encrypt the backups for additional security, and you can set up a custom schedule to control when the backups are taken. For more details on the benefits of using Microsoft Azure Blob storage for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backups, see [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics/TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md)  
  
##  <a name="Prereqs"></a> Prerequisites  
 Microsoft Azure Storage is used by [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] to store the backup files. The following prerequisites are required:  
  
|Prerequisite|Description|  
|------------------|-----------------|  
|**Microsoft Azure Account**|You can get started with Azure with a [free trial](http://azure.microsoft.com/pricing/free-trial/) before exploring [purchase options](http://azure.microsoft.com/pricing/purchase-options/).|  
|**Azure Storage Account**|The backups are stored in Azure blob storage associated with an Azure storage account. For step-by-step instructions to create a storage account, see [About Azure Storage Accounts](http://azure.microsoft.com/en-us/documentation/articles/storage-create-storage-account/).|  
|**Blob Container**|Blobs are organized in containers. You specify the target container for the backup files. You can create a container in the [Azure Management Portal](https://manage.windowsazure.com/), or you use the **New-AzureStorageContainer**[Azure PowerShell](http://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) command.|  
|**Shared Access Signature (SAS)**|Access to the target container is controlled by a Shared Access Signature (SAS). For an overview of SAS, see [Shared Access Signatures, Part 1: Understanding the SAS Model](http://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/). You can create a SAS token in code or with the **New-AzureStorageContainerSASToken** PowerShell command. For a PowerShell script that simplifies this process, see [Simplifying creation of SQL Credentials with Shared Access Signature ( SAS ) tokens on Azure Storage with Powershell](http://blogs.msdn.com/b/sqlcat/archive/2015/03/21/simplifying-creation-sql-credentials-with-shared-access-signature-sas-keys-on-azure-storage-containers-with-powershell.aspx). The SAS token can be stored in a **SQL Credential** for use with [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].|  
|**SQL Server Agent**|SQL Server Agent must be running for [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] to work. Consider setting the startup option to automatic.|  
  
## Components  
 Transact-SQL is the main interface to interact with [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)]. System stored procedures are used for enabling, configuring, and monitoring [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)]. System functions are used to retrieve existing configuration settings, parameter values, and backup file information. Extended events are used to surface errors and warnings. Alert mechanisms are enabled through SQL Agent jobs and SQL Server Policy Based Management. The following is a list of the objects and a description of its functionality in relation to [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].  
  
 PowerShell cmdlets are also available to configure [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)]. SQL Server Management Studio supports restoring backups created by [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] by using the **Restore Database** task  
  
|||  
|-|-|  
|System Object|Description|  
|**MSDB**|Stores the metadata, backup history for all the backups created by [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].|  
|[managed_backup.sp_backup_config_basic (Transact-SQL)](assetId:///3ad73051-ae9a-4e41-a889-166146e5508f)|Enables [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].|  
|[managed_backup.sp_backup_config_advanced (Transact-SQL)](assetId:///4fae8193-1f88-48fd-a94a-4786efe8d6af)|Configures advanced settings for [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)], such as encryption.|  
|[managed_backup.sp_backup_config_schedule (Transact-SQL)](assetId:///82541160-d1df-4061-91a5-6868dd85743a)|Creates a custom schedule for [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].|  
|[smart_backup.sp_master_switch](assetId:///1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2)|Pauses and resumes [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)].|  
|[smart_admin.sp_set_backup_parameter](assetId:///bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f)|Enables and configures monitoring for [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)]. Examples: enabling extended events, mail settings for notifications.|  
|[smart_admin.sp_backup_on_demand](assetId:///638f809f-27fa-4c44-a549-9cf37ecc920c)|Performs an ad-hoc backup for a database that is enabled to use [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] without breaking the log chain.|  
|[smart_admin.fn_backup_db_config](assetId:///7c755d8a-64dd-44b2-be5e-735d30758900)|Returns the current [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] status and configuration values for a database, or for all the databases on the instance.|  
|[smart_admin.fn_is_master_switch_on](assetId:///e8c2108d-b104-46cb-9645-a15f46112c86)|Returns the status of the master switch.|  
|[smart_admin.sp_get_backup_diagnostics](assetId:///2266a233-6354-464b-91ec-824ca4eb9ceb)|Returns the events logged by Extended Events.|  
|[smart_admin.fn_get _parameter](assetId:///ed94e54d-4516-4806-a8ce-f013d3a04122)|Returns the current values for backup system settings such as monitoring and mail settings for alerts.|  
|[smart_admin.fn_available_backups](assetId:///7aa84474-16e5-49bd-a703-c8d1408ef107)|Retrieves available backups for a specified database or for all the databases in an instance.|  
|[Smart_admin.fn_get_current_xevent_settings](assetId:///95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a)|Returns the current extended event settings.|  
|[smart_admin.fn_get_health_status](assetId:///b376711d-444a-4b5e-b483-8df323b4e31f)|Returns the aggregated counts of errors logged by Extended Events for a specified period.|  
  
## Backup Strategy  
  
### Backup Scheduling  
 You can specify a custom backup schedule using the system stored procedure [managed_backup.sp_backup_config_schedule (Transact-SQL)](assetId:///82541160-d1df-4061-91a5-6868dd85743a). If you do not specify a custom schedule, the type of backups scheduled and the backup frequency is determined based on the workload of the database. The retention period settings are used to determine the length of time a backup file should be retained in the storage and the ability to recover the database to a point-in-time within the retention period.  
  
### Backup File Naming Conventions  
 [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] uses the container that you specify, so you have control over the name of the container. For the backup files, non availability databases are named using the following convention: The name is created using the first 40 characters of the database name, the database GUID without the ‘-‘, and the timestamp. The underscore character is inserted between segments as separators. The **.bak** file extension is used for full backup and **.log** for log backups. For Avaialbility Group databases, in addition to the file naming convention described above, the Availability Group database GUID is added after the 40 characters of the database name. The Availability Group database GUID value is the value for group_database_id in sys.databases.  
  
### Full Database Backup  
 [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] agent schedules a full database backup if any of the following is true.  
  
-   A database is [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] enabled for the first time, or when [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] is enabled with default settings at the instance level.  
  
-   The log growth since last full database backup is equal to or larger than 1 GB.  
  
-   The maximum time interval of one week has passed since the last full database backup.  
  
-   The log chain is broken. [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] periodically checks to see whether the log chain is intact by comparing the first and last LSNs of the backup files. If there is break in the log chain for any reason, [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] schedules a full database backup. The most common reason for log chain breaks is probably a backup command issued using Transact-SQL or through the Backup task in SQL Server Management Studio.  Other common scenarios include accidental deletion of the backup log files, or accidental overwrites of backups.  
  
### Transaction Log Backup  
 [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] schedules a log backup if any of the following is true:  
  
-   There is no log backup history that can be found. This is usually true when [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] is enabled for the first time.  
  
-   The transaction log space used is 5 MB or larger.  
  
-   The maximum time interval of 2 hours since the last log backup is reached.  
  
-   Any time the transaction log backup is lagging behind a full database backup. The goal is to keep the log chain ahead of full backup.  
  
## Retention Period Settings  
 When enabling backup you must set the retention period in days: The minimum is 1 day, and maximum is 30 days.  
  
 [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] based on the retention period settings, assesses the ability to recover to a point in time in the specified time, to determine what backup files to keep and identifying the backup files to delete. The backup_finish_date of the backup is used to determine and match the time specified by the retention period settings.  
  
## Important Considerations  
 For a database, if there is an existing full database backup job running, then [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] waits for the current job to be completed before doing another full database backup for the same database. Similarly, only one transaction log backup can be running at a given time. However, a full database backup and a transaction log backup can run concurrently. Failures are logged as Extended Events.  
  
 If more than 10 concurrent full database backups are scheduled, a warning is issued through the debug channel of Extended Events. [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] then maintains a priority queue for the remaining databases that require a backup until the all backups are scheduled and completed.  
  
##  <a name="support_limits"></a> Supportability  
 The following support limitations and considerations are specific to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]:  
  
-   System Databases are supported in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   For [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], all recovery models are supported (Full, Bulk-logged, and Simple).  
  
-   [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] agent only supports database full and log backups. File backup automation is not supported.  
  
-   Microsoft Azure Blob Storage service is the only supported backup storage option. Backups to disk or tape are not supported.  
  
-   [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] uses the Backup to Block Blob feature. The maximum size of a block blob is 200 GB. But by utilizing striping, the maximum size of an individual backup can be up to 12 TB. If your backup requirements exceed this, consider using compression, and test the backup file size prior to setting up [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)]. You can either test by backing up to a local disk or manually backing up to Microsoft Azure storage using **BACKUP TO URL** Transact-SQL statement. For more information, see [SQL Server Backup to URL](../../Topics/TopicNameNotContainA/SQL-Server-Backup-to-URL.md).  
  
-   [!INCLUDE[ss_smartbackup](../../Topics/TopicNameNotContainA/tokens/ss_smartbackup_md.md)] may have some limitations when it is configured with other technologies supporting backup, high availability, or disaster recovery.  
  
## See Also  
 [Enable SQL Server Managed Backup to Microsoft Azure](../../Topics/TopicNameNotContainA/Enable-SQL-Server-Managed-Backup-to-Microsoft-Azure.md)   
 [Configure Advanced Options for SQL Server Managed Backup to Microsoft Azure](../../Topics/TopicNameNotContainA/Configure-Advanced-Options-for-SQL-Server-Managed-Backup-to-Microsoft-Azure.md)   
 [Disable SQL Server Managed Backup to Microsoft Azure](../../Topics/TopicNameNotContainA/Disable-SQL-Server-Managed-Backup-to-Microsoft-Azure.md)