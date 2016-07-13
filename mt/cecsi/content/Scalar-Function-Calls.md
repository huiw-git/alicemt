---
title: Scalar Function Calls
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Scalar Function Calls
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Scalar functions return a value for each row. For example, the absolute value scalar function takes a numeric column as an argument and returns the absolute value of each value in the column. The escape sequence for calling a scalar function is</para>
    <para>         <legacyBold>{fn </legacyBold>         <legacyItalic>scalar-function</legacyItalic>         <legacyBold>}</legacyBold>       </para>
    <para>where <legacyItalic>scalar-function</legacyItalic> is one of the functions listed in <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>. For more information about the scalar function escape sequence, see <legacyLink xlink:href="aaf5d516-e090-445f-8839-9e39581c69c7">Scalar Function Escape Sequence</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>For example, the following SQL statements create the same result set of uppercase customer names. The first statement uses the escape-sequence syntax. The second statement uses the native syntax for Ingres for OS/2 and is not interoperable.</para>
    <code>SELECT {fn UCASE(Name)} FROM Customers

SELECT uppercase(Name) FROM Customers</code>
    <para>An application can mix calls to scalar functions that use native syntax and calls to scalar functions that use ODBC syntax. For example, assume that names in the Employee table are stored as a last name, a comma, and a first name. The following SQL statement creates a result set of last names of employees in the Employee table. The statement uses the ODBC scalar function <legacyBold>SUBSTRING</legacyBold> and the SQL Server scalar function <legacyBold>CHARINDEX</legacyBold> and will execute correctly only on SQL Server.</para>
    <code>SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) – 1)} FROM Customers</code>
    <para>For maximum interoperability, applications should use the <legacyBold>CONVERT</legacyBold> scalar function to make sure that the output of a scalar function is the required type. The <legacyBold>CONVERT</legacyBold> function converts data from one SQL data type to the specified SQL data type. The syntax of the <legacyBold>CONVERT</legacyBold> function is</para>
    <para>         <legacyBold>CONVERT(</legacyBold>         <legacyItalic>value_exp</legacyItalic>         <legacyBold>,</legacyBold> <legacyItalic>data_type</legacyItalic><legacyBold>)</legacyBold></para>
    <para>where <legacyItalic>value_exp</legacyItalic> is a column name, the result of another scalar function, or a literal value, and <legacyItalic>data_type</legacyItalic> is a keyword that matches the <legacyBold>#define</legacyBold> name that is used by an SQL data type identifier as defined in <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>. For example, the following SQL statement uses the <legacyBold>CONVERT</legacyBold> function to make sure that the output of the <legacyBold>CURDATE</legacyBold> function is a date, instead of a timestamp or character data:</para>
    <code>INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)</code>
    <para>To determine which scalar functions are supported by a data source, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS, and SQL_TIMEDATE_FUNCTIONS options. To determine which conversion operations are supported by the <legacyBold>CONVERT</legacyBold> function, an application calls <legacyBold>SQLGetInfo</legacyBold> with any of the options that start with SQL_CONVERT.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>