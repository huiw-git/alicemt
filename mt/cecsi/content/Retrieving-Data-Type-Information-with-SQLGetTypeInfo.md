---
title: "Retrieving Data Type Information with SQLGetTypeInfo"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving Data Type Information with SQLGetTypeInfo
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Because the mappings from underlying SQL data types to ODBC type identifiers are approximate, ODBC provides a function (<legacyBold>SQLGetTypeInfo</legacyBold>) through which a driver can completely describe each SQL data type in the data source. This function returns a result set, each row of which describes the characteristics of a single data type, such as name, type identifier, precision, scale, and nullability.</para>
    <para>This information generally is used by generic applications that allow the user to create and alter tables. Such applications call <legacyBold>SQLGetTypeInfo</legacyBold> to retrieve the data type information and then present some or all of it to the user. Such applications need to be aware of two things:  </para>
    <list class="bullet">
      <listItem>
        <para>More than one SQL data type can map to a single type identifier, which can make it difficult to determine which data type to use. To solve this, the result set is ordered first by type identifier and second by closeness to the type identifier's definition. In addition, data source–defined data types take precedence over user-defined data types. For example, suppose that a data source defines the INTEGER and COUNTER data types to be the same except that COUNTER is auto-incrementing. Suppose also that the user-defined type WHOLENUM is a synonym of INTEGER. Each of these types maps to SQL_INTEGER. In the <legacyBold>SQLGetTypeInfo</legacyBold> result set, INTEGER appears first, followed by WHOLENUM and then COUNTER. WHOLENUM appears after INTEGER because it is user-defined, but before COUNTER because it more closely matches the definition of the SQL_INTEGER type identifier.</para>
      </listItem>
      <listItem>
        <para>ODBC does not define data type names for use in <legacyBold>CREATE TABLE</legacyBold> and <legacyBold>ALTER TABLE</legacyBold> statements. Instead, the application should use the name returned in the TYPE_NAME column of the result set returned by <legacyBold>SQLGetTypeInfo</legacyBold>. The reason for this is that although most of SQL does not vary much across DBMSs, data type names vary tremendously. Rather than forcing drivers to parse SQL statements and replace standard data type names with DBMS-specific data type names, ODBC requires applications to use the DBMS-specific names in the first place.</para>
      </listItem>
    </list>
    <para>Note that <legacyBold>SQLGetTypeInfo</legacyBold> does not necessarily describe all of the data types an application can encounter. In particular, result sets might contain data types not directly supported by the data source. For example, the data types of the columns in result sets returned by catalog functions are defined by ODBC and these data types might not be supported by the data source. To determine the characteristics of the data types in a result set, an application calls <legacyBold>SQLColAttribute</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>