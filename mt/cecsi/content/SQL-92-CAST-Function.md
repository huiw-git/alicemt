---
title: "SQL-92 CAST Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL-92 CAST Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>CAST</legacyBold> function defined in SQL-92 is equivalent to the <legacyBold>CONVERT</legacyBold> function defined in ODBC. The syntax of the equivalent functions is as follows:</para>
  </introduction>
  <section>
    <content>
      <code>{ fn CONVERT (value-exp, data-type) } /* ODBC
CAST (value-exp AS data-type) /* SQL92</code>
      <para>The SQL-92 <legacyBold>CAST</legacyBold> function mandates which data types can be converted to which other data types. (For more information, see the SQL-92 specification.) The <legacyBold>CAST</legacyBold> function is supported at the FIPS Transitional level.</para>
      <para>An application can determine support for the <legacyBold>CAST</legacyBold> function as follows:

</para>
      <list class="ordered">
        <listItem>
          <para>Call <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL_CONFORMANCE information type. If the return value for the information type is SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE, or SQL_SC_SQL92_FULL, the <legacyBold>CAST</legacyBold> function is supported.</para>
        </listItem>
        <listItem>
          <para>If the return value of the SQL_SQL_CONFORMANCE information type is SQL_SC_ENTRY_LEVEL or 0, call <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL92_VALUE_EXPRESSIONS information type. If the SQL_SVE_CAST bit is set, the <legacyBold>CAST</legacyBold> function is supported.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>