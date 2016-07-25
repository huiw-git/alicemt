---
title: "SQL Type Identifiers"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Type Identifiers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each data source defines its own SQL data types. ODBC defines type identifiers and describes the general characteristics of the SQL data types that might be mapped to each type identifier. It is driver-specific how each data type in the underlying data source is mapped to an SQL type identifier of ODBC.</para>
    <para>For example, SQL_CHAR is the type identifier for a character column with a fixed length, typically between 1 and 254 characters. These characteristics correspond to the CHAR data type found in many SQL data sources. Thus, when an application discovers that the type identifier for a column is SQL_CHAR, it can assume it is probably dealing with a CHAR column. However, it should still check the byte length of the column before assuming it is between 1 and 254 characters; the driver for a non-SQL data source, for example, might map a fixed-length character column of 500 characters to SQL_CHAR or SQL_LONGVARCHAR, because neither is an exact match.</para>
    <para>ODBC defines a wide variety of SQL type identifiers. However, the driver is not required to use all of these identifiers. Instead, it uses only those identifiers it needs to expose the SQL data types supported by the underlying data source. If the underlying data source supports SQL data types to which no type identifier corresponds, the driver can define additional type identifiers. For more information, see <legacyLink xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</legacyLink>.</para>
    <para>For a complete description of SQL type identifiers, see <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> in Appendix D: Data Types.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>