---
title: TRUSTWORTHY Database Property
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
---
# TRUSTWORTHY Database Property
  The TRUSTWORTHY database property is used to indicate whether the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] trusts the database and the contents within it. By default, this setting is OFF, but can be set to ON by using the ALTER DATABASE statement. For example, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  To set this option, you must be a member of the **sysadmin** fixed server role.  
  
 This property can be used to reduce certain threats that can exist as a result of attaching a database that contains one of the following objects:  
  
-   Malicious assemblies with an EXTERNAL\_ACCESS or UNSAFE permission setting. For more information, see [CLR Integration Security](../Topic/CLR%20Integration%20Security.md).  
  
-   Malicious modules that are defined to execute as high privileged users. For more information, see [EXECUTE AS Clause &#40;Transact-SQL&#41;](../Topic/EXECUTE%20AS%20Clause%20\(Transact-SQL\).md).  
  
 Both of these situations require a specific degree of privileges and are protected against by appropriate mechanisms when they are used in the context of a database that is already attached to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. However, if the database is taken offline, a user that has access to the database file can potentially attach it to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] of his or her choice and add malicious content to the database. When databases are detached and attached in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], certain permissions are set on the data and log files that restrict access to the database files.  
  
 Because a database that is attached to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be immediately trusted, the database is not allowed to access resources beyond the scope of the database until the database is explicitly marked trustworthy. Also, modules that are designed to access resources outside the database, and assemblies with either the EXTERNAL\_ACCESS and UNSAFE permission setting, have additional requirements in order to run successfully.  
  
## Related Content  
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)  
  
  