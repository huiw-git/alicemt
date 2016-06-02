---
title: View or Change the Properties of a Database
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
---
# View or Change the Properties of a Database
  This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. After you change a database property, the modification takes effect immediately.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To view or change the properties of a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When AUTO\_CLOSE is ON, some columns in the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data. To resolve this, open the database.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database to change the properties of a database. Requires at least membership in the Public database role to view the properties of a database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or change the properties of a database  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database to view, and then click **Properties**.  
  
3.  In the **Database Properties** dialog box, select a page to view the corresponding information. For example, select the **Files** page to view data and log file information.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Transact\-SQL provides a number of different methods for viewing the properties of a database and view changing the properties of a database. To view the properties of a database, you can use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../Topic/DATABASEPROPERTYEX%20\(Transact-SQL\).md) function and the [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view. To change the properties of a database, you can use the version of the ALTER DATABASE statement for your environment:  [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md) or [ALTER DATABASE &#40;Azure SQL Database&#41;](../Topic/ALTER%20DATABASE%20\(Azure%20SQL%20Database\).md). To view database scoped properties, use the [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../Topic/sys.database_scoped_configurations%20\(Transact-SQL\).md) catalog view and to alter database scoped properties, use the [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SCOPED%20CONFIGURATION%20\(Transact-SQL\).md) statement.  
  
#### To view a property of a database by using the DATABASEPROPERTYEX function  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then connect to the database for which you wish to view its properties.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses the [DATABASEPROPERTYEX](../Topic/DATABASEPROPERTYEX%20\(Transact-SQL\).md) system function to return the status of the AUTO\_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database. A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.  
  
    ```tsql  
    SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
    ```  
  
#### To view the properties of a database by querying sys.databases  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then connect to the database for which you wish to view its properties..  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database. This example returns the database ID number \(`database_id`\), whether the database is read\-only or read\-write \(`is_read_only`\), the collation for the database \(`collation_name`\), and the database compatibility level \(`compatibility_level`\).  
  
    ```tsql  
    SELECT database_id, is_read_only, collation_name, compatibility_level  
    FROM sys.databases WHERE name = 'AdventureWorks2012';  
    ```  
  
#### To view the properties of a database\-scoped configuration by querying sys.databases\_scoped\_configuration  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and then connect to the database for which you wish to view its properties..  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../Topic/sys.database_scoped_configurations%20\(Transact-SQL\).md) catalog view to view several properties of the current database.  
  
    ```tsql  
    SELECT configuration_id, name, value, value_for_secondary  
    FROM sys.database_scoped_configurations;  
    ```  
  
     For more examples, see [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../Topic/sys.database_scoped_configurations%20\(Transact-SQL\).md)  
  
#### To change the properties of a SQL Server 2016 database using ALTER DATABASE  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window. The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database, changes the state of the property, and then verifies the change.  
  
     To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.  
  
     To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.  
  
     To verify the change, select the second `SELECT` statement, and click **Execute**.  
  
     [!CODE [DatabaseDDL#AlterDatabase9](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase9)]  
  
#### To change the database\-scoped properties using ALTER DATABASE SCOPED CONFIGURATION  
  
1.  Connect to a database in your SQL Server instance.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window. The following example sets MAXDOP for a secondary database to the value for the primary database.  
  
    ```  
    ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY   
    ```  
  
## See Also  
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../Topic/DATABASEPROPERTYEX%20\(Transact-SQL\).md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [ALTER DATABASE &#40;Azure SQL Database&#41;](../Topic/ALTER%20DATABASE%20\(Azure%20SQL%20Database\).md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SCOPED%20CONFIGURATION%20\(Transact-SQL\).md)   
 [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../Topic/sys.database_scoped_configurations%20\(Transact-SQL\).md)  
  
  