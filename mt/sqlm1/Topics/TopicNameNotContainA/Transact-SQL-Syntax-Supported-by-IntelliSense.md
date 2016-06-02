---
title: Transact-SQL Syntax Supported by IntelliSense
ms.custom: na
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
---
# Transact-SQL Syntax Supported by IntelliSense
  This topic describes the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
## Statements Supported by IntelliSense  
 In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements. Some general [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor conditions might prevent IntelliSense from functioning. For more information, see [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](../Topic/Troubleshooting%20IntelliSense%20\(SQL%20Server%20Management%20Studio\).md).  
  
> [!NOTE]  
>  IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user\-defined functions. Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user\-defined types.  
  
### SELECT Statement  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:  
  
|||  
|-|-|  
|SELECT|WHERE|  
|FROM|ORDER BY|  
|HAVING|UNION|  
|FOR|GROUP BY|  
|TOP|OPTION \(hint\)|  
  
### Additional Transact\-SQL Statements That Are Supported  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that are shown in the following table.  
  
|Transact\-SQL statement|Syntax supported|Exceptions|  
|-----------------------------|----------------------|----------------|  
|[INSERT](../Topic/INSERT%20\(Transact-SQL\).md)|All syntax, except the *execute\_statement* clause.|None|  
|[UPDATE](../Topic/UPDATE%20\(Transact-SQL\).md)|All syntax.|None|  
|[DELETE](../Topic/DELETE%20\(Transact-SQL\).md)|All syntax.|None|  
|[DECLARE @local\_variable](../Topic/DECLARE%20@local_variable%20\(Transact-SQL\).md)|All syntax.|None|  
|[SET @local\_variable](../Topic/SET%20@local_variable%20\(Transact-SQL\).md)|All syntax.|None|  
|[EXECUTE](../Topic/EXECUTE%20\(Transact-SQL\).md)|Execution of user\-defined stored procedures, system stored procedures, user\-defined functions, and system functions.|None|  
|[CREATE TABLE](../Topic/CREATE%20TABLE%20\(Transact-SQL\).md)|All syntax.|None|  
|[CREATE VIEW](../Topic/CREATE%20VIEW%20\(Transact-SQL\).md)|All syntax.|None|  
|[CREATE PROCEDURE](../Topic/CREATE%20PROCEDURE%20\(Transact-SQL\).md)|All syntax.|There is no IntelliSense support for the EXTERNAL NAME clause.<br /><br /> In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.|  
|[ALTER PROCEDURE](../Topic/ALTER%20PROCEDURE%20\(Transact-SQL\).md)|All syntax|There is no IntelliSense support for the EXTERNAL NAME clause.<br /><br /> In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.|  
|[USE](../Topic/USE%20\(Transact-SQL\).md)|All syntax.|None|  
  
## IntelliSense in Supported Statements  
 IntelliSense in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements:  
  
-   All join types, including APPLY  
  
-   PIVOT and UNPIVOT  
  
-   References to the following database objects:  
  
    -   Databases and schemas  
  
    -   Tables, views, table\-valued functions, and table expressions  
  
    -   Columns  
  
    -   Procedures and procedure parameters  
  
    -   Scalar functions and scalar expressions  
  
    -   Local variables  
  
    -   Common table expressions \(CTE\)  
  
-   Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run. These objects are as follows:  
  
    -   Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.  
  
    -   Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.  
  
    > [!NOTE]  
    >  IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.  
  
 IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements. For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.  
  
## Examples  
 Within a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Query Editor supports only the statements and syntax that are listed in this topic. The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] code examples show what statements and syntax elements IntelliSense supports. For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.  
  
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
  
 This functionality also applies to the sets of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.  
  
 Within a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed. For example, you might enter the following code in the Query Editor:  
  
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
  
  