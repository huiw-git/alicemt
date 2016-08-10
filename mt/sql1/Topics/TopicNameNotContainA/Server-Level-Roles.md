---
title: "Server-Level Roles"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7adf2ad7-015d-4cbe-9e29-abaefd779008
caps.latest.revision: 51
caps.handback.revision: 0
manager: jhubbard
---
# Server-Level Roles
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides server-level roles to help you manage the permissions on a server. These roles are security principals that group other principals. Server-level roles are server-wide in their permissions scope. (*Roles* are like *groups* in the Windows operating system.)  
  
 Fixed server roles are provided for convenience and backward compatibility. Assign more specific permissions whenever possible.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides nine fixed server roles. The permissions that are granted to the fixed server roles cannot be changed. Beginning with [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], you can create user-defined server roles and add server-level permissions to the user-defined server roles.  
  
 You can add server-level principals ([!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins, Windows accounts, and Windows groups) into server-level roles. Each member of a fixed server role can add other logins to that same role. Members of user-defined server roles cannot add other server principals to the role.  
  
## Fixed Server-Level Roles  
 The following table shows the fixed server-level roles and their capabilities.  
  
|Fixed server-level role|Description|  
|------------------------------|-----------------|  
|sysadmin|Members of the sysadmin fixed server role can perform any activity in the server.|  
|serveradmin|Members of the serveradmin fixed server role can change server-wide configuration options and shut down the server.|  
|securityadmin|Members of the securityadmin fixed server role manage logins and their properties. They can GRANT, DENY, and REVOKE server-level permissions. They can also GRANT, DENY, and REVOKE database-level permissions if they have access to a database. Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins.<br /><br /> **\*\* Security Note \*\*** The ability to grant access to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and to configure user permissions allows the security admin to assign most server permissions. The **securityadmin** role should be treated as equivalent to the **sysadmin** role.|  
|processadmin|Members of the processadmin fixed server role can end processes that are running in an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|  
|setupadmin|Members of the setupadmin fixed server role can add and remove linked servers by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements. (sysadmin membership is needed when using [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].)|  
|bulkadmin|Members of the bulkadmin fixed server role can run the BULK INSERT statement.|  
|diskadmin|The diskadmin fixed server role is used for managing disk files.|  
|dbcreator|Members of the dbcreator fixed server role can create, alter, drop, and restore any database.|  
|public|Every [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login belongs to the public server role. When a server principal has not been granted or denied specific permissions on a securable object, the user inherits the permissions granted to public on that object. Only assign public permissions on any object when you want the object to be available to all users. You cannot change membership in public.<br /><br /> Note: public is implemented differently than other roles. However, permissions can be granted, denied, or revoked from public.|  
  
## Permissions of Fixed Server Roles  
 Each fixed server role has certain permissions assigned to it. For a chart of the permissions assigned to the server roles, see [Database Engine Fixed Server and Fixed Database Roles](http://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).  
  
> [!IMPORTANT]  
>  The **CONTROL SERVER** permission is similar but not identical to the **sysadmin** fixed server role. Permissions do not imply role memberships and role memberships do not grant permissions. (E.g. **CONTROL SERVER** does not imply membership in the **sysadmin** fixed server role.) However, it is sometimes possible to impersonate between roles and equivalent permissions. Most **DBCC** commands and many system procedures require membership in the **sysadmin** fixed server role. For a list of 171 system stored procedures that require **sysadmin** membership, see the following blog post by Andreas Wolter [CONTROL SERVER vs. sysadmin/sa: permissions, system procedures, DBCC, automatic schema creation and privilege escalation - caveats](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).  
  
## Server-Level Permissions  
 Only server-level permissions can be added to user-defined server roles. To list the server-level permissions, execute the following statement. The server-level permissions are:  
  
```tsql  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 For more information about permissions, see [Permissions (Database Engine)](../../Topics/TopicNameNotContainA/Permissions--Database-Engine-.md) and [sys.fn_builtin_permissions (Transact-SQL)](assetId:///704b1ad3-3534-4cf3-aff4-9fb70064b6cc).  
  
## Working with Server-Level Roles  
 The following table explains the commands, views, and functions that you can use to work with server-level roles.  
  
|Feature|Type|Description|  
|-------------|----------|-----------------|  
|[sp_helpsrvrole (Transact-SQL)](assetId:///5c7f39f3-c261-4f70-8beb-08242d4ac242)|Metadata|Returns a list of server-level roles.|  
|[sp_helpsrvrolemember (Transact-SQL)](assetId:///d0714913-8d6b-4de3-b042-3ae9934f839d)|Metadata|Returns information about the members of a server-level role.|  
|[sp_srvrolepermission (Transact-SQL)](assetId:///5709667f-e3e4-48a2-93ec-af5e22a2ac58)|Metadata|Displays the permissions of a server-level role.|  
|[IS_SRVROLEMEMBER (Transact-SQL)](assetId:///3241a44a-6958-415b-b8b7-2a1207c36ab3)|Metadata|Indicates whether a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login is a member of the specified server-level role.|  
|[sys.server_role_members (Transact-SQL)](assetId:///efa20414-2c6b-45a2-a7a9-60110a24da18)|Metadata|Returns one row for each member of each server-level role.|  
|[sp_addsrvrolemember (Transact-SQL)](assetId:///777f0e09-8ee5-4cb2-a3ac-939d02c3cd22)|Command|Adds a login as a member of a server-level role. Deprecated. Use [ALTER SERVER ROLE](assetId:///7a4db7bb-c442-4e12-9a8a-114da5bc7710) instead.|  
|[sp_dropsrvrolemember (Transact-SQL)](assetId:///7be99181-d221-49d0-9cb2-c930d8c044a0)|Command|Removes a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login or a Windows user or group from a server-level role. Deprecated. Use [ALTER SERVER ROLE](assetId:///7a4db7bb-c442-4e12-9a8a-114da5bc7710) instead.|  
|[CREATE SERVER ROLE (Transact-SQL)](assetId:///30c92f80-f7f6-4a84-ae89-16e69add0de6)|Command|Creates a user-defined server role.|  
|[ALTER SERVER ROLE (Transact-SQL)](assetId:///7a4db7bb-c442-4e12-9a8a-114da5bc7710)|Command|Changes the membership of a server role or changes name of a user-defined server role.|  
|[DROP SERVER ROLE (Transact-SQL)](assetId:///a2a1e6e6-e40c-4d6a-81be-d197b80bf226)|Command|Removes a user-defined server role.|  
|[IS_SRVROLEMEMBER (Transact-SQL)](assetId:///3241a44a-6958-415b-b8b7-2a1207c36ab3)|Function|Determines membership of server role.|  
  
## See Also  
 [Database-Level Roles](../../Topics/TopicNameNotContainA/Database-Level-Roles.md)   
 [Security Catalog Views (Transact-SQL)](assetId:///4d5cf1bf-09a7-4ee0-9dbb-5c584750fc67)   
 [Security Functions (Transact-SQL)](assetId:///7773a87d-2f1b-4951-a225-baf159a7291b)   
 [Securing SQL Server](../../Topics/TopicNameNotContainA/Securing-SQL-Server.md)   
 [GRANT Server Principal Permissions (Transact-SQL)](assetId:///4cbed281-5e1e-4d8b-b410-4c18a6cd0205)   
 [REVOKE Server Principal Permissions (Transact-SQL)](assetId:///75409024-f150-4326-af16-9d60e900df18)   
 [DENY Server Principal Permissions (Transact-SQL)](assetId:///859affa7-0567-47d1-9490-57c1abbd619b)   
 [Create a Server Role](../../Topics/TopicNameContainA/Create-a-Server-Role.md)