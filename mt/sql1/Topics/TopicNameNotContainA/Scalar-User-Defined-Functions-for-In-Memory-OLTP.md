---
title: "Scalar User-Defined Functions for In-Memory OLTP"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2546e40-fdfc-414b-8196-76ed1f124bf5
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Scalar User-Defined Functions for In-Memory OLTP
In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], you can create and drop natively compiled, scalar user-defined functions. You can also alter these user-defined functions. Native compilation improves performance of the evaluation of user-defined functions in Transact-SQL.  
  
 When you alter a natively compiled, scalar user-defined function, the application remains available while the operation is being run and the new version of the function is being compiled.  
  
 For supported T-SQL constructs, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md).  
  
## Creating, Dropping, and Altering User-Defined Functions  
 You use the CREATE FUNCTION to create the natively compiled, scalar user-defined function, the DROP FUNCTION to remove the user-defined function, and the ALTER FUNCTION to change the function. BEGIN ATOMIC WITH is required for the user-defined functions.  
  
 For information about the supported syntax and any restrictions, see the following topics.  
  
-   [CREATE FUNCTION (Transact-SQL)](assetId:///864b393f-225f-4895-8c8d-4db59ea60032)  
  
-   [ALTER FUNCTION (Transact-SQL)](assetId:///89f066ee-05ac-4439-ab04-d8c3d5911179)  
  
-   [DROP FUNCTION (Transact-SQL)](assetId:///ee5ad283-9e44-4109-902f-0ce12669ee11)  
  
     The DROP FUNCTION syntax for natively compiled, scalar user-defined functions is the same as for interpreted user-defined functions.  
  
-   [EXECUTE (Transact-SQL)](assetId:///bc806b71-cc55-470a-913e-c5f761d5c4b7)  
  
 The [sp_recompile (Transact-SQL)](assetId:///6192ca87-febd-4075-8199-14b4fa609b8c)stored procedure can be used with the natively compiled, scalar user-defined function. It will result in the function being recompiled using the definition that exists in metadata.  
  
 The following sample shows a scalar UDF from the [AdventureWorks2016CTP3](https://www.microsoft.com/download/details.aspx?id=49502) sample database.  
  
```tsql  
CREATE FUNCTION [dbo].[ufnLeadingZeros_native](@Value int)   
RETURNS varchar(8)   
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS   
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
  
    DECLARE @ReturnValue varchar(8);  
    SET @ReturnValue = CONVERT(varchar(8), @Value);  
	   DECLARE @i int = 0, @count int = 8 - LEN(@ReturnValue)  
  
   	WHILE @i < @count  
	   BEGIN  
		    SET @ReturnValue = '0' + @ReturnValue;  
		    SET @i += 1  
	   END  
  
    RETURN (@ReturnValue);  
  
END  
```  
  
## Calling User-Defined Functions  
 Natively compiled, scalar user-defined functions can be used in expressions, in the same place as built-in scalar functions and interpreted scalar user-defined functions. Natively compiled, scalar user-defined functions can also be used with the EXECUTE statement, in a Transact-SQL statement and in a natively compiled stored procedure.  
  
 You can use these scalar user-defined functions in natively compiled store procedures and natively compiled user-defined functions, and wherever built-in functions are permitted. You can also use natively compiled, scalar user-defined functions in traditional Transact-SQL modules.  
  
 You can use these scalar user-defined functions in interop mode, wherever an interpreted scalar user-defined function can be used. This use is subject to cross-container transaction limitations, as described in **Supported Isolation Levels for Cross-Container Transactions** section in [Transactions with Memory-Optimized Tables](../../Topics/TopicNameNotContainA/Transactions-with-Memory-Optimized-Tables.md). For more information about interop mode, see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](../../Topics/TopicNameNotContainA/Accessing-Memory-Optimized-Tables-Using-Interpreted-Transact-SQL.md).  
  
 Natively compiled, scalar user-defined functions do require an explicit execution context. For more information, see [EXECUTE AS Clause (Transact-SQL)](assetId:///bd517aa3-f06e-4356-87d8-70de5df4494a). EXECUTE AS CALLER is not supported. For more information, see [EXECUTE (Transact-SQL)](assetId:///bc806b71-cc55-470a-913e-c5f761d5c4b7).  
  
 For the supported syntax for Transact-SQL Execute statements, for natively compiled, scalar user-defined functions, see [EXECUTE (Transact-SQL)](assetId:///bc806b71-cc55-470a-913e-c5f761d5c4b7). For the supported syntax for executing the user-defined functions in a natively compiled stored procedure, see [Supported Features for Natively Compiled T-SQL Modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md).  
  
## Hints and Parameters  
 Support for table, join, and query hints inside natively compiled, scalar user-defined functions is equal to support for these hints for natively compiled stored procedures. As with interpreted scalar user-defined functions, the query hints included with a Transact-SQL query that reference a natively compiled, scalar user-defined function do not impact the query plan for this user-defined function.  
  
 The parameters supported for the natively compiled, scalar user-defined functions are all the parameters supported for natively compiled stored procedures, as long as the parameters are allowed for scalar user-defined functions. An example of a supported parameter is the table-valued parameter.  
  
## Schema-Bound  
 The following apply to natively compiled, scalar user-defined functions.  
  
-   Must be schema-bound, by using the WITH SCHEMABINDING argument in the CREATE FUNCTION and ALTER FUNCTION.  
  
-   Cannot be dropped or altered when referenced by a schema-bound stored procedure or user-defined function.  
  
## SHOWPLAN_XML  
 Natively compiled, scalar user-defined functions support SHOWPLAN_XML. It conforms to the general SHOWPLAN_XML schema, as with natively compiled stored procedures. The base element for the user-defined functions is `<UDF>`.  
  
 STATISTICS XML is not supported for natively compiled, scalar user-defined functions. When you run a query referencing the user-defined function, with STATISTICS XML enabled, the XML content is returned without the part for the user-defined function.  
  
## Permissions  
 As with natively compiled stored procedures, the permissions for objects referenced from a natively compiled, scalar user-defined function are checked when the function is created. The CREATE FUNCTION fails if the impersonated user does not have the correct permissions. If permission changes result in the impersonated user no longer having the correct permissions, subsequent executions of the user-defined function fail.  
  
 When you use a natively compiled, scalar user-defined function inside a natively compiled stored procedure, the permissions for executing the user-defined function are checked when the outer procedure is created. If the user impersonated by the outer procedure does not have EXEC permissions for the user-defined function, the creation of the stored procedure fails. If permission changes result in the user no longer having the EXEC permissions, the execution of the outer procedure fails.  
  
## See Also  
 [Built-in Functions (Transact-SQL)](assetId:///17186213-5ab5-40b0-b470-b660af1ec44c)   
 [Save an Execution Plan in XML Format](../../Topics/TopicNameNotContainA/Save-an-Execution-Plan-in-XML-Format.md)