---
title: "Troubleshoot Orphaned Users (SQL Server)"
ms.custom: na
ms.date: 2016-04-05
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
caps.latest.revision: 41
manager: jhubbard
---
# Troubleshoot Orphaned Users (SQL Server)
Orphaned users in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] occur when a database user is based on  a login in the **master** database, but the login no longer exists in **master**. This can occur when the login is deleted, or when the database is moved to another server where the login does not exist. This topic describes how to find orphaned users, and remap them to logins.  
  
> [!NOTE]  
>  Reduce the possibility of orphaned users by using contained database users for databases that might be moved. For more information, see [Contained Database Users - Making Your Database Portable](../../Topics/TopicNameNotContainA/Contained-Database-Users---Making-Your-Database-Portable.md).  
  
## Background  
 To connect to a database on an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using a security principal (database user identity) based on a login, the principal must have a valid login in the **master** database. This login is used in the authentication process that verifies the principals identity and determines if the principal is allowed to connect to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins on a server instance are visible in the **sys.server_principals** catalog view and the **sys.syslogins** compatibility view.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins access individual databases  as "database user" that is mapped to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login. There are three exceptions to this rule:  
  
-   Contained database users  
  
     Contained database users authenticate at the user-database level and are not associated with logins. This is recommended because the databases are more portable and contained database users cannot become orphaned. However they must be recreated for each database. This might be impractical in an environment with many databases.  
  
-   The **guest** account.  
  
     When enabled in the database, this account permits [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins that are not mapped to a database user to enter the database as the **guest** user. The **guest** account is disabled by default.  
  
-   Microsoft Windows group memberships.  
  
     A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login created from a Windows user can enter a database if the Windows user is a member of a Windows group that is also a user in the database.  
  
 Information about the mapping of a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to a database user is stored within the database. It includes the name of the database user and the SID of the corresponding [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login. The permissions of this database user are applied for authorization in the database.  
  
 A database user (based on a login) for which the corresponding [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance. Such a user is said to be an *orphaned user* of the database on that server instance. Orphaning can happen if the database user is mapped to a login SID that is not present in the `master` instance. A database user can become orphaned after a database is restored or attached to a different instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] where the login was never created. A database user can also become orphaned if the corresponding [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login is dropped. Even if the login is recreated, it will have a different SID, so the database user will still be orphaned.  
  
## To Detect Orphaned Users  
 To detect orphaned users based on missing [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] authentication logins, execute the following statement in the user database:  
  
```  
SELECT dp.type_desc, dp.SID, dp.name AS user_name  
FROM sys.database_principals AS dp  
LEFT JOIN sys.server_principals AS sp  
    ON dp.SID = sp.SID  
WHERE sp.SID IS NULL  
    AND authentication_type_desc = 'INSTANCE';  
```  
  
 The output lists the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] authentication  users and corresponding security identifiers (SID) in the current database that are not linked to any [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login.  
  
## To Resolve an Orphaned User  
 Use the [CREATE LOGIN](assetId:///eb737149-7c92-4552-946b-91085d8b1b01) statement with the SID option to recreate a missing login, providing the `SID` of the database user obtained in the previous section:  
  
```  
CREATE LOGIN <login_name>   
WITH PASSWORD = '<use_a_strong_password_here>',  
SID = <SID>;  
```  
  
 To map an orphaned user to a login which already exists in **master**, execute the [ALTER USER](assetId:///344fc6ce-a008-47c8-a02e-47fae66cc590) statement, specifying the login name.  
  
```  
ALTER USER <user_name> WITH Login = <login_name>;  
```  
  
 When you recreate a missing login, the user can access the database using the password provided. Then the user can alter the password of the login account by using the ALTER LOGIN statement.  
  
```  
ALTER LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
> [!IMPORTANT]  
>  Any login can change it's own password. Only logins with the `ALTER ANY LOGIN` permission can change the password of another user's login. However, only members of the **sysadmin** role can modify passwords of **sysadmin** role members.  
  
 The deprecated procedure [sp_change_users_login](assetId:///1554b39f-274b-4ef8-898e-9e246b474333) also works with orphaned users. `sp_change_users_login` cannot be used with [!INCLUDE[ssSDS](../../Topics/TopicNameContainA/tokens/ssSDS_md.md)].  
  
## See Also  
 [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)   
 [ALTER USER (Transact-SQL)](assetId:///344fc6ce-a008-47c8-a02e-47fae66cc590)   
 [CREATE USER (Transact-SQL)](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80)   
 [sys.database_principals (Transact-SQL)](assetId:///8cb239e9-eb8c-4109-9cec-0d35de95fa0e)   
 [sys.server_principals (Transact-SQL)](assetId:///c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37)   
 [sp_change_users_login (Transact-SQL)](assetId:///1554b39f-274b-4ef8-898e-9e246b474333)   
 [sp_addlogin](assetId:///030f19c3-a5e3-4b53-bfc4-de4bfca0fddc)   
 [sp_grantlogin](assetId:///0c873d99-c3bf-4eb1-948b-a46cb235ccd4)   
 [sp_password (Transact-SQL)](assetId:///0ecbec81-e637-44a9-a61e-11bf060ef084)   
 [sys.sysusers (Transact-SQL)](assetId:///5f0e6a8d-c983-44f6-97e9-aab5bff67d18)   
 [sys.syslogins (Transact-SQL)](assetId:///4cb34f17-a4bb-469f-a218-71f074e6308f)