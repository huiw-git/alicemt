---
title: "Grant Permissions on a Stored Procedure"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-stored-Procs
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Grant Permissions on a Stored Procedure
This topic describes how to grant permissions on a stored procedure in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Permissions can be granted to an existing user, database role, or application role in the database.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To grant permissions on a stored procedure, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   You cannot use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to grant permissions on system procedures or system functions. Use [GRANT Object Permissions](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea) instead.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION, or a higher permission that implies the permission being granted. Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure. For more information, see [GRANT Object Permissions (Transact-SQL)](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To grant permissions on a stored procedure  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.  
  
3.  Expand **Stored Procedures**, right-click the procedure to grant permissions on, and then click **Properties**.  
  
4.  From **Stored Procedure Properties**, select the **Permissions** page.  
  
5.  To grant permissions to a user, database role, or application role, click **Search**.  
  
6.  In **Select Users or Roles**, click **Object Types** to add or clear the users and roles you want.  
  
7.  Click **Browse** to display the list of users or roles. Select the users or roles to whom permissions should be granted.  
  
8.  In the **Explicit Permissions** grid, select the permissions to grant to the specified user or role. For a description of the permissions, see [Permissions (Database Engine)](../../Topics/TopicNameNotContainA/Permissions--Database-Engine-.md).  
  
 Selecting **Grant** indicates the grantee will be given the specified permission. Selecting **Grant With** indicates that the grantee will also be able to grant the specified permission to other principals.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To grant permissions on a stored procedure  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example grants `EXECUTE` permission on the stored procedure `HumanResources.uspUpdateEmployeeHireInfo` to an application role named `Recruiting11`.  
  
```tsql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## See Also  
 [Sys.Fn_Builtin_Permissions (Transact-SQL)](assetId:///704b1ad3-3534-4cf3-aff4-9fb70064b6cc)   
 [GRANT Object Permissions (Transact-SQL)](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea)   
 [Create a Stored Procedure](../../Topics/TopicNameContainA/Create-a-Stored-Procedure.md)   
 [Modify a Stored Procedure](../../Topics/TopicNameContainA/Modify-a-Stored-Procedure.md)   
 [Delete a Stored Procedure](../../Topics/TopicNameContainA/Delete-a-Stored-Procedure.md)   
 [Rename a Stored Procedure](../../Topics/TopicNameContainA/Rename-a-Stored-Procedure.md)