---
title: Level 2 API Functions (ODBC Driver for Oracle)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Level 2 API Functions (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Functions at this level provide Level 1 interface conformance plus additional functionality such as support for bookmarks, dynamic parameters, and asynchronous execution of ODBC functions.</para>
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
              <legacyBold>SQLBindParameter</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Associates a buffer with a parameter marker in an SQL statement. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLBrowseConnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns successive levels of attributes and attribute values.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDataSources</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Lists data source names. Implemented by the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDescribeParam</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the description of a parameter marker associated with a prepared SQL statement.</para>
            <para>Returns a best guess of what the parameter is, based on parsing the statement. If the parameter type cannot be determined, SQL_VARCHAR returns with length 2000.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDrivers</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Implemented by the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLExtendedFetch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Similar to <legacyBold>SQLFetch</legacyBold> but returns multiple rows using an array for each column. The result set is forward-scrollable and can be made backward-scrollable if the cursor is defined to be static, not forward-only. For forward-only cursors with default column binding, column data from data sets larger than the BUFFERSIZE connection attribute is fetched directly into data buffers. Does not support variable-length bookmarks and does not support fetching a rowset at an offset (other than 0) from a bookmark.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLForeignKeys</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns a list of foreign keys in a single table, or a list of foreign keys in other tables that refer to a single table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLMoreResults</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Determines whether more results are pending on a statement handle, hstmt, containing SELECT, UPDATE, INSERT, or DELETE statements and if so, initializes processing for those results.</para>
            <para>Oracle supports multiple result sets only from stored procedures, when using {resultset... } escape sequences.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLNativeSql</legacyBold>
            </para>
          </TD>
          <TD>
            <para>For information about usage, see <legacyLink xlink:href="2018069b-da5d-4cee-a971-991897d4f7b5">Returning Array Parameters from Stored Procedures</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLNumParams</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the number of parameters in an SQL statement. The number of parameters should equal the number of question marks in the SQL statement passed to <legacyBold>SQLPrepare</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLPrimaryKeys</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the column names that comprise the primary key for a table. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLProcedureColumns</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns a list of input and output parameters, the return value, the columns in the result set of a single procedure, and two additional columns, OVERLOAD and ORDINAL_POSITION. OVERLOAD is the OVERLOAD column from the ALL_ARGUMENTS table of the Oracle Data Dictionary View. ORDINAL_POSITION is the SEQUENCE column from the ALL_ARGUMENTS table of the Oracle Data Dictionary View. For packaged procedures, the PROCEDURE NAME column is in <legacyItalic>packagename.procedurename</legacyItalic> format. Does not return the procedure columns of a created synonym that refers to a procedure or function.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLProcedures</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns a list of procedures in the data source. For packaged procedures, the PROCEDURE NAME column is in <legacyItalic>packagename.procedurename</legacyItalic> format.</para>
            <para>Because Oracle does not provide a way to distinguish packaged procedures from packaged functions, the driver returns SQL_PT_UNKNOWN for the PROCEDURE_TYPE column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetPos</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Sets the cursor position in a rowset. You can use <legacyBold>SQLSetPos</legacyBold> with <legacyBold>SQLGetData</legacyBold> to retrieve rows from unbound columns after positioning the cursor to a specific row in the rowset. Rows added to the result set using <legacyItalic>fOption</legacyItalic> SQL_ADD are added after the last row in the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetScrollOptions</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Sets options that control the behavior of cursors associated with a statement handle, hstmt. For details, see <legacyLink xlink:href="db63d610-f86f-4029-9d66-fed616c8a818">Cursor Type and Concurrency Combinations</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>