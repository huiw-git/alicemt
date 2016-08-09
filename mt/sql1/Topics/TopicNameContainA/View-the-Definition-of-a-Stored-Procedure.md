---
title: "View the Definition of a Stored Procedure"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-stored-Procs
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# View the Definition of a Stored Procedure
##  <a name="Top"></a> You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.  
  
-   **Before you begin:**  [Security](#Security)  
  
-   **To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 System Stored Procedure: **sp_helptext**  
 Requires membership in the **public** role. System object definitions are publicly visible. The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.  
  
 System Function: **OBJECT_DEFINITION**  
 System object definitions are publicly visible. The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION. These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.  
  
 Object Catalog View: **sys.sql_modules**  
 The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission. For more information, see [Metadata Visibility Configuration](../../Topics/TopicNameNotContainA/Metadata-Visibility-Configuration.md).  
  
##  <a name="Procedures"></a> How to View the Definition of a Stored Procedure  
 You can use one of the following:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view the definition a procedure in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.  
  
3.  Expand **Stored Procedures**, right-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.  
  
4.  Select **New Query Editor Window**. This will display the procedure definition.  
  
###  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To view the definition of a procedure in Query Editor**  
  
 System Stored Procedure: **sp_helptext**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statement that uses the **sp_helptext** system stored procedure. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 System Function: **OBJECT_DEFINITION**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statements that use the **OBJECT_DEFINITION** system function. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Object Catalog View: **sys.sql_modules**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statements that use the **sys.sql_modules** catalog view. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## See Also  
 [Create a Stored Procedure](../../Topics/TopicNameContainA/Create-a-Stored-Procedure.md)   
 [Modify a Stored Procedure](../../Topics/TopicNameContainA/Modify-a-Stored-Procedure.md)   
 [Delete a Stored Procedure](../../Topics/TopicNameContainA/Delete-a-Stored-Procedure.md)   
 [Rename a Stored Procedure](../../Topics/TopicNameContainA/Rename-a-Stored-Procedure.md)   
 [OBJECT_DEFINITION (Transact-SQL)](assetId:///2ac837c7-eca9-4d29-b06e-72e30450c68d)   
 [sys.sql_modules (Transact-SQL)](assetId:///23d3ccd2-f356-4d89-a2cd-bee381243f99)   
 [sp_helptext (Transact-SQL)](assetId:///24135456-05f0-427c-884b-93cf38dd47a8)   
 [OBJECT_ID (Transact-SQL)](assetId:///f89286db-440f-4218-a828-30881ce3077a)