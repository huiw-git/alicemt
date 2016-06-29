---
title: msdb Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5032cb2d-65a0-40dd-b569-4dcecdd58ceb
---
# msdb Database
  The **msdb** database is used by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent for scheduling alerts and jobs and by other features such as [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)], [!INCLUDE[ssSB](../../Topics/TopicNameContainA/includes/ssSB_md.md)] and Database Mail.  
  
 For example, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] automatically maintains a complete online backup-and-restore history within tables in **msdb**. This information includes the name of the party that performed the backup, the time of the backup, and the devices or files where the backup is stored. [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)] uses this information to propose a plan for restoring a database and applying any transaction log backups. Backup events for all databases are recorded even if they were created with custom applications or third-party tools. For example, if you use a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[vbprvb](../../Topics/TopicNameContainA/includes/vbprvb_md.md)] application that calls SQL Server Management Objects (SMO) objects to perform backup operations, the event is logged in the **msdb** system tables, the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows application log, and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] error log. To help your protect the information that is stored in **msdb**, we recommend that you consider placing the **msdb** transaction log on fault tolerant storage.  
  
 By default, **msdb** uses the simple recovery model. If you use the [backup and restore history](../../Topics/TopicNameNotContainA/Backup-History-and-Header-Information--SQL-Server-.md) tables, we recommend that you use the full recovery model for **msdb**. For more information, see [Recovery Models &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md). Notice that when [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] is installed or upgraded and whenever Setup.exe is used to rebuild the system databases, the recovery model of **msdb** is automatically set to simple.  
  
> [!IMPORTANT]  
>  After any operation that updates **msdb**, such as backing up or restoring any database, we recommend that you back up **msdb**. For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-System-Databases--SQL-Server-.md).  
  
## Physical Properties of msdb  
 The following table lists the initial configuration values of the **msdb** data and log files. The sizes of these files may vary slightly for different editions of [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)].  
  
|File|Logical name|Physical name|File growth|  
|----------|------------------|-------------------|-----------------|  
|Primary data|MSDBData|MSDBData.mdf|Autogrow by 256 KB until the disk is full.|  
|Log|MSDBLog|MSDBLog.ldf|Autogrow by 256 KB to a maximum of 2 terabytes.|  
  
 To move the **msdb** database or log files, see [Move System Databases](../../Topics/TopicNameNotContainA/Move-System-Databases.md).  
  
### Database Options  
 The following table lists the default value for each database option in the **msdb** database and whether the option can be modified. To view the current settings for these options, use the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view.  
  
|Database option|Default value|Can be modified|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|No|  
|ANSI_NULL_DEFAULT|OFF|Yes|  
|ANSI_NULLS|OFF|Yes|  
|ANSI_PADDING|OFF|Yes|  
|ANSI_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO_CLOSE|OFF|Yes|  
|AUTO_CREATE_STATISTICS|ON|Yes|  
|AUTO_SHRINK|OFF|Yes|  
|AUTO_UPDATE_STATISTICS|ON|Yes|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Yes|  
|CHANGE_TRACKING|OFF|No|  
|CONCAT_NULL_YIELDS_NULL|OFF|Yes|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Yes|  
|CURSOR_DEFAULT|GLOBAL|Yes|  
|Database Availability Options|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|No<br /><br /> Yes<br /><br /> Yes|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Yes|  
|DB_CHAINING|ON|Yes|  
|ENCRYPTION|OFF|No|  
|MIXED_PAGE_ALLOCATION|ON|No|  
|NUMERIC_ROUNDABORT|OFF|Yes|  
|PAGE_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Yes|  
|QUOTED_IDENTIFIER|OFF|Yes|  
|READ_COMMITTED_SNAPSHOT|OFF|No|  
|RECOVERY|SIMPLE|Yes|  
|RECURSIVE_TRIGGERS|OFF|Yes|  
|Service Broker Options|ENABLE_BROKER|Yes|  
|TRUSTWORTHY|ON|Yes|  
  
 For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
## Restrictions  
 The following operations cannot be performed on the **msdb** database:  
  
-   Changing collation. The default collation is the server collation.  
  
-   Dropping the database.  
  
-   Dropping the **guest** user from the database.  
  
-   Enabling change data capture.  
  
-   Participating in database mirroring.  
  
-   Removing the primary filegroup, primary data file, or log file.  
  
-   Renaming the database or primary filegroup.  
  
-   Setting the database to OFFLINE.  
  
-   Setting the primary filegroup to READ_ONLY.  
  
## Related Content  
 [System Databases](../../Topics/TopicNameNotContainA/System-Databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
 [Move Database Files](../../Topics/TopicNameNotContainA/Move-Database-Files.md)  
  
 [Database Mail](../../Topics/TopicNameNotContainA/Database-Mail.md)  
  
 [SQL Server Service Broker](../../Topics/TopicNameNotContainA/SQL-Server-Service-Broker.md)  
  
  