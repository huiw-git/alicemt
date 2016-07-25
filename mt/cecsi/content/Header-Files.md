---
title: "Header Files"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Header Files
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Sql.h header file contains prototypes for the functions and features in the Core ODBC Interface conformance level. The Sqlext.h header file contains prototypes for the functions and features in the Level 1 and Level 2 API conformance levels. The Sqltypes.h header file contains type definitions and indicators for the SQL data types.</para>
    <para>The header files all contain a <legacyBold>#define</legacyBold>, ODBCVER, that an application or driver can set to be compiled for different versions of ODBC.</para>
    <para>To align with the ISO CLI and Open Group CLI, the header files contain aliases for the information types used in calls to <legacyBold>SQLGetInfo</legacyBold>. In the following table, the column "ODBC name" indicates the ODBC name for the information type in <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>. The column "Alias in header file" indicates the name that is used in the ISO CLI and the Open Group CLI. The actual numeric value of these manifest names is the same in both ODBC and the standard CLIs. These aliases enable a standards-compliant application or driver to compile with the ODBC 3<legacyItalic>.x</legacyItalic> header files.</para>
    <para>These aliases include expansions of abbreviations in the ODBC names so that the names are more understandable. "MAX" is expanded to "MAXIMUM", "LEN" to "LENGTH", "MULT" to "MULTIPLE", "OJ" to "OUTER_JOIN", and "TXN" to "TRANSACTION."</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC name</para>
          </TD>
          <TD>
            <para>Alias in header file</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_MAX_CATALOG_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_CATALOG_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_COLUMN_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_COLUMN_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_COLUMNS_IN_GROUP_BY</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_COLUMNS_IN_GROUP_BY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_COLUMNS_IN_ORDER_BY</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_COLUMNS_IN_ORDER_BY</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_COLUMNS_IN_SELECT</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_COLUMNS_IN_SELECT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_COLUMNS_IN_TABLE</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_COLUMNS_IN_TABLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_CONCURRENT_ACTIVITIES</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_CONCURRENT_ACTIVITIES</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_CURSOR_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_CURSOR_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_DRIVER_CONNECTIONS</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_DRIVER_CONNECTIONS</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_IDENTIFIER_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_IDENTIFIER_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_SCHEMA_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_SCHEMA_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_STATEMENT_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_STATEMENT_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_TABLE_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_TABLE_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_TABLES_IN_SELECT</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_TABLES_IN_SELECT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MAX_USER_NAME_LEN</para>
          </TD>
          <TD>
            <para>SQL_MAXIMUM_USER_NAME_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_MULT_RESULT_SETS</para>
          </TD>
          <TD>
            <para>SQL_MULTIPLE_RESULT_SETS</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_OJ_CAPABILITIES</para>
          </TD>
          <TD>
            <para>SQL_OUTER_JOIN_CAPABILITIES</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TXN_CAPABLE</para>
          </TD>
          <TD>
            <para>SQL_TRANSACTION_CAPABLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TXN_ISOLATION_OPTION</para>
          </TD>
          <TD>
            <para>SQL_TRANSACTION_ISOLATION_OPTION</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>