---
title: "View or Change the Properties of a Database"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-01-18
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# View or Change the Properties of a Database
This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. After you change a database property, the modification takes effect immediately.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To view or change the properties of a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When AUTO_CLOSE is ON, some columns in the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data. To resolve this, open the database.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database to change the properties of a database. Requires at least membership in the Public database role to view the properties of a database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or change the properties of a database  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **Databases**, right-click the database to view, and then click **Properties**.  
  
3.  In the **Database Properties** dialog box, select a page to view the corresponding information. For example, select the **Files** page to view data and log file information.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 Transact-SQL provides a number of different methods for viewing the properties of a database and view changing the properties of a database. To view the properties of a database, you can use the [DATABASEPROPERTYEX (Transact-SQL)](assetId:///8a9e0ffb-28b5-4640-95b2-a54e3e5ad941) function and the [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view. To change the properties of a database, you can use the version of the ALTER DATABASE statement for your environment:  [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da) or [ALTER DATABASE (Azure SQL Database)](assetId:///6fc5fd95-2045-4f20-a914-3598091bc7cc). To view database scoped properties, use the [sys.database_scoped_configurations (Transact-SQL)](assetId:///8899310a-3464-4d38-9f2f-88396c4e7dc2) catalog view and to alter database scoped properties, use the [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a) statement.  
  
#### To view a property of a database by using the DATABASEPROPERTYEX function  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then connect to the database for which you wish to view its properties.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses the [DATABASEPROPERTYEX](assetId:///8a9e0ffb-28b5-4640-95b2-a54e3e5ad941) system function to return the status of the AUTO_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database. A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.  
  
    ```tsql  
    SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
    ```  
  
#### To view the properties of a database by querying sys.databases  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then connect to the database for which you wish to view its properties..  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database. This example returns the database ID number (`database_id`), whether the database is read-only or read-write (`is_read_only`), the collation for the database (`collation_name`), and the database compatibility level (`compatibility_level`).  
  
    ```tsql  
    SELECT database_id, is_read_only, collation_name, compatibility_level  
    FROM sys.databases WHERE name = 'AdventureWorks2012';  
    ```  
  
#### To view the properties of a database-scoped configuration by querying sys.databases_scoped_configuration  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then connect to the database for which you wish to view its properties..  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.database_scoped_configurations (Transact-SQL)](assetId:///8899310a-3464-4d38-9f2f-88396c4e7dc2) catalog view to view several properties of the current database.  
  
    ```tsql  
    SELECT configuration_id, name, value, value_for_secondary  
    FROM sys.database_scoped_configurations;  
    ```  
  
     For more examples, see [sys.database_scoped_configurations (Transact-SQL)](assetId:///8899310a-3464-4d38-9f2f-88396c4e7dc2)  
  
#### To change the properties of a SQL Server 2016 database using ALTER DATABASE  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window. The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database, changes the state of the property, and then verifies the change.  
  
     To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.  
  
     To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.  
  
     To verify the change, select the second `SELECT` statement, and click **Execute**.  
  
     [!CODE [DatabaseDDL#AlterDatabase9](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase9)]  
  
#### To change the database-scoped properties using ALTER DATABASE SCOPED CONFIGURATION  
  
1.  Connect to a database in your SQL Server instance.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window. The following example sets MAXDOP for a secondary database to the value for the primary database.  
  
    ```  
    ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY   
    ```  
  
## See Also  
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)   
 [DATABASEPROPERTYEX (Transact-SQL)](assetId:///8a9e0ffb-28b5-4640-95b2-a54e3e5ad941)   
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [ALTER DATABASE (Azure SQL Database)](assetId:///6fc5fd95-2045-4f20-a914-3598091bc7cc)   
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a)   
 [sys.database_scoped_configurations (Transact-SQL)](assetId:///8899310a-3464-4d38-9f2f-88396c4e7dc2)