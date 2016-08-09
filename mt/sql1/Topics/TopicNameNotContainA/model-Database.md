---
title: "model Database"
ms.custom: na
ms.date: 2016-03-04
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
caps.latest.revision: 53
caps.handback.revision: 0
manager: jhubbard
---
# model Database
The **model** database is used as the template for all databases created on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Because **tempdb** is created every time [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is started, the **model** database must always exist on a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] system. The entire contents of the **model** database, including database options, are copied to the new database. Some of the settings of **model** are also used for creating a new **tempdb** during start up, so the **model** database must always exist on a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] system.  
  
 Newly created user databases use the same [recovery model](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md) as the model database. The default is user configurable. To learn the current recovery model of the model, see [View or Change the Recovery Model of a Database (SQL Server)](../../Topics/TopicNameContainA/View-or-Change-the-Recovery-Model-of-a-Database--SQL-Server-.md).  
  
> [!IMPORTANT]  
>  If you modify the **model** database with user-specific template information, we recommend that you back up **model**. For more information, see [Back Up and Restore of System Databases (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-System-Databases--SQL-Server-.md).  
  
## model Usage  
 When a CREATE DATABASE statement is issued, the first part of the database is created by copying in the contents of the **model** database. The rest of the new database is then filled with empty pages.  
  
 If you modify the **model** database, all databases created afterward will inherit those changes. For example, you could set permissions or database options, or add objects such as tables, functions, or stored procedures. File properties of the **model** database are an exception, and are ignored except the initial size of the data file. The default initial size of the model database data and log file is 8 MB.  
  
## Physical Properties of model  
 The following table lists initial configuration values of the **model** data and log files.  
  
|File|Logical name|Physical name|File growth|  
|----------|------------------|-------------------|-----------------|  
|Primary data|modeldev|model.mdf|Autogrow by 64 MB until the disk is full.|  
|Log|modellog|modellog.ldf|Autogrow by 64 MB to a maximum of 2 terabytes.|  
  
 For versions before [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], see [model Database](https://msdn.microsoft.com/library/ms186388\(v=sql.120\).aspx)for default file growth values.  
  
 To move the **model** database or log files, see [Move System Databases](../../Topics/TopicNameNotContainA/Move-System-Databases.md).  
  
### Database Options  
 The following table lists the default value for each database option in the **model** database and whether the option can be modified. To view the current settings for these options, use the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view.  
  
|Database option|Default value|Can be modified|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Yes|  
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
|DB_CHAINING|OFF|No|  
|ENCRYPTION|OFF|No|  
|MIXED_PAGE_ALLOCATION|ON|No|  
|NUMERIC_ROUNDABORT|OFF|Yes|  
|PAGE_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Yes|  
|QUOTED_IDENTIFIER|OFF|Yes|  
|READ_COMMITTED_SNAPSHOT|OFF|Yes|  
|RECOVERY|Depends on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] edition*|Yes|  
|RECURSIVE_TRIGGERS|OFF|Yes|  
|Service Broker Options|DISABLE_BROKER|No|  
|TRUSTWORTHY|OFF|No|  
  
 *To verify the current recovery model of the database, see [View or Change the Recovery Model of a Database (SQL Server)](../../Topics/TopicNameContainA/View-or-Change-the-Recovery-Model-of-a-Database--SQL-Server-.md) or [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289).  
  
 For a description of these database options, see [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da).  
  
## Restrictions  
 The following operations cannot be performed on the **model** database:  
  
-   Adding files or filegroups.  
  
-   Changing collation. The default collation is the server collation.  
  
-   Changing the database owner. **model** is owned by **sa**.  
  
-   Dropping the database.  
  
-   Dropping the **guest** user from the database.  
  
-   Enabling change data capture.  
  
-   Participating in database mirroring.  
  
-   Removing the primary filegroup, primary data file, or log file.  
  
-   Renaming the database or primary filegroup.  
  
-   Setting the database to OFFLINE.  
  
-   Setting the primary filegroup to READ_ONLY.  
  
-   Creating procedures, views, or triggers using the WITH ENCRYPTION option. The encryption key is tied to the database in which the object is created. Encrypted objects created in the **model** database can only be used in **model**.  
  
## Related Content  
 [System Databases](../../Topics/TopicNameNotContainA/System-Databases.md)  
  
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)  
  
 [sys.master_files (Transact-SQL)](assetId:///803b22f2-0016-436b-a561-ce6f023d6b6a)  
  
 [Move Database Files](../../Topics/TopicNameNotContainA/Move-Database-Files.md)