---
title: model Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
---
# model Database
  The **model** database is used as the template for all databases created on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Because **tempdb** is created every time [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started, the **model** database must always exist on a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system. The entire contents of the **model** database, including database options, are copied to the new database. Some of the settings of **model** are also used for creating a new **tempdb** during start up, so the **model** database must always exist on a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system.  
  
 Newly created user databases use the same [recovery model](../Topic/Recovery%20Models%20\(SQL%20Server\).md) as the model database. The default is user configurable. To learn the current recovery model of the model, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md).  
  
> [!IMPORTANT]  
>  If you modify the **model** database with user\-specific template information, we recommend that you back up **model**. For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md).  
  
## model Usage  
 When a CREATE DATABASE statement is issued, the first part of the database is created by copying in the contents of the **model** database. The rest of the new database is then filled with empty pages.  
  
 If you modify the **model** database, all databases created afterward will inherit those changes. For example, you could set permissions or database options, or add objects such as tables, functions, or stored procedures. File properties of the **model** database are an exception, and are ignored except the initial size of the data file. The default initial size of the model database data and log file is 8 MB.  
  
## Physical Properties of model  
 The following table lists initial configuration values of the **model** data and log files.  
  
|File|Logical name|Physical name|File growth|  
|----------|------------------|-------------------|-----------------|  
|Primary data|modeldev|model.mdf|Autogrow by 64 MB until the disk is full.|  
|Log|modellog|modellog.ldf|Autogrow by 64 MB to a maximum of 2 terabytes.|  
  
 For versions before [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], see [model Database](https://msdn.microsoft.com/library/ms186388\(v=sql.120\).aspx)for default file growth values.  
  
 To move the **model** database or log files, see [Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md).  
  
### Database Options  
 The following table lists the default value for each database option in the **model** database and whether the option can be modified. To view the current settings for these options, use the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view.  
  
|Database option|Default value|Can be modified|  
|---------------------|-------------------|---------------------|  
|ALLOW\_SNAPSHOT\_ISOLATION|OFF|Yes|  
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
|DB\_CHAINING|OFF|No|  
|ENCRYPTION|OFF|No|  
|MIXED\_PAGE\_ALLOCATION|ON|No|  
|NUMERIC\_ROUNDABORT|OFF|Yes|  
|PAGE\_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Yes|  
|QUOTED\_IDENTIFIER|OFF|Yes|  
|READ\_COMMITTED\_SNAPSHOT|OFF|Yes|  
|RECOVERY|Depends on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition\*|Yes|  
|RECURSIVE\_TRIGGERS|OFF|Yes|  
|Service Broker Options|DISABLE\_BROKER|No|  
|TRUSTWORTHY|OFF|No|  
  
 \*To verify the current recovery model of the database, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md) or [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md).  
  
 For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
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
  
-   Setting the primary filegroup to READ\_ONLY.  
  
-   Creating procedures, views, or triggers using the WITH ENCRYPTION option. The encryption key is tied to the database in which the object is created. Encrypted objects created in the **model** database can only be used in **model**.  
  
## Related Content  
 [System Databases](../../Topics\TopicNameNotContainA/System-Databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
 [Move Database Files](../../Topics\TopicNameNotContainA/Move-Database-Files.md)  
  
  