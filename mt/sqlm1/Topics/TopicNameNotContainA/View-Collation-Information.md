---
title: View Collation Information
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
---
# View Collation Information
    
##  <a name="Top"></a> You can view the collation of a server, database, or column in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] using Object Explorer menu options or by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
##  <a name="Procedures"></a> How to View a Collation Setting  
 You can use one of the following:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact\-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view a collation setting for a server \(instance of SQL Server\) in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  Right\-click the instance and select **Properties**.  
  
 **To view a collation setting for a database in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database and select **Properties**.  
  
 **To view a collation setting for a column in Object Explorer**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the database and then expand **Tables**.  
  
3.  Expand the table that contains the column and then expand **Columns**.  
  
4.  Right\-click the column and select **Properties**. If the collation property is empty, the column is not a character data type.  
  
###  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view the collation setting of a server**  
  
1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and on the toolbar, click **New Query**.  
  
2.  In the query window, enter the following statement that uses the SERVERPROPERTY system function.  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  Alternatively, you can use the sp\_helpsort system stored procedure.  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **To view all collations supported by [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]**  
  
1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and on the toolbar, click **New Query**.  
  
2.  In the query window, enter the following statement that uses the SERVERPROPERTY system function.  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **To view the collation setting of a database**  
  
1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and on the toolbar, click **New Query**.  
  
2.  In the query window, enter the following statement that uses the sys.databases system catalog view.  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  Alternatively, you can use the DATABASEPROPERTYEX system function.  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **To view the collation setting of a column**  
  
1.  In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and on the toolbar, click **New Query**.  
  
2.  In the query window, enter the following statement that uses the sys.columns system catalog view.  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## See Also  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../Topic/sys.fn_helpcollations%20\(Transact-SQL\).md)   
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)   
 [sys.columns &#40;Transact-SQL&#41;](../Topic/sys.columns%20\(Transact-SQL\).md)   
 [Collation Precedence &#40;Transact-SQL&#41;](../Topic/Collation%20Precedence%20\(Transact-SQL\).md)   
 [sp_helpsort &#40;Transact-SQL&#41;](../Topic/sp_helpsort%20\(Transact-SQL\).md)  
  
  