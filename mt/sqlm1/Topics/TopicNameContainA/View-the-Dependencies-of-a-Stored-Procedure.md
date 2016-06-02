---
title: View the Dependencies of a Stored Procedure
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-stored-Procs
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
---
# View the Dependencies of a Stored Procedure
  This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
##  <a name="Top"></a>   
-   **Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)  
  
-   **To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 System Function: **sys.dm\_sql\_referencing\_entities**  
 Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm\_sql\_referencing\_entities. When the referenced entity is a partition function, CONTROL permission on the database is required. By default, SELECT permission is granted to public.  
  
 System Function: **sys.dm\_sql\_referenced\_entities**  
 Requires SELECT permission on sys.dm\_sql\_referenced\_entities and VIEW DEFINITION permission on the referencing entity. By default, SELECT permission is granted to public. Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database\-level DDL trigger. Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server\-level DDL trigger.  
  
 Object Catalog View: **sys.sql\_expression\_dependencies**  
 Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql\_expression\_dependencies for the database. By default, SELECT permission is granted only to members of the db\_owner fixed database role. When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.  
  
##  <a name="Procedures"></a> How to View the Dependencies of a Stored Procedure  
 You can use one of the following:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact\-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view the dependencies of a procedure in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.  
  
3.  Expand **Stored Procedures**, right\-click the procedure and then click **View Dependencies**.  
  
4.  View the list of objects that depend on the procedure.  
  
5.  View the list of objects on which the procedure depends.  
  
6.  Click **OK**.  
  
###  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view the dependencies of a procedure in Query Editor**  
  
 System Function: **sys.dm\_sql\_referencing\_entities**  
 This function is used to display the objects that depend on a procedure.  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs.  
  
3.  Click on **New Query** under the **File** menu.  
  
4.  Copy and paste the following examples into the query editor. The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../Token\Other/ssSampleDBCoFull_md.md)] database, the products they supply, their credit ratings, and their availability.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  After the procedure is created, the second example uses the sys.dm\_sql\_referencing\_entities function to display the objects that depend on the procedure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 System Function: **sys.dm\_sql\_referenced\_entities**  
 This function is used to display the objects a procedure depends on.  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs.  
  
3.  Click on **New Query** under the **File** menu.  
  
4.  Copy and paste the following examples into the query editor. The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../Token\Other/ssSampleDBCoFull_md.md)] database, the products they supply, their credit ratings, and their availability.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  After the procedure is created, the second example uses the sys.dm\_sql\_referenced\_entities function to display the objects that the procedure depends on.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 Object Catalog View: **sys.sql\_expression\_dependencies**  
 This view can be used to display objects that a procedure depends on or that depend on a procedure.  
  
 Displaying the objects that depend on a procedure.  
 1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs.  
  
3.  Click on **New Query** under the **File** menu.  
  
4.  Copy and paste the following examples into the query editor. The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../Token\Other/ssSampleDBCoFull_md.md)] database, the products they supply, their credit ratings, and their availability.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  After the procedure is created, the second example uses the sys.sql\_expression\_dependencies view to display the objects that depend on the procedure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 Displaying the objects a procedure depends on.  
 1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database in which the procedure belongs.  
  
3.  Click on **New Query** under the **File** menu.  
  
4.  Copy and paste the following examples into the query editor. The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../Token\Other/ssSampleDBCoFull_md.md)] database, the products they supply, their credit ratings, and their availability.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  After the procedure is created, the second example uses the sys.sql\_expression\_dependencies view to display the objects the procedure depends on.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo');  
    GO  
    ```  
  
## See Also  
 [Rename a Stored Procedure](../../Topics\TopicNameContainA/Rename-a-Stored-Procedure.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../Topic/sys.dm_sql_referencing_entities%20\(Transact-SQL\).md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../Topic/sys.dm_sql_referenced_entities%20\(Transact-SQL\).md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../Topic/sys.sql_expression_dependencies%20\(Transact-SQL\).md)  
  
  