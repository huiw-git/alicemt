---
title: Getting Started with Database Engine Permissions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 051af34e-bb5b-403e-bd33-007dc02eef7b
---
# Getting Started with Database Engine Permissions
  Permissions in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] are managed at the server level through logins and server roles, and at the database level through database users and database roles. The model for [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] exposes  the same system within each database, but the server level permissions are not available. This topic reviews some basic security concepts and then describes a typical implementation of the permissions.  
  
## Security Principals  
 Security principal is the official name of the identities that use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and that can be assigned permission to take actions. They are usually people or groups of people, but can be  other entities that pretend to be people. The security principals can be created and managed using the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] listed, or by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 Logins  
 Logins are individual user accounts for logging on to the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] support logins based on Windows authentication and logins based on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication. For information about the two types of logins, see [Choose an Authentication Mode](../../Topics\TopicNameNotContainA/Choose-an-Authentication-Mode.md).  
  
 Fixed Server Roles  
 In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], fixed server roles are a set of pre\-configured roles that provide convenient group of server\-level permissions. Logins can be added to the roles using the `ALTER SERVER ROLE ... ADD MEMBER` statement. For more information, see [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20ROLE%20\(Transact-SQL\).md). [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] does not support the fixed server roles, but has two roles in the master database \(`dbmanager` and `loginmanager`\) that act like server roles.  
  
 User\-defined Server Roles  
 In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can create your own server roles and assign server\-level permissions to them. Logins can be added to the server roles using the `ALTER SERVER ROLE ... ADD MEMBER` statement. For more information, see [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20ROLE%20\(Transact-SQL\).md). [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] does not support the user\-defined server roles.  
  
 Database Users  
 Logins are granted access to a database by creating a database user in a database and mapping that database user to login. Typically the database user name is the same as the login name, though it does not have to be the same. Each database user maps to a single login. A login can be mapped to only one user in a database, but can be mapped as a database user in several different databases.  
  
 Database users can also be created that do not have a corresponding login. These are called *contained database users*. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] encourages the use of contained database users because it makes it easier to move your database to a different server. Like a login, a contained database user can use either Windows authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication. For more information, see [Contained Database Users - Making Your Database Portable](../../Topics\TopicNameNotContainA/Contained-Database-Users---Making-Your-Database-Portable.md).  
  
 There are 12 types of users with slight differences in how they authenticate, and who they represent. To see a list of users, see [CREATE USER &#40;Transact-SQL&#41;](../Topic/CREATE%20USER%20\(Transact-SQL\).md).  
  
 Fixed Database Roles  
 Fixed database roles are a set of pre\-configured roles that provide convenient group of database\-level permissions. Database users and user\-defined database roles can be added to the fixed database roles using the  `ALTER ROLE ... ADD MEMBER` statement. For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](../Topic/ALTER%20ROLE%20\(Transact-SQL\).md).  
  
 User\-defined Database Roles  
 Users with the `CREATE ROLE` permission can create new user\-defined database roles to represent groups of users with common permissions. Typically permissions are granted or denied to the entire role, simplifying permissions management and monitoring. Database users can be added to the database roles by using the `ALTER ROLE ... ADD MEMBER` statement. For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](../Topic/ALTER%20ROLE%20\(Transact-SQL\).md).  
  
 Other principals  
 Additional security principals not discussed here include application roles, and logins and users based on certificates or asymmetric keys.  
  
 For a graphic showing the relationships between Windows users, Windows groups, logins, and database users, see [Create a Database User](../../Topics\TopicNameContainA/Create-a-Database-User.md).  
  
## Typical Scenario  
 The following example represents a common and recommended method of configuring permissions.  
  
#### In Active Directory or Azure Active Directory:  
  
1.  Create a Windows user for each person.  
  
2.  Create Windows groups that represent the work units and the work functions.  
  
3.  Add the Windows users to the Windows groups.  
  
#### If the person connecting will be connecting to many databases  
  
1.  Create a login for the Windows groups. \(If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication, skip the Active Directory steps, and create [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication logins here.\)  
  
2.  In the user database, create a database user for the login representing the Windows groups.  
  
3.  In the user database, create one or more user\-defined database roles, each representing a similar function. For example financial analyst, and sales analyst.  
  
4.  Add the database users to one or more user\-defined database roles.  
  
5.  Grant permissions to the user\-defined database roles.  
  
#### If the person connecting will be connecting to only one database  
  
1.  Create a login for the Windows groups. \(If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication, skip the Active Directory steps, and create [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication logins here.\)  
  
2.  In the user database, create a contained database user for the Windows group. \(If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication, skip the Active Directory steps, and create contained database user [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authentication here.  
  
3.  In the user database, create one or more user\-defined database roles, each representing a similar function. For example financial analyst, and sales analyst.  
  
4.  Add the database users to one or more user\-defined database roles.  
  
5.  Grant permissions to the user\-defined database roles.  
  
 The typical result at this point, is that a Windows user is a member of a Windows group. The Windows group has a login in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)]. The login is mapped to a user identity in the user\-database. The user is a member of a database role. Now you need to add permissions to the role.  
  
## Assigning Permissions  
 Most permission statements have the format:  
  
```  
AUTHORIZATION  PERMISSION  ON  SECURABLE::NAME  TO  PRINCIPAL;  
```  
  
-   `AUTHORIZATION` must be `GRANT`, `REVOKE` or `DENY`.  
  
-   The `PERMISSION` establishes what action is allowed or prohibited. [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] can specify 230 permissions. [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] has fewer permissions because some actions are not relevant in Azure. The permissions are listed in the topic [Permissions &#40;Database Engine&#41;](../Topic/Permissions%20\(Database%20Engine\).md) and in the chart referenced below.  
  
-   `ON SECURABLE::NAME` is the type of securable \(server, server object, database, or database object\) and its name. Some permissions do not require `ON SECURABLE::NAME` because it is unambiguous or inappropriate in the context. For example the `CREATE TABLE` permission doesn’t require the `ON SECURABLE::NAME` clause. \(For example `GRANT CREATE TABLE TO Mary;` allows Mary to create tables.\)  
  
-   `PRINCIPAL` is the security principal \(login, user, or role\) which receives or loses the permission. Grant permissions to roles whenever possible.  
  
 The following example grant statement, grants the `UPDATE` permission on the `Parts` table or view which is contained in the `Production` schema to the role named `PartsTeam`:  
  
```  
GRANT UPDATE ON OBJECT::Production.Parts TO PartsTeam;  
```  
  
 Permissions are granted to security principals \(logins, users, and roles\) by using the `GRANT` statement. Permissions are explicitly denied by using the  `DENY` command. A previously granted or denied permission is removed by using the `REVOKE` statement. Permissions are cumulative, with the user receiving all the permissions granted to the user, login, and any group memberships; however any permission denial overrides all grants.  
  
> [!TIP]  
>  A common mistake is to attempt to remove a `GRANT` by using `DENY` instead of `REVOKE`. This can cause problems when a user receives permissions from multiple sources; which is quite common. The following example demonstrates the principal.  
  
 The Sales group receives `SELECT` permissions on the OrderStatus table through the statement `GRANT SELECT ON OBJECT::OrderStatus TO Sales;`. User Ted is a member of the Sales role. Ted has also been granted `SELECT` permission to the OrderStatus table under his own user name through the statement  `GRANT SELECT ON OBJECT::OrderStatus TO Ted;`. Presume the administer wishes to remove the `GRANT` to the Sales role.  
  
-   If the administrator correctly executes `REVOKE SELECT ON OBJECT::OrderStatus TO Sales;`, then Ted will retain `SELECT` access to the OrderStatus table through his individual `GRANT` statement.  
  
-   If the administrator incorrectly executes `DENY SELECT ON OBJECT::OrderStatus TO Sales;` then Ted, as a member of the Sales role, will be denied the `SELECT` permission because the `DENY` to Sales overrides his individual  `GRANT`.  
  
> [!NOTE]  
>  Permissions can be configured using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]. Find the securable in Object Explorer, right\-click the securable, and then click **Properties**. Select the **Permissions** page. For help on using the permission page, see [Permissions or Securables Page](../../Topics\TopicNameNotContainA/Permissions-or-Securables-Page.md).  
  
## Permission Hierarchy  
 Permissions have a parent\/child hierarchy. That is, if you grant `SELECT` permission on a database, that permission includes `SELECT` permission on all \(child\) schemas in the database. If you grant `SELECT` permission on a schema, it includes `SELECT` permission on all the \(child\) tables and views in the schema. The permissions are transitive; that is, if you grant `SELECT` permission on a database, it includes `SELECT` permission on all \(child\) schemas, and all \(grandchild\) tables and views.  
  
 Permissions also have covering permissions. The `CONTROL` permission on an object, normally gives you all other permissions on the object.  
  
 Because both the parent\/child hierarchy and the covering hierarchy can act on the same permission, the permission system can get complicated. For example, let's take a table \(Region\), in a schema \(Customers\), in a database \(SalesDB\).  
  
-   `CONTROL` permission on table Region includes all the other permissions on the table Region, including `ALTER`, `SELECT`, `INSERT`,  `UPDATE`, `DELETE`, and some other permissions.  
  
-   `SELECT` on the Customers schema that owns the Region table includes the `SELECT` permission on the Region table.  
  
 So `SELECT` permission on the Region table can be achieved through any of these six statements:  
  
```  
GRANT SELECT ON OBJECT::Region TO Ted;   
  
GRANT CONTROL ON OBJECT::Region TO Ted;   
  
GRANT SELECT ON SCHEMA::Customers TO Ted;   
  
GRANT CONTROL ON SCHEMA::Customers TO Ted;   
  
GRANT SELECT ON DATABASE::SalesDB TO Ted;   
  
GRANT CONTROL ON DATABASE::SalesDB TO Ted;  
```  
  
## Grant the Least Permission  
 The first permission listed above \(`GRANT SELECT ON OBJECT::Region TO Ted;`\) is the most granular, that is, that statement is the least permission possible that grants the `SELECT`. No permissions to subordinate objects come with it. It's a good principal to always grant the least permission possible, but \(contradicting that\) grant at higher levels in order to simplify the granting system. So if Ted needs permissions to the entire schema, grant `SELECT` once at the schema level, instead of granting `SELECT` at the table or view level many times. The design of the database has a great deal of impact on how successful this strategy can be. This strategy will work best when your database is designed so that objects needing identical permissions are included in a single schema.  
  
## List of Permissions  
 [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] has 230 permissions. [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] has 219 permissions. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] has 214 permissions. [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] has 195 permissions. [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)], [!INCLUDE[ssDW](../../Token\Other/ssDW_md.md)], and [!INCLUDE[ssAPS](../../Token\Other/ssAPS_md.md)] have fewer permissions because they expose only a portion of the database engine, though each have some permissions that do not apply to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The following graphic shows the permissions and their relationships to each other. Some of the higher level permissions \(such as `CONTROL SERVER`\) are listed many times. In this topic, the poster is far to small to read. Download the Database Engine Permissions Poster from [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
 ![Database Engine Permissions](../../Images\Image\ImageNotContaina/Database-Engine-Permissions.PNG "Database Engine Permissions")  
  
 For a graphic showing the relationships among the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] principals and server and database objects,  see [Permissions Hierarchy &#40;Database Engine&#41;](../Topic/Permissions%20Hierarchy%20\(Database%20Engine\).md).  
  
## Permissions vs. Fixed Server and Fixed Database Roles  
 The permissions of the fixed server roles and fixed database roles are similar but not exactly the same as the granular permissions. For example, members of the `sysadmin` fixed server role have all permissions on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], as do logins with the `CONTROL SERVER` permission. But granting the `CONTROL SERVER` permission does not make a login a member of the sysadmin fixed server role, and making adding a login to the  `sysadmin` fixed server role does not explicitly grant the login the  `CONTROL SERVER` permission. Sometimes a stored procedure will check permissions by checking the fixed role and not checking the granular permission. For example detaching a database requires membership in the `db_owner` fixed database role. The equivalent `CONTROL DATABASE` permission is not enough. These two systems operate in parallel but rarely interact with each other. Microsoft recommends using the newer, granular permission system instead of the fixed roles whenever possible.  
  
## Monitoring Permissions  
 The following views return security information.  
  
-   The logins and user\-defined server roles on a server can be examined by using the `sys.server_principals` view. This view is not available in [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)].  
  
-   The users and user\-defined roles in a database can be examined by using the `sys.database_principals` view.  
  
-   The permissions granted to logins and user\-defined fixed server roles can be examined by using the `sys.server_permissions` view. This view is not available in [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)].  
  
-   The permissions granted to users and user\-defined fixed database roles can be examined by using the `sys.database_permissions` view.  
  
-   Database role membership can be examined by using the `sys. sys.database_role_members` view.  
  
-   Server role membership can be examined by using the `sys.server_role_members` view. This view is not available in [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)].  
  
-   For additional security related views, see [Security Catalog Views &#40;Transact-SQL&#41;](../Topic/Security%20Catalog%20Views%20\(Transact-SQL\).md) .  
  
### Useful Transact\-SQL Statements  
 The following statements return useful information about permissions.  
  
 To return the explicit permissions granted or denied in a database \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)]\), execute the following statement in the database.  
  
```  
SELECT   
    perms.state_desc AS State,   
    permission_name AS [Permission],   
    obj.name AS [on Object],   
    dPrinc.name AS [to User Name],   
    sPrinc.name AS [who is Login Name]  
FROM sys.database_permissions AS perms  
JOIN sys.database_principals AS dPrinc  
    ON perms.grantee_principal_id = dPrinc.principal_id  
JOIN sys.objects AS obj  
    ON perms.major_id = obj.object_id  
LEFT OUTER JOIN sys.server_principals AS sPrinc  
    ON dPrinc.sid = sPrinc.sid;  
```  
  
 To return the members of the server roles \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] only\), execute the following statement.  
  
```  
SELECT sRole.name AS [Server Role Name] , sPrinc.name AS [Members]  
FROM sys.server_role_members AS sRo  
JOIN sys.server_principals AS sPrinc  
    ON sRo.member_principal_id = sPrinc.principal_id  
JOIN sys.server_principals AS sRole  
    ON sRo.role_principal_id = sRole.principal_id;  
```  
  
 To return the members of the database roles \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)]\), execute the following statement in the database.  
  
```  
SELECT dRole.name AS [Database Role Name], dPrinc.name AS [Members]  
FROM sys.database_role_members AS dRo  
JOIN sys.database_principals AS dPrinc  
    ON dRo.member_principal_id = dPrinc.principal_id  
JOIN sys.database_principals AS dRole  
    ON dRo.role_principal_id = dRole.principal_id;  
```  
  
## Next Steps  
 For more topics to get you started, see:  
  
-   [Tutorial: Getting Started with the Database Engine](../Topic/Tutorial:%20Getting%20Started%20with%20the%20Database%20Engine.md) [Creating a Database &#40;Tutorial&#41;](../Topic/Creating%20a%20Database%20\(Tutorial\).md)  
  
-   [Tutorial: SQL Server Management Studio](../Topic/Tutorial:%20SQL%20Server%20Management%20Studio.md)  
  
-   [Tutorial: Writing Transact-SQL Statements](../Topic/Tutorial:%20Writing%20Transact-SQL%20Statements.md)  
  
## See Also  
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)   
 [Security Functions &#40;Transact-SQL&#41;](../Topic/Security%20Functions%20\(Transact-SQL\).md)   
 [Security-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;](../Topic/Security-Related%20Dynamic%20Management%20Views%20and%20Functions%20\(Transact-SQL\).md)   
 [Security Catalog Views &#40;Transact-SQL&#41;](../Topic/Security%20Catalog%20Views%20\(Transact-SQL\).md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../Topic/sys.fn_builtin_permissions%20\(Transact-SQL\).md)  
  
  