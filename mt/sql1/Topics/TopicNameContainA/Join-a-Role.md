---
title: "Join a Role"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Join a Role
This topic describes how to assign roles to logins and database users in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Use roles in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to efficiently manage permissions. Assign permissions to roles, and then add and remove users and logins to the roles. By using roles, permissions do not have to be individually maintained for each user.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports four types of roles.  
  
-   Fixed server roles  
  
-   User-defined server roles  
  
-   Fixed database roles  
  
-   User-defined database roles  
  
 The fixed roles are automatically available in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Fixed roles have the necessary permissions to accomplish common tasks. For more information about fixed roles, see the following links. User-defined roles are created by you, and can be customized with the permissions that you select. For more information about user-defined roles, see the following links.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To assign roles to logins and database users, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Changing the name of a database role does not change ID number, owner, or permissions of the role.  
  
-   Database roles are visible in the sys.database_role_members and sys.database_principals catalog views.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires **ALTER ANY ROLE** permission on the database, **ALTER** permission on the role, or membership in **db_securityadmin**.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To add a member to a fixed server role  
  
1.  In Object Explorer, expand the server in which you want to edit a fixed server role.  
  
2.  Expand the **Security** folder.  
  
3.  Expand the **Server Roles** folder  
  
4.  Right-click the role you want to edit and select **Properties**.  
  
5.  In the **Server Role Properties –***server_role_name* dialog box, on the **Members** page, click **Add**.  
  
6.  In the **Select Server Login or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or server role to add to this server role. Alternately, click **Browse…** and select any or all of the available objects in the **Browse for Objects** dialog box. Click **OK** to return to the **Server Role Properties –***server_role_name* dialog box.  
  
7.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
#### To add a member to a user-defined database role  
  
1.  In Object Explorer, expand the server in which you want to edit a user-defined database role.  
  
2.  Expand the **Databases** folder.  
  
3.  Expand the database in which you want to edit a user-defined database role.  
  
4.  Expand the **Security** folder.  
  
5.  Expand the **Roles** folder.  
  
6.  Expand the **Server Roles** folder.  
  
7.  Right-click the role you want to edit and select **Properties**.  
  
8.  In the **Database Role Properties –***database_role_name* dialog box, in the **General** page, click **Add**.  
  
9. In the **Select Database User or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or database role to add to this database role. Alternately, click **Browse…** and select any or all of the available objects in the **Browse for Objects** dialog box. Click **OK** to return to the **Database Role Properties –***database_role_name* dialog box.  
  
10. [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To add a member to a fixed server role  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD [Domain\Juan] ;  
    GO  
    ```  
  
 For more information, see [ALTER ROLE (Transact-SQL)](assetId:///e1e83caa-17cc-4871-b2db-2711339fb64f).  
  
#### To add a member to a user-defined database role  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 For more information, see [sp_addrolemember (Transact-SQL)](assetId:///a583c087-bdb3-46d2-b9e5-3921b3e6d10b).  
  
## See Also  
 [Server-Level Roles](../../Topics/TopicNameNotContainA/Server-Level-Roles.md)   
 [Database-Level Roles](../../Topics/TopicNameNotContainA/Database-Level-Roles.md)   
 [Application Roles](../../Topics/TopicNameNotContainA/Application-Roles.md)