---
title: Indexes on Computed Columns
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
---
# Indexes on Computed Columns
  You can define indexes on computed columns as long as the following requirements are met:  
  
-   Ownership requirements  
  
-   Determinism requirements  
  
-   Precision requirements  
  
-   Data type requirements  
  
-   SET option requirements  
  
 **Ownership Requirements**  
  
 All function references in the computed column must have the same owner as the table.  
  
 **Determinism Requirements**  
  
> [!IMPORTANT]  
>  Expressions are deterministic if they always return the same result for a specified set of inputs. The **IsDeterministic** property of the [COLUMNPROPERTY](../Topic/COLUMNPROPERTY%20\(Transact-SQL\).md) function reports whether a *computed\_column\_expression* is deterministic.  
  
 The *computed\_column\_expression* must be deterministic. A *computed\_column\_expression* is deterministic when one or more of the following is true:  
  
-   All functions that are referenced by the expression are deterministic and precise. These functions include both user\-defined and built\-in functions. For more information, see [Deterministic and Nondeterministic Functions](../../Topics\TopicNameNotContainA/Deterministic-and-Nondeterministic-Functions.md). Functions might be imprecise if the computed column is PERSISTED. For more information, see [Creating Indexes on Persisted Computed Columns](#BKMK_persisted) later in this topic.  
  
-   All columns that are referenced in the expression come from the table that contains the computed column.  
  
-   No column reference pulls data from multiple rows. For example, aggregate functions such as SUM or AVG depend on data from multiple rows and would make a *computed\_column\_expression* nondeterministic.  
  
-   The *computed\_column\_expression* has no system data access or user data access.  
  
 Any computed column that contains a common language runtime \(CLR\) expression must be deterministic and marked PERSISTED before the column can be indexed. CLR user\-defined type expressions are allowed in computed column definitions. Computed columns whose type is a CLR user\-defined type can be indexed as long as the type is comparable. For more information, see [CLR User-Defined Types](../Topic/CLR%20User-Defined%20Types.md).  
  
> [!NOTE]  
>  When you refer to string literals of the date data type in indexed computed columns in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], we recommend that you explicitly convert the literal to the date type that you want by using a deterministic date format style. For a list of the date format styles that are deterministic, see [CAST and CONVERT](../Topic/CAST%20and%20CONVERT%20\(Transact-SQL\).md). Expressions that involve implicit conversion of character strings to date data types are considered nondeterministic, unless the database compatibility level is set to 80 or earlier. This is because the results depend on the [LANGUAGE](../Topic/SET%20LANGUAGE%20\(Transact-SQL\).md) and [DATEFORMAT](../Topic/SET%20DATEFORMAT%20\(Transact-SQL\).md) settings of the server session. For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`30 listopad 1996`' means different months in different languages. Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.  
>   
>  Implicit conversion of non\-Unicode character data between collations is also considered nondeterministic, unless the compatibility level is set to 80 or earlier.  
>   
>  When the database compatibility level setting is 90, you cannot create indexes on computed columns that contain these expressions. However, existing computed columns that contain these expressions from an upgraded database are maintainable. If you use indexed computed columns that contain implicit string to date conversions, to avoid possible index corruption, make sure that the LANGUAGE and DATEFORMAT settings are consistent in your databases and applications.  
  
 **Precision Requirements**  
  
 The *computed\_column\_expression* must be precise. A *computed\_column\_expression* is precise when one or more of the following is true:  
  
-   It is not an expression of the **float** or **real** data types.  
  
-   It does not use a **float** or **real** data type in its definition. For example, in the following statement, column `y` is **int** and deterministic but not precise.  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  Any **float** or **real** expression is considered imprecise and cannot be a key of an index; a **float** or **real** expression can be used in an indexed view but not as a key. This is true also for computed columns. Any function, expression, or user\-defined function is considered imprecise if it contains any **float** or **real** expressions. This includes logical ones \(comparisons\).  
  
 The **IsPrecise** property of the COLUMNPROPERTY function reports whether a *computed\_column\_expression* is precise.  
  
 **Data Type Requirements**  
  
-   The *computed\_column\_expression* defined for the computed column cannot evaluate to the **text**, **ntext**, or **image** data types.  
  
-   Computed columns derived from **image**, **ntext**, **text**, **varchar\(max\)**, **nvarchar\(max\)**, **varbinary\(max\)**, and **xml** data types can be indexed as long as the computed column data type is allowable as an index key column.  
  
-   Computed columns derived from **image**, **ntext**, and **text** data types can be nonkey \(included\) columns in a nonclustered index as long as the computed column data type is allowable as a nonkey index column.  
  
 **SET Option Requirements**  
  
-   The ANSI\_NULLS connection\-level option must be set to ON when the CREATE TABLE or ALTER TABLE statement that defines the computed column is executed. The [OBJECTPROPERTY](../Topic/OBJECTPROPERTY%20\(Transact-SQL\).md) function reports whether the option is on through the **IsAnsiNullsOn** property.  
  
-   The connection on which the index is created, and all connections trying INSERT, UPDATE, or DELETE statements that will change values in the index, must have six SET options set to ON and one option set to OFF. The optimizer ignores an index on a computed column for any SELECT statement executed by a connection that does not have these same option settings.  
  
    -   The NUMERIC\_ROUNDABORT option must be set to OFF, and the following options must be set to ON:  
  
    -   ANSI\_NULLS  
  
    -   ANSI\_PADDING  
  
    -   ANSI\_WARNINGS  
  
    -   ARITHABORT  
  
    -   CONCAT\_NULL\_YIELDS\_NULL  
  
    -   QUOTED\_IDENTIFIER  
  
     Setting ANSI\_WARNINGS to ON implicitly sets ARITHABORT to ON when the database compatibility level is set to 90 or higher.  
  
##  <a name="BKMK_persisted"></a> Creating Indexes on Persisted Computed Columns  
 You can create an index on a computed column that is defined with a deterministic, but imprecise, expression if the column is marked PERSISTED in the CREATE TABLE or ALTER TABLE statement. This means that the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] stores the computed values in the table, and updates them when any other columns on which the computed column depends are updated. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] uses these persisted values when it creates an index on the column, and when the index is referenced in a query. This option enables you to create an index on a computed column when [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] cannot prove with accuracy whether a function that returns computed column expressions, particularly a CLR function that is created in the [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)], is both deterministic and precise.  
  
## Related Content  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](../Topic/COLUMNPROPERTY%20\(Transact-SQL\).md)  
  
  