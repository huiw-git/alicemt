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
  The **msdb** database is used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent for scheduling alerts and jobs and by other features such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] and Database Mail.  
  
 For example, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] automatically maintains a complete online backup\-and\-restore history within tables in **msdb**. This information includes the name of the party that performed the backup, the time of the backup, and the devices or files where the backup is stored. [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] uses this information to propose a plan for restoring a database and applying any transaction log backups. Backup events for all databases are recorded even if they were created with custom applications or third\-party tools. For example, if you use a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] application that calls SQL Server Management Objects \(SMO\) objects to perform backup operations, the event is logged in the **msdb** system tables, the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows application log, and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log. To help your protect the information that is stored in **msdb**, we recommend that you consider placing the **msdb** transaction log on fault tolerant storage.  
  
 By default, **msdb** uses the simple recovery model. If you use the [backup and restore history](../Topic/Backup%20History%20and%20Header%20Information%20\(SQL%20Server\).md) tables, we recommend that you use the full recovery model for **msdb**. For more information, see [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md). Notice that when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed or upgraded and whenever Setup.exe is used to rebuild the system databases, the recovery model of **msdb** is automatically set to simple.  
  
> [!IMPORTANT]  
>  After any operation that updates **msdb**, such as backing up or restoring any database, we recommend that you back up **msdb**. For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md).  
  
## Physical Properties of msdb  
 The following table lists the initial configuration values of the **msdb** data and log files. The sizes of these files may vary slightly for different editions of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
|File|Logical name|Physical name|File growth|  
|----------|------------------|-------------------|-----------------|  
|Primary data|MSDBData|MSDBData.mdf|Autogrow by 256 KB until the disk is full.|  
|Log|MSDBLog|MSDBLog.ldf|Autogrow by 256 KB to a maximum of 2 terabytes.|  
  
 To move the **msdb** database or log files, see [Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md).  
  
### Database Options  
 The following table lists the default value for each database option in the **msdb** database and whether the option can be modified. To view the current settings for these options, use the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view.  
  
|Database option|Default value|Can be modified|  
|---------------------|-------------------|---------------------|  
|ALLOW\_SNAPSHOT\_ISOLATION|ON|No|  
|ANSI\_NULL\_DEFAULT|OFF|Yes|  
|ANSI\_NULLS|OFF|Yes|  
|ANSI\_PADDING|OFF|Yes|  
|ANSI\_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO\_CLOSE|OFF|Yes|  
|AUTO\_CREATE\_STATISTICS|ON|Yes|  
|AUTO\_SHRINK|OFF|Yes|  
|AUTO\_UPDATE\_STATISTICS|ON|Yes|  
|AUTO\_UPDATE\_STATISTICS\_ASYNC|OFF|Yes|  
|CHANGE\_TRACKING|OFF|No|  
|CONCAT\_NULL\_YIELDS\_NULL|OFF|Yes|  
|CURSOR\_CLOSE\_ON\_COMMIT|OFF|Yes|  
|CURSOR\_DEFAULT|GLOBAL|Yes|  
|Database Availability Options|ONLINE<br /><br /> MULTI\_USER<br /><br /> READ\_WRITE|No<br /><br /> Yes<br /><br /> Yes|  
|DATE\_CORRELATION\_OPTIMIZATION|OFF|Yes|  
|DB\_CHAINING|ON|Yes|  
|ENCRYPTION|OFF|No|  
|MIXED\_PAGE\_ALLOCATION|ON|No|  
|NUMERIC\_ROUNDABORT|OFF|Yes|  
|PAGE\_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Yes|  
|QUOTED\_IDENTIFIER|OFF|Yes|  
|READ\_COMMITTED\_SNAPSHOT|OFF|No|  
|RECOVERY|SIMPLE|Yes|  
|RECURSIVE\_TRIGGERS|OFF|Yes|  
|Service Broker Options|ENABLE\_BROKER|Yes|  
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
  
-   Setting the primary filegroup to READ\_ONLY.  
  
## Related Content  
 [System Databases](../../Topics\TopicNameNotContainA/System-Databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
 [Move Database Files](../../Topics\TopicNameNotContainA/Move-Database-Files.md)  
  
 [Database Mail](../../Topics\TopicNameNotContainA/Database-Mail.md)  
  
 [SQL Server Service Broker](../../Topics\TopicNameNotContainA/SQL-Server-Service-Broker.md)  
  
  