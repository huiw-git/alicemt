---
title: Create Views
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-views
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
---
# Create Views
  You can create views in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. A view can be used for the following purposes:  
  
-   To focus, simplify, and customize the perception each user has of the database.  
  
-   As a security mechanism by allowing users to access data through the view, without granting the users permissions to directly access the underlying base tables.  
  
-   To provide a backward compatible interface to emulate a table whose schema has changed.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To create a view, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 A view can be created only in the current database.  
  
 A view can have a maximum of 1,024 columns.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To create a view by using the Query and View Designer  
  
1.  In **Object Explorer**, expand the database where you want to create your new view.  
  
2.  Right\-click the **Views** folder, then click **New View…**.  
  
3.  In the **Add Table** dialog box, select the element or elements that you want to include in your new view from one of the following tabs: Tables, Views, Functions, and Synonyms.  
  
4.  Click **Add**, then click **Close**.  
  
5.  In the **Diagram Pane**, select the columns or other elements to include in the new view.  
  
6.  In the **Criteria Pane**, select additional sort or filter criteria for the columns.  
  
7.  On the **File** menu, click **Save***view name*.  
  
8.  In the **Choose Name** dialog box, enter a name for the new view and click **OK**.  
  
     For more information about the query and view designer, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](../Topic/Query%20and%20View%20Designer%20Tools%20\(Visual%20Database%20Tools\).md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To create a view  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](../Topic/CREATE%20VIEW%20\(Transact-SQL\).md).  
  
  