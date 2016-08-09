---
title: "Supported Features for Natively Compiled T-SQL Modules"
ms.custom: na
ms.date: 2016-06-01
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 43
caps.handback.revision: 0
manager: jhubbard
---
# Supported Features for Natively Compiled T-SQL Modules
This topic contains a list of T-SQL surface area and supported features in the body of natively compiled T-SQL modules, such as stored procedures ([CREATE PROCEDURE (Transact-SQL)](assetId:///afe3d86d-c9ab-44e4-b74d-4e3dbd9cc58c)), scalar user-defined functions, inline table-valued functions, and triggers.  
  
 For supported features around the definition of native modules, see [Supported DDL for Natively Compiled T-SQL modules](../../Topics/TopicNameNotContainA/Supported-DDL-for-Natively-Compiled-T-SQL-modules.md).  
  
-   [Query Surface Area in Native Modules](#qsancsp)  
  
-   [Data Modification](#dml)  
  
-   [Control-of-flow language](#cof)  
  
-   [Supported Operators](#so)  
  
-   [Built-in Functions in Natively Compiled Modules](#bfncsp)  
  
-   [Auditing](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#auditing)  
  
-   [Table and Query Hints](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#tqh)  
  
-   [Limitations on Sorting](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#los)  
  
 For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled modules, see [Migration Issues for Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md). For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
##  <a name="qsancsp"></a> Query Surface Area in Native Modules  
 The following query constructs are supported:  
  
 SELECT clause:  
  
-   Columns and  name aliases (using either AS or = syntax).  
  
-   Scalar subqueries  
  
-   TOP*  
  
-   SELECT DISTINCT  
  
     DISTINCT aggregates are not supported.  
  
-   Variable assignments  
  
 FROM clause:  
  
-   FROM <memory optimized table or table variable\>  
  
-   FROM <natively compiled inline TVF\>  
  
-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN and INNER JOIN.  
  
-   Subqueries `[AS] table_alias`. For more information, see [FROM (Transact-SQL)](assetId:///36b19e68-94f6-4539-aeb1-79f5312e4263).  
  
 WHERE clause:  
  
-   Filter predicate IS [NOT] NULL  
  
-   AND, OR, NOT, IN, EXISTS, BETWEEN  
  
-   [GROUP BY](assetId:///40075914-6385-4692-b4a5-62fe44ae6cb6) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM.  
  
     MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.  
  
     [ORDER BY Clause (Transact-SQL)](assetId:///bb394abe-cae6-4905-b5c6-8daaded77742) is supported with [GROUP BY](assetId:///40075914-6385-4692-b4a5-62fe44ae6cb6) if an expression in the ORDER BY list appears verbatim in the GROUP BY list. For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.  
  
 [GROUP BY](assetId:///40075914-6385-4692-b4a5-62fe44ae6cb6) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM. MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.   
            [ORDER BY Clause (Transact-SQL)](assetId:///bb394abe-cae6-4905-b5c6-8daaded77742) is supported with [GROUP BY](assetId:///40075914-6385-4692-b4a5-62fe44ae6cb6) if an expression in the ORDER BY list appears verbatim in the GROUP BY list. For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.  
  
 HAVING is supported, subject to the same expression limitations as the WHERE clause.  
  
 *ORDER BY  is supported.  
  
 *ORDER BY and TOP are supported in natively compiled modules, with some restrictions:  
  
-   There is no support for **DISTINCT** in the **ORDER BY** clause.  
  
-   There is no support for **WITH TIES** or **PERCENT** in the **TOP** clause.  
  
-   **TOP** combined with **ORDER BY** does not support more than 8,192 when using a constant in the **TOP** clause. This limit may be lowered in case the query contains joins or aggregate functions. (For example, with one join (two tables), the limit is 4,096 rows. With two joins (three tables), the limit is 2,730 rows.)  
  
     You can obtain results greater than 8,192 by storing the number of rows in a variable:  
  
    ```tsql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) … FROM … ORDER BY …  
    ```  
  
 However, a constant in the **TOP** clause results in better performance compared to using a variable.  
  
 These restrictions do not apply to interpreted [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] access on memory-optimized tables.  
  
##  <a name="dml"></a> Data Modification  
 The following DML statements are supported.  
  
-   INSERT VALUES (one row per statement) and INSERT ... SELECT  
  
-   UPDATE  
  
-   DELETE  
  
-   WHERE is supported with UPDATE and DELETE statements.  
  
##  <a name="cof"></a> Control-of-flow language  
 The following control-of-flow language constructs are supported.  
  
-   [IF...ELSE (Transact-SQL)](assetId:///676c881f-dee1-417a-bc51-55da62398e81)  
  
-   [WHILE (Transact-SQL)](assetId:///52dd29ab-25d7-4fd3-a960-ac55c30c9ea9)  
  
-   [RETURN (Transact-SQL)](assetId:///1d9c8247-fd89-4544-be9c-01c95b745db0)  
  
-   [DECLARE @local_variable (Transact-SQL)](assetId:///d1635ebb-f751-4de1-8bbc-cae161f90821) can use all [Supported Data Types for In-Memory OLTP](../../Topics/TopicNameNotContainA/Supported-Data-Types-for-In-Memory-OLTP.md), as well as memory-optimized table types. Variables can be declared as NULL or NOT NULL.  
  
-   [SET @local_variable (Transact-SQL)](assetId:///d410e06e-061b-4c25-9973-b2dc9b60bd85)  
  
-   [TRY...CATCH (Transact-SQL)](assetId:///248df62a-7334-4bca-8262-235a28f4b07f)  
  
     To achieve optimal performance, use a single TRY/CATCH block for an entire natively compiled T-SQL module.  
  
-   [THROW (Transact-SQL)](assetId:///43661b89-8f13-4480-ad53-70306cbb14c5)  
  
-   BEGIN ATOMIC (at the outer level of the stored procedure). For more detail see [Atomic Blocks](../../Topics/TopicNameNotContainA/Atomic-Blocks.md).  
  
##  <a name="so"></a> Supported Operators  
 The following operators are supported.  
  
-   [Comparison Operators (Transact-SQL)](assetId:///b0cc68ef-3029-484c-a917-0c15dcbc230d) (for example, >, <, >=, and <=)  
  
-   Unary operators (+, -).  
  
-   Binary operators (*, /, +, -, % (modulo)).  
  
     The plus operator (+) is supported on both numbers and strings.  
  
-   Logical operators (AND, OR, NOT).  
  
-   Bitwise operators ~, &, &#124;, and ^  
  
##  <a name="bfncsp"></a> Built-in Functions in Natively Compiled Modules  
 The following functions are supported in constraints on memory-optimized tables and in natively compiled T-SQL modules.  
  
-   All [Mathematical Functions (Transact-SQL)](assetId:///46495a2e-81d0-4677-9d72-9db083cd1023)  
  
-   Date functions: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.  
  
-   String functions: LEN, LTRIM, RTRIM, and SUBSTRING  
  
-   Identity functions: SCOPE_IDENTITY  
  
-   NULL functions: ISNULL  
  
-   Uniqueidentifier functions: NEWID and NEWSEQUENTIALID  
  
-   Error functions: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE  
  
-   System Functions: @@rowcount. Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure. However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.  
  
-   Security functions: IS_MEMBER({'group' &#124; 'role'}), IS_ROLEMEMBER ('role' [, 'database_principal']), IS_SRVROLEMEMBER ('role' [, 'login']), ORIGINAL_LOGIN(), SESSION_USER, CURRENT_USER, SUSER_ID(['login']), SUSER_SID(['login'] [, Param2]), SUSER_SNAME([server_user_sid]), SYSTEM_USER, SUSER_NAME, USER, USER_ID(['user']), USER_NAME([id]), CONTEXT_INFO().  
  
##  <a name="auditing"></a> Auditing  
 Procedure level auditing is supported in natively compiled stored procedures.  
  
 For more information about auditing, see [Create a Server Audit and Database Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md).  
  
##  <a name="tqh"></a> Table and Query Hints  
 The following are supported:  
  
-   INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause (Transact-SQL)](assetId:///f47e2f3f-9302-4711-9d66-16b1a2a7ffe3) of the query. For more information, see [Table Hints (Transact-SQL)](assetId:///8bf1316f-c0ef-49d0-90a7-3946bc8e7a89).  
  
-   FORCE ORDER  
  
-   LOOP JOIN hint  
  
-   OPTIMIZE FOR  
  
 For more information, see [Query Hints (Transact-SQL)](assetId:///66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d).  
  
##  <a name="los"></a> Limitations on Sorting  
 You can sort greater than 8,000 rows in a query that uses [TOP (Transact-SQL)](assetId:///da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c) and an [ORDER BY Clause (Transact-SQL)](assetId:///bb394abe-cae6-4905-b5c6-8daaded77742). However, without [ORDER BY Clause (Transact-SQL)](assetId:///bb394abe-cae6-4905-b5c6-8daaded77742), [TOP (Transact-SQL)](assetId:///da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c) can sort up to 8,000 rows (fewer rows if there are joins).  
  
 If your query uses both the [TOP (Transact-SQL)](assetId:///da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c) operator and an [ORDER BY Clause (Transact-SQL)](assetId:///bb394abe-cae6-4905-b5c6-8daaded77742), you can specify up to 8192 rows for the TOP operator. If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *<procedureName\>*, Line *<lineNumber\>* The TOP operator can return a maximum of 8192 rows; *<number\>* was requested.**  
  
 If you do not have a TOP clause, you can sort any number of rows with ORDER BY.  
  
 If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.  
  
 Example with TOP N = 8192: Compiles  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Example with TOP N > 8192: Fails to compile.  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 The 8192 row limitation only applies to `TOP N` where `N` is a constant, as in the preceding examples.  If you need `N` greater than 8192 you can assign the value to a variable and use that variable with `TOP`.  
  
 Example using a variable: Compiles  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 **Limitations on rows returned:** There are two cases where that can potentially reduce the number of rows that can be returned by the TOP operator:  
  
-   Using JOINs in the query.  The influence of JOINs on the limitation depends on the query plan.  
  
-   Using aggregate functions or references to aggregate functions in the ORDER BY clause.  
  
 The formula to calculate a worst case maximum supported N in TOP N is: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)   
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics/TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)