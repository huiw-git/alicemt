---
title: "Transact-SQL Syntax Supported by IntelliSense"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Transact-SQL Syntax Supported by IntelliSense
This topic describes the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
## Statements Supported by IntelliSense  
 In [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements. Some general [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor conditions might prevent IntelliSense from functioning. For more information, see [Troubleshooting IntelliSense (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Troubleshooting-IntelliSense--SQL-Server-Management-Studio-.md).  
  
> [!NOTE]  
>  IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user-defined functions. Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user-defined types.  
  
### SELECT Statement  
 The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:  
  
|||  
|-|-|  
|SELECT|WHERE|  
|FROM|ORDER BY|  
|HAVING|UNION|  
|FOR|GROUP BY|  
|TOP|OPTION (hint)|  
  
### Additional Transact-SQL Statements That Are Supported  
 The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements that are shown in the following table.  
  
|Transact-SQL statement|Syntax supported|Exceptions|  
|-----------------------------|----------------------|----------------|  
|[INSERT](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50)|All syntax, except the *execute_statement* clause.|None|  
|[UPDATE](assetId:///40e63302-0c68-4593-af3e-6d190181fee7)|All syntax.|None|  
|[DELETE](assetId:///ed6b2105-0f35-408f-ba51-e36ade7ad5b2)|All syntax.|None|  
|[DECLARE @local_variable](assetId:///d1635ebb-f751-4de1-8bbc-cae161f90821)|All syntax.|None|  
|[SET @local_variable](assetId:///d410e06e-061b-4c25-9973-b2dc9b60bd85)|All syntax.|None|  
|[EXECUTE](assetId:///bc806b71-cc55-470a-913e-c5f761d5c4b7)|Execution of user-defined stored procedures, system stored procedures, user-defined functions, and system functions.|None|  
|[CREATE TABLE](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)|All syntax.|None|  
|[CREATE VIEW](assetId:///aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9)|All syntax.|None|  
|[CREATE PROCEDURE](assetId:///afe3d86d-c9ab-44e4-b74d-4e3dbd9cc58c)|All syntax.|There is no IntelliSense support for the EXTERNAL NAME clause.<br /><br /> In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.|  
|[ALTER PROCEDURE](assetId:///ed9b2f76-11ec-498d-a95e-75b490a75733)|All syntax|There is no IntelliSense support for the EXTERNAL NAME clause.<br /><br /> In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.|  
|[USE](assetId:///c05acac8-c063-4770-8e36-d7f71d500b10)|All syntax.|None|  
  
## IntelliSense in Supported Statements  
 IntelliSense in the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements:  
  
-   All join types, including APPLY  
  
-   PIVOT and UNPIVOT  
  
-   References to the following database objects:  
  
    -   Databases and schemas  
  
    -   Tables, views, table-valued functions, and table expressions  
  
    -   Columns  
  
    -   Procedures and procedure parameters  
  
    -   Scalar functions and scalar expressions  
  
    -   Local variables  
  
    -   Common table expressions (CTE)  
  
-   Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run. These objects are as follows:  
  
    -   Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.  
  
    -   Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.  
  
    > [!NOTE]  
    >  IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.  
  
 IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements. For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.  
  
## Examples  
 Within a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor supports only the statements and syntax that are listed in this topic. The following [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code examples show what statements and syntax elements IntelliSense supports. For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 This functionality also applies to the sets of [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.  
  
 Within a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed. For example, you might enter the following code in the Query Editor:  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 After you type `SELECT`, IntelliSense lists **PrimaryKeyCol**, **FirstNameCol**, and **LastNameCol** as possible elements in the select list, even if the script has not been executed and `MyTable` does not yet exist in `MyTestDB`.