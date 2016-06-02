---
title: Supported Features for Natively Compiled T-SQL Modules
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
---
# Supported Features for Natively Compiled T-SQL Modules
  This topic contains a list of T\-SQL surface area and supported features in the body of natively compiled T\-SQL modules, such as stored procedures \([CREATE PROCEDURE &#40;Transact-SQL&#41;](../Topic/CREATE%20PROCEDURE%20\(Transact-SQL\).md)\), scalar user\-defined functions, inline table\-valued functions, and triggers.  
  
 For supported features around the definition of native modules, see [Supported DDL for Natively Compiled T-SQL modules](../../Topics\TopicNameNotContainA/Supported-DDL-for-Natively-Compiled-T-SQL-modules.md).  
  
-   [Query Surface Area in Native Modules](#qsancsp)  
  
-   [Data Modification](#dml)  
  
-   [Control-of-flow language](#cof)  
  
-   [Supported Operators](#so)  
  
-   [Built-in Functions in Natively Compiled Modules](#bfncsp)  
  
-   [Auditing](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md)  
  
-   [Table and Query Hints](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md)  
  
-   [Limitations on Sorting](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md)  
  
 For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled modules, see [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md). For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md).  
  
##  <a name="qsancsp"></a> Query Surface Area in Native Modules  

The following query constructs are supported:  
  
SELECT clause:  
  
-   Columns and  name aliases \(using either AS or \= syntax\).  
  
-   Scalar subqueries  
  
-   TOP\*  
  
-   SELECT DISTINCT  
  
    DISTINCT aggregates are not supported.  

- UNION and UNION ALL

-   Variable assignments  
  
FROM clause:  
  
-   FROM \<memory optimized table or table variable\>  
  
-   FROM \<natively compiled inline TVF\>  
  
-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN and INNER JOIN.  
  
-   Subqueries `[AS] table_alias`. For more information, see [FROM &#40;Transact-SQL&#41;](../Topic/FROM%20\(Transact-SQL\).md).  
  
WHERE clause:  
  
-   Filter predicate IS \[NOT\] NULL  
  
-   AND, OR, NOT, IN, EXISTS, BETWEEN  


[GROUP BY](../Topic/GROUP%20BY%20%28Transact-SQL%29.md) clause:

- Aggregate functions AVG, COUNT, COUNT\_BIG, MIN, MAX, and SUM.  

- MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.  

[ORDER BY](../Topic/ORDER%20BY%20Clause%20%28Transact-SQL%29.md) clause:


- There is no support for **DISTINCT** in the **ORDER BY** clause.


- Is supported with [GROUP BY &#40;Transact-SQL&#41;](../Topic/GROUP%20BY%20\(Transact-SQL\).md) if an expression in the ORDER BY list appears verbatim in the GROUP BY list.
  - For example, GROUP BY a \+ b ORDER BY a \+ b is supported, but GROUP BY a, b ORDER BY a \+ b is not.  


HAVING clause:

- Is subject to the same expression limitations as the WHERE clause.


#### ORDER BY and TOP are supported in natively compiled modules, with some restrictions


- There is no support for **WITH TIES** or **PERCENT** in the **TOP** clause.


- There is no support for **DISTINCT** in the **ORDER BY** clause.  


- **TOP** combined with **ORDER BY** does not support more than 8,192 when using a constant in the **TOP** clause.
  - This limit may be lowered in case the query contains joins or aggregate functions. \(For example, with one join \(two tables\), the limit is 4,096 rows. With two joins \(three tables\), the limit is 2,730 rows.\)  
  - You can obtain results greater than 8,192 by storing the number of rows in a variable:  

```tsql
DECLARE @v INT = 9000;
SELECT TOP (@v) … FROM … ORDER BY …
```

However, a constant in the **TOP** clause results in better performance compared to using a variable.  

These restrictions on natively compiled [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] do not apply to interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access on memory\-optimized tables.  

  
##  <a name="dml"></a> Data Modification  

The following DML statements are supported.  
  
-   INSERT VALUES \(one row per statement\) and INSERT ... SELECT  
  
-   UPDATE  
  
-   DELETE  
  
-   WHERE is supported with UPDATE and DELETE statements.  
  
##  <a name="cof"></a> Control\-of\-flow language  
 The following control\-of\-flow language constructs are supported.  
  
-   [IF...ELSE &#40;Transact-SQL&#41;](../Topic/IF...ELSE%20\(Transact-SQL\).md)  
  
-   [WHILE &#40;Transact-SQL&#41;](../Topic/WHILE%20\(Transact-SQL\).md)  
  
-   [RETURN &#40;Transact-SQL&#41;](../Topic/RETURN%20\(Transact-SQL\).md)  
  
-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../Topic/DECLARE%20@local_variable%20\(Transact-SQL\).md) can use all [Supported Data Types for In-Memory OLTP](../../Topics\TopicNameNotContainA/Supported-Data-Types-for-In-Memory-OLTP.md), as well as memory\-optimized table types. Variables can be declared as NULL or NOT NULL.  
  
-   [SET @local_variable &#40;Transact-SQL&#41;](../Topic/SET%20@local_variable%20\(Transact-SQL\).md)  
  
-   [TRY...CATCH &#40;Transact-SQL&#41;](../Topic/TRY...CATCH%20\(Transact-SQL\).md)  
  
     To achieve optimal performance, use a single TRY\/CATCH block for an entire natively compiled T\-SQL module.  
  
-   [THROW &#40;Transact-SQL&#41;](../Topic/THROW%20\(Transact-SQL\).md)  
  
-   BEGIN ATOMIC \(at the outer level of the stored procedure\). For more detail see [Atomic Blocks](../../Topics\TopicNameNotContainA/Atomic-Blocks.md).  
  
##  <a name="so"></a> Supported Operators  
 The following operators are supported.  
  
-   [Comparison Operators &#40;Transact-SQL&#41;](../Topic/Comparison%20Operators%20\(Transact-SQL\).md) \(for example, \>, \<, \>\=, and \<\=\)  
  
-   Unary operators \(\+, \-\).  
  
-   Binary operators \(\*, \/, \+, \-, % \(modulo\)\).  
  
     The plus operator \(\+\) is supported on both numbers and strings.  
  
-   Logical operators \(AND, OR, NOT\).  
  
-   Bitwise operators ~, &, |, and ^  
  
##  <a name="bfncsp"></a> Built\-in Functions in Natively Compiled Modules  
 The following functions are supported in constraints on memory\-optimized tables and in natively compiled T\-SQL modules.  
  
-   All [Mathematical Functions &#40;Transact-SQL&#41;](../Topic/Mathematical%20Functions%20\(Transact-SQL\).md)  
  
-   Date functions: CURRENT\_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.  
  
-   String functions: LEN, LTRIM, RTRIM, and SUBSTRING  
  
-   Identity functions: SCOPE\_IDENTITY  
  
-   NULL functions: ISNULL  
  
-   Uniqueidentifier functions: NEWID and NEWSEQUENTIALID  
  
-   Error functions: ERROR\_LINE, ERROR\_MESSAGE, ERROR\_NUMBER, ERROR\_PROCEDURE, ERROR\_SEVERITY, and ERROR\_STATE  
  
-   System Functions: @@rowcount. Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure. However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.  
  
-   Security functions: IS\_MEMBER\({'group' | 'role'}\), IS\_ROLEMEMBER \('role' \[, 'database\_principal'\]\), IS\_SRVROLEMEMBER \('role' \[, 'login'\]\), ORIGINAL\_LOGIN\(\), SESSION\_USER, CURRENT\_USER, SUSER\_ID\(\['login'\]\), SUSER\_SID\(\['login'\] \[, Param2\]\), SUSER\_SNAME\(\[server\_user\_sid\]\), SYSTEM\_USER, SUSER\_NAME, USER, USER\_ID\(\['user'\]\), USER\_NAME\(\[id\]\), CONTEXT\_INFO\(\).

- Executions of native modules can be nested.
  
##  <a name="auditing"></a> Auditing  
 Procedure level auditing is supported in natively compiled stored procedures.  
  
 For more information about auditing, see [Create a Server Audit and Database Audit Specification](../../Topics\TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md).  
  
##  <a name="tqh"></a> Table and Query Hints  
 The following are supported:  
  
-   INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause &#40;Transact-SQL&#41;](../Topic/OPTION%20Clause%20\(Transact-SQL\).md) of the query. For more information, see [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  
  
-   FORCE ORDER  
  
-   LOOP JOIN hint  
  
-   OPTIMIZE FOR  
  
 For more information, see [Query Hints &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).  
  
##  <a name="los"></a> Limitations on Sorting  
 You can sort greater than 8,000 rows in a query that uses [TOP &#40;Transact-SQL&#41;](../Topic/TOP%20\(Transact-SQL\).md) and an [ORDER BY Clause &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md). However, without [ORDER BY Clause &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), [TOP &#40;Transact-SQL&#41;](../Topic/TOP%20\(Transact-SQL\).md) can sort up to 8,000 rows \(fewer rows if there are joins\).  
  
 If your query uses both the [TOP &#40;Transact-SQL&#41;](../Topic/TOP%20\(Transact-SQL\).md) operator and an [ORDER BY Clause &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), you can specify up to 8192 rows for the TOP operator. If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *\<procedureName\>*, Line *\<lineNumber\>* The TOP operator can return a maximum of 8192 rows; *\<number\>* was requested.**  
  
 If you do not have a TOP clause, you can sort any number of rows with ORDER BY.  
  
 If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.  
  
 Example with TOP N \= 8192: Compiles  
  
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
  
 Example with TOP N \> 8192: Fails to compile.  
  
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
 [Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)   
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)  
  
  