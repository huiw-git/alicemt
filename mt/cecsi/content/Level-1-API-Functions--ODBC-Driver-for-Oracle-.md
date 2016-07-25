---
title: "Level 1 API Functions (ODBC Driver for Oracle)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Level 1 API Functions (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Functions at this level provide Core interface conformance plus additional functionality such as transaction support.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>API function</para>
          </TD>
          <TD>
            <para>Notes</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLColumns</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Creates a result set for a table, which is the column list for the specified table or tables. When you request columns for a PUBLIC synonym, you must have set the SYNONYMCOLUMNS connection attribute and specified an empty string as the <legacyItalic>szTableOwner</legacyItalic> argument. When returning columns for PUBLIC synonyms, the driver sets the TABLE NAME column to an empty string. The result set contains an additional column, ORDINAL POSITION, at the end of each row. This value is the ordinal position of the column in the table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDriverConnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Connects to an existing data source. For details, see <legacyLink xlink:href="0c360112-8720-4e54-a1a6-b9b18d943557">Connection String Format and Attributes</legacyLink>. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetConnectOption</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the current setting of a connection option. This function is partially supported. The driver supports all values for the <legacyItalic>fOption</legacyItalic> argument but does not support some <legacyItalic>vParam</legacyItalic> values for the <legacyItalic>fOption</legacyItalic> argument <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_TXN_ISOLATION</legacyLink>. For more information, see <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">Connect Options</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetData</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Retrieves the value of a single field in the current record of the given result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetFunctions</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns TRUE for all supported functions. Implemented by the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetInfo</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns information, including SQLHDBC, SQLUSMALLINT, SQLPOINTER, SQLSMALLINT, and SQLSMALLINT *, about the ODBC Driver for Oracle and data source associated with a connection handle, <legacyItalic>hdbc</legacyItalic>. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetStmtOption</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the current setting of a statement option. For more information, see <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">Statement Options</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetTypeInfo</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns information about the data types supported by a data source. The driver returns the information in an SQL result set. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLParamData</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Used in conjunction with <legacyBold>SQLPutData</legacyBold> to specify parameter data at statement execution time.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLPutData</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Allows an application to send data for a parameter or column to the driver at statement execution time.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetConnectOption</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Provides access to options that govern aspects of the connection. This function is partially supported: The driver supports all values for the <legacyItalic>fOption</legacyItalic> argument but does not support some <legacyItalic>vParam</legacyItalic> values for the <legacyItalic>fOption</legacyItalic> argument <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">SQL_TXN_ISOLATION</legacyLink>. For more information, see <legacyLink xlink:href="abfdc133-cb33-435f-a467-fbe15444f687">Connect Options</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetStmtOption</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Sets options related to a statement handle, <legacyItalic>hstmt</legacyItalic>. For more information, see <legacyLink xlink:href="cd73b769-c8b5-43e0-9f80-b3011b7a6162">Statement Options</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSpecialColumns</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Retrieves the optimal set of columns that uniquely identifies a row in the table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLStatistics</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Retrieves a list of statistics about a single table and the indexes, or tag names, associated with the table. The driver returns the information as a result set. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLTables</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the list of table names specified by the parameter in the <legacyBold>SQLTables</legacyBold> statement. If no parameter is specified, returns the table names stored in the current data source. The driver returns the information as a result set.</para>
            <para>Enumeration type calls will not receive a result set entry for remote views or local parameterized views. However, a call to <legacyBold>SQLTables</legacyBold> with a unique table name specifier will find a match for such a view, if present, with that name; this allows the API to check for name conflicts prior to creation of a new table.</para>
            <para>PUBLIC synonyms are returned with a TABLE_OWNER value of "".</para>
            <para>VIEWS owned by SYS or SYSTEM are identified as SYSTEM VIEW.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>