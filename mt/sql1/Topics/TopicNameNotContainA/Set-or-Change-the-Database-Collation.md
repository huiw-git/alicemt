---
title: "Set or Change the Database Collation"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Set or Change the Database Collation
This topic describes how set and change the database collation in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. If no collation is specified, the server collation is used.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To set or change the database collation, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Windows Unicode-only collations can only be used with the COLLATE clause to apply collations to the **nchar**, **nvarchar**, and **ntext** data types on column level and expression-level data. They cannot be used with the COLLATE clause to change the collation of a database or server instance.  
  
-   If the specified collation or the collation used by the referenced object uses a code page that is not supported by Windows, the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] displays an error.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   You can find the supported collation names in [Windows Collation Name (Transact-SQL)](assetId:///acceef84-2c68-46e2-a021-be019b7ab14e) and [SQL Server Collation Name (Transact-SQL)](assetId:///56483d24-add7-483d-9b96-c6fda460ddbc); or you can use the [sys.fn_helpcollations (Transact-SQL)](assetId:///b5082e81-1fee-4e2c-b567-5412eaee41c1) system function.  
  
-   When you change the database collation, you change the following:  
  
    -   Any **char**, **varchar**, **text**, **nchar**, **nvarchar**, or **ntext** columns in system tables are changed to the new collation.  
  
    -   All existing **char**, **varchar**, **text**, **nchar**, **nvarchar**, or **ntext** parameters and scalar return values for stored procedures and user-defined functions are changed to the new collation.  
  
    -   The **char**, **varchar**, **text**, **nchar**, **nvarchar**, or **ntext** system data types, and all user-defined data types based on these system data types, are changed to the new default collation.  
  
-   You can change the collation of any new objects that are created in a user database by using the COLLATE clause of the [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da) statement. This statement does not change the collation of the columns in any existing user-defined tables. These can be changed by using the COLLATE clause of [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 CREATE DATABASE  
 Requires CREATE DATABASE permission in the **master** database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.  
  
 ALTER DATABASE  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To set or change the database collation  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], expand that instance, and then expand **Databases**.  
  
2.  If you are creating a new database, right-click **Databases** and then click **New Database**. If you do not want the default collation, click the **Options** page, and select a collation from the **Collation** drop-down list.  
  
     Alternatively, if the database already exists, right-click the database that you want and click **Properties**. Click the **Options** page, and select a collation from the **Collation** drop-down list.  
  
3.  After you are finished, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To set the database collation  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use the [COLLATE](assetId:///76763ac8-3e0d-4bbb-aa53-f5e7da021daa) clause to specify a collation name. The example creates the database `MyOptionsTest` that uses the `Latin1_General_100_CS_AS_SC` collation. After you create the database, execute the `SELECT` statement to verify the setting.  
  
```tsql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### To change the database collation  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use the [COLLATE](assetId:///76763ac8-3e0d-4bbb-aa53-f5e7da021daa) clause in an [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da) statement to change the collation name. Execute the `SELECT` statement to verify the change.  
  
```tsql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## See Also  
 [Collation and Unicode Support](../../Topics/TopicNameNotContainA/Collation-and-Unicode-Support.md)   
 [sys.fn_helpcollations (Transact-SQL)](assetId:///b5082e81-1fee-4e2c-b567-5412eaee41c1)   
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)   
 [SQL Server Collation Name (Transact-SQL)](assetId:///56483d24-add7-483d-9b96-c6fda460ddbc)   
 [Windows Collation Name (Transact-SQL)](assetId:///acceef84-2c68-46e2-a021-be019b7ab14e)   
 [COLLATE (Transact-SQL)](assetId:///76763ac8-3e0d-4bbb-aa53-f5e7da021daa)   
 [Collation Precedence (Transact-SQL)](assetId:///58c4e64b-5634-4c29-aa22-33193282dd27)   
 [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)   
 [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)   
 [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1)   
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)