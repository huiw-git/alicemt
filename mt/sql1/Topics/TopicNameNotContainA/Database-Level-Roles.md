---
title: Database-Level Roles
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f3fa5f6-6b50-43bb-9047-1544ade55e39
---
# Database-Level Roles
  To easily manage the permissions in your databases, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] provides several *roles* which are security principals that group other principals. They are like ***groups*** in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows operating system. Database-level roles are database-wide in their permissions scope.  
  
 There are two types of database-level roles in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]: *fixed database roles* that are predefined in the database and *flexible database roles* that you can create.  
  
 Fixed database roles are defined at the database level and exist in each database. Members of the **db_owner** database role can manage fixed database role membership. There are also some special-purpose fixed database roles in the msdb database.  
  
 You can add any database account and other [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] roles into database-level roles. Each member of a fixed database role can add other logins to that same role.  
  
> [!IMPORTANT]  
>  Do not add flexible database roles as members of fixed roles. This could enable unintended privilege escalation.  
  
 The following table shows the fixed database-level roles and their capabilities. These roles exist in all databases.  
  
|Database-level role name|Description|  
|-------------------------------|-----------------|  
|**db_owner**|Members of the **db_owner** fixed database role can perform all configuration and maintenance activities on the database, and can also drop the database.|  
|**db_securityadmin**|Members of the **db_securityadmin** fixed database role can modify role membership and manage permissions. Adding principals to this role could enable unintended privilege escalation.|  
|**db_accessadmin**|Members of the **db_accessadmin** fixed database role can add or remove access to the database for Windows logins, Windows groups, and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] logins.|  
|**db_backupoperator**|Members of the **db_backupoperator** fixed database role can back up the database.|  
|**db_ddladmin**|Members of the **db_ddladmin** fixed database role can run any Data Definition Language (DDL) command in a database.|  
|**db_datawriter**|Members of the **db_datawriter** fixed database role can add, delete, or change data in all user tables.|  
|**db_datareader**|Members of the **db_datareader** fixed database role can read all data from all user tables.|  
|**db_denydatawriter**|Members of the **db_denydatawriter** fixed database role cannot add, modify, or delete any data in the user tables within a database.|  
|**db_denydatareader**|Members of the **db_denydatareader** fixed database role cannot read any data in the user tables within a database.|  
  
## msdb Roles  
 The msdb database contains the special-purpose roles that are shown in the following table.  
  
|msdb role name|Description|  
|--------------------|-----------------|  
|**db_ssisadmin**<br /><br /> **db_ssisoperator**<br /><br /> **db_ssisltduser**|Members of these database roles can administer and use [!INCLUDE[ssIS](../../Topics/TopicNameContainA/includes/ssIS_md.md)]. Instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] that are upgraded from an earlier version might contain an older version of the role that was named using Data Transformation Services (DTS) instead of [!INCLUDE[ssIS](../../Topics/TopicNameContainA/includes/ssIS_md.md)]. For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../Topics/TopicNameNotContainA/Integration-Services-Roles--SSIS-Service-.md).|  
|**dc_admin**<br /><br /> **dc_operator**<br /><br /> **dc_proxy**|Members of these database roles can administer and use the data collector. For more information, see [Data Collection](../../Topics/TopicNameNotContainA/Data-Collection.md).|  
|**PolicyAdministratorRole**|Members of the **db_ PolicyAdministratorRole** database role can perform all configuration and maintenance activities on Policy-Based Management policies and conditions. For more information, see [Administer Servers by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md).|  
|**ServerGroupAdministratorRole**<br /><br /> **ServerGroupReaderRole**|Members of these database roles can administer and use registered server groups.|  
|**dbm_monitor**|Created in the **msdb** database when the first database is registered in Database Mirroring Monitor. The **dbm_monitor** role has no members until a system administrator assigns users to the role.|  
  
> [!IMPORTANT]  
>  Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin. This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] packages and [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent. To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] packages, configure [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.  
  
## Working with Database-Level Roles  
 The following table explains the commands, views and functions for working with database-level roles.  
  
|Feature|Type|Description|  
|-------------|----------|-----------------|  
|[sp_helpdbfixedrole &#40;Transact-SQL&#41;](../Topic/sp_helpdbfixedrole%20\(Transact-SQL\).md)|Metadata|Returns a list of the fixed database roles.|  
|[sp_dbfixedrolepermission &#40;Transact-SQL&#41;](../Topic/sp_dbfixedrolepermission%20\(Transact-SQL\).md)|Metadata|Displays the permissions of a fixed database role.|  
|[sp_helprole &#40;Transact-SQL&#41;](../Topic/sp_helprole%20\(Transact-SQL\).md)|Metadata|Returns information about the roles in the current database.|  
|[sp_helprolemember &#40;Transact-SQL&#41;](../Topic/sp_helprolemember%20\(Transact-SQL\).md)|Metadata|Returns information about the members of a role in the current database.|  
|[sys.database_role_members &#40;Transact-SQL&#41;](../Topic/sys.database_role_members%20\(Transact-SQL\).md)|Metadata|Returns one row for each member of each database role.|  
|[IS_MEMBER &#40;Transact-SQL&#41;](../Topic/IS_MEMBER%20\(Transact-SQL\).md)|Metadata|Indicates whether the current user is a member of the specified Microsoft Windows group or Microsoft SQL Server database role.|  
|[CREATE ROLE &#40;Transact-SQL&#41;](../Topic/CREATE%20ROLE%20\(Transact-SQL\).md)|Command|Creates a new database role in the current database.|  
|[ALTER ROLE &#40;Transact-SQL&#41;](../Topic/ALTER%20ROLE%20\(Transact-SQL\).md)|Command|Changes the name of a database role.|  
|[DROP ROLE &#40;Transact-SQL&#41;](../Topic/DROP%20ROLE%20\(Transact-SQL\).md)|Command|Removes a role from the database.|  
|[sp_addrole &#40;Transact-SQL&#41;](../Topic/sp_addrole%20\(Transact-SQL\).md)|Command|Creates a new database role in the current database.|  
|[sp_droprole &#40;Transact-SQL&#41;](../Topic/sp_droprole%20\(Transact-SQL\).md)|Command|Removes a database role from the current database.|  
|[sp_addrolemember &#40;Transact-SQL&#41;](../Topic/sp_addrolemember%20\(Transact-SQL\).md)|Command|Adds a database user, database role, Windows login, or Windows group to a database role in the current database.|  
|[sp_droprolemember &#40;Transact-SQL&#41;](../Topic/sp_droprolemember%20\(Transact-SQL\).md)|Command|Removes a security account from a SQL Server role in the current database.|  
  
## public Database Role  
 Every database user belongs to the **public** database role. When a user has not been granted or denied specific permissions on a securable object, the user inherits the permissions granted to **public** on that object.  
  
## Related Content  
 [Security Catalog Views &#40;Transact-SQL&#41;](../Topic/Security%20Catalog%20Views%20\(Transact-SQL\).md)  
  
 [Security Stored Procedures &#40;Transact-SQL&#41;](../Topic/Security%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
 [Security Functions &#40;Transact-SQL&#41;](../Topic/Security%20Functions%20\(Transact-SQL\).md)  
  
 [Securing SQL Server](../../Topics/TopicNameNotContainA/Securing-SQL-Server.md)  
  
 [sp_helprotect &#40;Transact-SQL&#41;](../Topic/sp_helprotect%20\(Transact-SQL\).md)  
  
  