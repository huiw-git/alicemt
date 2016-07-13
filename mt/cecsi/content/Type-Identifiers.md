---
title: Type Identifiers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Type Identifiers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To describe SQL and C data types, ODBC defines two sets of <legacyItalic>type identifiers</legacyItalic>. A type identifier describes the type of an SQL column or a C buffer. It is a <legacyBold>#define</legacyBold> value and is generally passed as a function argument or returned in metadata. </para>
    <para>For example, the following call to <legacyBold>SQLBindParameter</legacyBold> binds a variable of type SQL_DATE_STRUCT to a date parameter in an SQL statement. The C type identifier SQL_C_TYPE_DATE specifies the type of the <legacyItalic>Date</legacyItalic> variable, and the SQL type identifier SQL_TYPE_DATE specifies the type of the dynamic parameter.</para>
    <code>SQL_DATE_STRUCT Date;
SQLINTEGER  DateInd = 0;
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,
                  &amp;Date, 0, &amp;DateInd);</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>