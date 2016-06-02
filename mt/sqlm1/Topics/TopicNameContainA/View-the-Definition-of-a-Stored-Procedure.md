---
title: View the Definition of a Stored Procedure
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-stored-Procs
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
---
# View the Definition of a Stored Procedure
    
##  <a name="Top"></a> You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.  
  
-   **Before you begin:**  [Security](#Security)  
  
-   **To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 System Stored Procedure: **sp\_helptext**  
 Requires membership in the **public** role. System object definitions are publicly visible. The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.  
  
 System Function: **OBJECT\_DEFINITION**  
 System object definitions are publicly visible. The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION. These permissions are implicitly held by members of the **db\_owner**, **db\_ddladmin**, and **db\_securityadmin** fixed database roles.  
  
 Object Catalog View: **sys.sql\_modules**  
 The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission. For more information, see [Metadata Visibility Configuration](../../Topics\TopicNameNotContainA/Metadata-Visibility-Configuration.md).  
  
##  <a name="Procedures"></a> How to View the Definition of a Stored Procedure  
 You can use one of the following:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact\-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view the definition a procedure in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.  
  
3.  Expand **Stored Procedures**, right\-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.  
  
4.  Select **New Query Editor Window**. This will display the procedure definition.  
  
###  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view the definition of a procedure in Query Editor**  
  
 System Stored Procedure: **sp\_helptext**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statement that uses the **sp\_helptext** system stored procedure. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 System Function: **OBJECT\_DEFINITION**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statements that use the **OBJECT\_DEFINITION** system function. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Object Catalog View: **sys.sql\_modules**  
 1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the toolbar, click **New Query**.  
  
3.  In the query window, enter the following statements that use the **sys.sql\_modules** catalog view. Change the database name and stored procedure name to reference the database and stored procedure that you want.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## See Also  
 [Create a Stored Procedure](../../Topics\TopicNameContainA/Create-a-Stored-Procedure.md)   
 [Modify a Stored Procedure](../../Topics\TopicNameContainA/Modify-a-Stored-Procedure.md)   
 [Delete a Stored Procedure](../../Topics\TopicNameContainA/Delete-a-Stored-Procedure.md)   
 [Rename a Stored Procedure](../../Topics\TopicNameContainA/Rename-a-Stored-Procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../Topic/OBJECT_DEFINITION%20\(Transact-SQL\).md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../Topic/sys.sql_modules%20\(Transact-SQL\).md)   
 [sp_helptext &#40;Transact-SQL&#41;](../Topic/sp_helptext%20\(Transact-SQL\).md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../Topic/OBJECT_ID%20\(Transact-SQL\).md)  
  
  