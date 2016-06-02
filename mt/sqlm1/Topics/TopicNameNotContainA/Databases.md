---
title: Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 316eea58-81b8-4bf3-a1fc-801946740e94
---
# Databases
  A database in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is made up of a collection of tables that stores a specific set of structured data. A table contains a collection of rows, also referred to as records or tuples, and columns, also referred to as attributes. Each column in the table is designed to store a certain type of information, for example, dates, names, dollar amounts, and numbers.  
  
## Basic Information about Databases  
 A computer can have one or more than one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installed. Each instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can contain one or many databases.  Within a database, there are one or many object ownership groups called schemas. Within each schema there are database objects such as tables, views, and stored procedures. Some objects such as certificates and asymmetric keys are contained within the database, but are not contained within a schema. For more information about creating tables, see [Tables](../../Topics\TopicNameNotContainA/Tables.md).  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases are stored in the file system in files. Files can be grouped into filegroups. For more information about files and filegroups, see [Database Files and Filegroups](../../Topics\TopicNameNotContainA/Database-Files-and-Filegroups.md).  
  
 When people gain access to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] they are identified as a login. When people gain access to a database they are identified as a database user. A database user can be based on a login. If contained databases are enabled, a database user can be created that is not based on a login. For more information about users, see [CREATE USER &#40;Transact-SQL&#41;](../Topic/CREATE%20USER%20\(Transact-SQL\).md).  
  
 A user that has access to a database can be given permission to access the objects in the database. Though permissions can be granted to individual users, we recommend creating database roles, adding the database users to the roles, and then grant access permission to the roles. Granting permissions to roles instead of users makes it easier to keep permissions consistent and understandable as the number of users grow and continually change. For more information about roles permissions, see [CREATE ROLE &#40;Transact-SQL&#41;](../Topic/CREATE%20ROLE%20\(Transact-SQL\).md) and [Principals &#40;Database Engine&#41;](../Topic/Principals%20\(Database%20Engine\).md).  
  
## Working with Databases  
 Most people who work with databases use the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] tool. The [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] tool has a graphical user interface for creating databases and the objects in the databases. [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] also has a query editor for interacting with databases by writing [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements. [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] can be installed from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation disk, or downloaded from MSDN.  
  
## In This Section  
  
|||  
|-|-|  
|[System Databases](../../Topics\TopicNameNotContainA/System-Databases.md)|[Delete Data or Log Files from a Database](../../Topics\TopicNameContainA/Delete-Data-or-Log-Files-from-a-Database.md)|  
|[Contained Databases](../../Topics\TopicNameNotContainA/Contained-Databases.md)|[Display Data and Log Space Information for a Database](../../Topics\TopicNameContainA/Display-Data-and-Log-Space-Information-for-a-Database.md)|  
|[SQL Server Data Files in Microsoft Azure](../../Topics\TopicNameNotContainA/SQL-Server-Data-Files-in-Microsoft-Azure.md)|[Increase the Size of a Database](../../Topics\TopicNameContainA/Increase-the-Size-of-a-Database.md)|  
|[Database Files and Filegroups](../../Topics\TopicNameNotContainA/Database-Files-and-Filegroups.md)|[Rename a Database](../../Topics\TopicNameContainA/Rename-a-Database.md)|  
|[Database States](../../Topics\TopicNameNotContainA/Database-States.md)|[Set a Database to Single-user Mode](../../Topics\TopicNameContainA/Set-a-Database-to-Single-user-Mode.md)|  
|[File States](../../Topics\TopicNameNotContainA/File-States.md)|[Shrink a Database](../../Topics\TopicNameContainA/Shrink-a-Database.md)|  
|[Estimate the Size of a Database](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Database.md)|[Shrink a File](../../Topics\TopicNameContainA/Shrink-a-File.md)|  
|[Copy Databases to Other Servers](../../Topics\TopicNameNotContainA/Copy-Databases-to-Other-Servers.md)|[View or Change the Properties of a Database](../../Topics\TopicNameContainA/View-or-Change-the-Properties-of-a-Database.md)|  
|[Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md)|[View a List of Databases on an Instance of SQL Server](../../Topics\TopicNameContainA/View-a-List-of-Databases-on-an-Instance-of-SQL-Server.md)|  
|[Add Data or Log Files to a Database](../../Topics\TopicNameContainA/Add-Data-or-Log-Files-to-a-Database.md)|[View or Change the Compatibility Level of a Database](../../Topics\TopicNameContainA/View-or-Change-the-Compatibility-Level-of-a-Database.md)|  
|[Change the Configuration Settings for a Database](../../Topics\TopicNameContainA/Change-the-Configuration-Settings-for-a-Database.md)|[Use the Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)|  
|[Create a Database](../../Topics\TopicNameContainA/Create-a-Database.md)|[Create a User-Defined Data Type Alias](../../Topics\TopicNameContainA/Create-a-User-Defined-Data-Type-Alias.md)|  
|[Delete a Database](../../Topics\TopicNameContainA/Delete-a-Database.md)|[Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)|  
  
## Related Content  
 [Indexes](../../Topics\TopicNameNotContainA/Indexes.md)  
  
 [Views](../../Topics\TopicNameNotContainA/Views.md)  
  
 [Stored Procedures &#40;Database Engine&#41;](../Topic/Stored%20Procedures%20\(Database%20Engine\).md)  
  
  