---
title: "Unicode Data"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Unicode Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>SQL Unicode data types are provided to describe data that resides in Unicode natively on the DBMS. A C Unicode data type is provided to allow an application to bind data to a Unicode buffer. The Driver Manager can convert data from a Unicode C type (SQL_C_WCHAR) to make it function with an ANSI driver.</para>
    <para>An ODBC 3.0 or 2.<legacyItalic>x</legacyItalic> application will always bind to the ANSI data types. For optimum performance, an ODBC 3.5 (or higher) application should bind to the ANSI data C type if the SQL column type is ANSI, and should bind to the Unicode C data type if the SQL column type is Unicode.</para>
    <para>The SQL Unicode type indicators are SQL_WCHAR, SQL_WVARCHAR, and SQL_WLONGVARCHAR. SQL_WCHAR data has a fixed string length, while SQL_WVARCHAR has a variable length with a declared maximum and SQL_WLONGVARCHAR has a variable length with a maximum that depends on the data source.</para>
    <para>The C Unicode type indicator is SQL_C_WCHAR. This is the default for each of the SQL Unicode type indicators. All of the SQL types can be converted to SQL_C_WCHAR, and SQL_C_WCHAR can be converted to all of the SQL types. An application can retrieve data in one of three ways:  </para>
    <list class="bullet">
      <listItem>
        <para>Retrieve the data as SQL_C_CHAR.</para>
      </listItem>
      <listItem>
        <para>Retrieve the data as SQL_C_WCHAR.</para>
      </listItem>
      <listItem>
        <para>Declare the data as SQL_C_TCHAR. This is a macro that inserts SQL_C_WCHAR if the application is compiled as a Unicode application or inserts SQL_C_CHAR if it is compiled as an ANSI application.</para>
      </listItem>
    </list>
    <para>SQL_C_TCHAR is declared in a function as follows:</para>
    <code>SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &amp;Name)</code>
    <para>When the application is compiled as a Unicode application, the <legacyItalic>ValueType</legacyItalic> argument would be changed from SQL_C_TCHAR to SQL_C_WCHAR. When the application is compiled as an ANSI application, the <legacyItalic>ValueType</legacyItalic> argument would be changed to SQL_C_CHAR.</para>
    <para>Unicode drivers must still support ANSI data types, including SQL_CHAR. If an application working with a Unicode driver binds to SQL_CHAR, the Driver Manager will not map the SQL_CHAR data to SQL_WCHAR. The Unicode driver must accept the SQL_CHAR data.</para>
    <para>The Driver Manager stores driver and DSN names in Unicode and maps them to ANSI as needed. If a Unicode character cannot be mapped to an ANSI character (as can occur if characters from a code page that is not the native code page of the computer are used in driver and DSN names), the characters that could not be converted are represented by a default character supplied by the system.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>