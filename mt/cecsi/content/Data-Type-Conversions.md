---
title: Data Type Conversions
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Type Conversions
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data can be converted from one type to another at one of four times: when data is transferred from one application variable to another (C to C), when data in an application variable is sent to a statement parameter (C to SQL), when data in a result set column is returned in an application variable (SQL to C), and when data is transferred from one data source column to another (SQL to SQL).</para>
    <para>Any conversion that occurs when data is transferred from one application variable to another is outside the scope of this document.</para>
    <para>When an application binds a variable to a result set column or statement parameter, the application implicitly specifies a data type conversion in its choice of the data type of the application variable. For example, suppose a column contains integer data. If the application binds an integer variable to the column, it specifies that no conversion be done; if the application binds a character variable to the column, it specifies that the data be converted from integer to character.</para>
    <para>ODBC defines how data is converted between each SQL and C data type. Basically, ODBC supports all reasonable conversions, such as character to integer and integer to float, and does not support ill-defined conversions, such as float to date. Drivers are required to support all conversions for each SQL data type they support. For a complete list of conversions between SQL and C data types, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink> and <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink> in Appendix D: Data Types.</para>
    <para>ODBC also defines a scalar function for converting data from one SQL data type to another. The <legacyBold>CONVERT</legacyBold> scalar function is mapped by the driver to the underlying scalar function or functions defined to perform conversions in the data source. Because this function is mapped to DBMS-specific functions, ODBC does not define how these conversions work or what conversions must be supported. An application discovers what conversions are supported by a particular driver and data source through the SQL_CONVERT options in <legacyBold>SQLGetInfo</legacyBold>. For more information about the <legacyBold>CONVERT</legacyBold> scalar function, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink> and <legacyLink xlink:href="d5789450-b668-4753-96c8-6789e955e7ed">Explicit Data Type Conversion Function</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>