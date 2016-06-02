---
title: master Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
---
# master Database
  The **master** database records all the system\-level information for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system. This includes instance\-wide metadata such as logon accounts, endpoints, linked servers, and system configuration settings. In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], system objects are no longer stored in the **master** database; instead, they are stored in the [Resource database](../../Topics\TopicNameNotContainA/Resource-Database.md). Also, **master** is the database that records the existence of all other databases and the location of those database files and records the initialization information for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Therefore, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot start if the **master** database is unavailable.  
  
## Physical Properties of master  
 The following table lists the initial configuration values of the **master** data and log files. The sizes of these files may vary slightly for different editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|File|Logical name|Physical name|File growth|  
|----------|------------------|-------------------|-----------------|  
|Primary data|master|master.mdf|Autogrow by 10 percent until the disk is full.|  
|Log|mastlog|mastlog.ldf|Autogrow by 10 percent to a maximum of 2 terabytes.|  
  
 For information about how to move the **master** data and log files, see [Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md).  
  
### Database Options  
 The following table lists the default value for each database option in the **master** database and whether the option can be modified. To view the current settings for these options, use the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view.  
  
|Database option|Default value|Can be modified|  
|---------------------|-------------------|---------------------|  
|ALLOW\_SNAPSHOT\_ISOLATION|ON|No|  
|ANSI\_NULL\_DEFAULT|OFF|Yes|  
|ANSI\_NULLS|OFF|Yes|  
|ANSI\_PADDING|OFF|Yes|  
|ANSI\_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO\_CLOSE|OFF|No|  
|AUTO\_CREATE\_STATISTICS|ON|Yes|  
|AUTO\_SHRINK|OFF|No|  
|AUTO\_UPDATE\_STATISTICS|ON|Yes|  
|AUTO\_UPDATE\_STATISTICS\_ASYNC|OFF|Yes|  
|CHANGE\_TRACKING|OFF|No|  
|CONCAT\_NULL\_YIELDS\_NULL|OFF|Yes|  
|CURSOR\_CLOSE\_ON\_COMMIT|OFF|Yes|  
|CURSOR\_DEFAULT|GLOBAL|Yes|  
|Database Availability Options|ONLINE<br /><br /> MULTI\_USER<br /><br /> READ\_WRITE|No<br /><br /> No<br /><br /> No|  
|DATE\_CORRELATION\_OPTIMIZATION|OFF|Yes|  
|DB\_CHAINING|ON|No|  
|ENCRYPTION|OFF|No|  
|MIXED\_PAGE\_ALLOCATION|ON|No|  
|NUMERIC\_ROUNDABORT|OFF|Yes|  
|PAGE\_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|Yes|  
|QUOTED\_IDENTIFIER|OFF|Yes|  
|READ\_COMMITTED\_SNAPSHOT|OFF|No|  
|RECOVERY|SIMPLE|Yes|  
|RECURSIVE\_TRIGGERS|OFF|Yes|  
|Service Broker Options|DISABLE\_BROKER|No|  
|TRUSTWORTHY|OFF|Yes|  
  
 For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
## Restrictions  
 The following operations cannot be performed on the **master** database:  
  
-   Adding files or filegroups.  
  
-   Changing collation. The default collation is the server collation.  
  
-   Changing the database owner. **master** is owned by **sa**.  
  
-   Creating a full\-text catalog or full\-text index.  
  
-   Creating triggers on system tables in the database.  
  
-   Dropping the database.  
  
-   Dropping the **guest** user from the database.  
  
-   Enabling change data capture.  
  
-   Participating in database mirroring.  
  
-   Removing the primary filegroup, primary data file, or log file.  
  
-   Renaming the database or primary filegroup.  
  
-   Setting the database to OFFLINE.  
  
-   Setting the database or primary filegroup to READ\_ONLY.  
  
## Recommendations  
 When you work with the **master** database, consider the following recommendations:  
  
-   Always have a current backup of the **master** database available.  
  
-   Back up the **master** database as soon as possible after the following operations:  
  
    -   Creating, modifying, or dropping any database  
  
    -   Changing server or database configuration values  
  
    -   Modifying or adding logon accounts  
  
-   Do not create user objects in **master**. If you do, **master** must be backed up more frequently.  
  
-   Do not set the TRUSTWORTHY option to ON for the **master** database.  
  
## What to Do If master Becomes Unusable  
 If **master** becomes unusable, you can return the database to a usable state in either of the following ways:  
  
-   Restore **master** from a current database backup.  
  
     If you can start the server instance, you should be able to restore **master** from a full database backup. For more information, see [Restore the master Database &#40;Transact-SQL&#41;](../Topic/Restore%20the%20master%20Database%20\(Transact-SQL\).md).  
  
-   Rebuild **master** completely.  
  
     If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you must rebuild **master**. For more information, see [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md).  
  
    > [!IMPORTANT]  
    >  Rebuilding **master** rebuilds all of the system databases.  
  
## Related Content  
 [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md)  
  
 [System Databases](../../Topics\TopicNameNotContainA/System-Databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
 [Move Database Files](../../Topics\TopicNameNotContainA/Move-Database-Files.md)  
  
  