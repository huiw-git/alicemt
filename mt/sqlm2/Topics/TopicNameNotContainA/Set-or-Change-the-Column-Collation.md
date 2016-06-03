---
title: Set or Change the Column Collation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
---
# Set or Change the Column Collation
  You can override the database collation for **char**, **varchar**, **text**, **nchar**, **nvarchar**, and **ntext** data by specifying a different collation for a specific column of a table and using one of the following:  
  
-   The COLLATE clause of [CREATE TABLE](../Topic/CREATE%20TABLE%20\(Transact-SQL\).md) and [ALTER TABLE](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md). For example:  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information, [Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md).  
  
-   Using the **Column.Collation** property in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Objects \(SMO\).  
  
 You cannot change the collation of a column that is currently referenced by any one of the following:  
  
-   A computed column  
  
-   An index  
  
-   Distribution statistics, either generated automatically or by the CREATE STATISTICS statement  
  
-   A CHECK constraint  
  
-   A FOREIGN KEY constraint  
  
 When you work with **tempdb**, the [COLLATE](../Topic/COLLATE%20\(Transact-SQL\).md) clause includes a *database\_default* option to specify that a column in a temporary table uses the collation default of the current user database for the connection instead of the collation of **tempdb**.  
  
## Collations and text Columns  
 You can insert or update values in a **text** column whose collation is different from the code page of the default collation of the database. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] implicitly converts the values to the collation of the column.  
  
## Collations and tempdb  
 The **tempdb** database is built every time [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started and has the same default collation as the **model** database. This is typically the same as the default collation of the instance. If you create a user database and specify a different default collation than **model**, the user database has a different default collation than **tempdb**. All temporary stored procedures or temporary tables are created and stored in **tempdb**. This means that all implicit columns in temporary tables and all coercible\-default constants, variables, and parameters in temporary stored procedures have collations that are different from comparable objects created in permanent tables and stored procedures.  
  
 This could lead to problems with a mismatch in collations between user\-defined databases and system database objects. For example, an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the Latin1\_General\_CS\_AS collation and you execute the following statements:  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 In this system, the **tempdb** database uses the Latin1\_General\_CS\_AS collation with code page 1252, and `TestDB` and `TestPermTab.Col1` use the `Estonian_CS_AS` collation with code page 1257. For example:  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 With the previous example, the **tempdb** database uses the Latin1\_General\_CS\_AS collation, and `TestDB` and `TestTab.Col1` use the `Estonian_CS_AS` collation. For example:  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Because **tempdb** uses the default server collation and `TestPermTab.Col1` uses a different collation, SQL Server returns this error: "Cannot resolve collation conflict between 'Latin1\_General\_CI\_AS\_KS\_WS' and 'Estonian\_CS\_AS' in equal to operation."  
  
 To prevent the error, you can use one of the following alternatives:  
  
-   Specify that the temporary table column use the default collation of the user database, not **tempdb**. This enables the temporary table to work with similarly formatted tables in multiple databases, if that is required of your system.  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   Specify the correct collation for the `#TestTempTab` column:  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## See Also  
 [Set or Change the Server Collation](../../Topics\TopicNameNotContainA/Set-or-Change-the-Server-Collation.md)   
 [Set or Change the Database Collation](../../Topics\TopicNameNotContainA/Set-or-Change-the-Database-Collation.md)   
 [Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md)  
  
  