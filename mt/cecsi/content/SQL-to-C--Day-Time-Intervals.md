---
title: SQL to C: Day-Time Intervals
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
translation.priority.ht: 
  - en-gb
---
# SQL to C: Day-Time Intervals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the day-time interval ODBC SQL data types are:</para>
    <para>SQL_INTERVAL_DAY</para>
    <para>SQL_INTERVAL_DAY_TO_MINUTE</para>
    <para>SQL_INTERVAL_HOUR</para>
    <para>SQL_INTERVAL_DAY_TO_SECOND</para>
    <para>SQL_INTERVAL_MINUTE</para>
    <para>SQL_INTERVAL_HOUR_TO_MINUTE</para>
    <para>SQL_INTERVAL_SECOND</para>
    <para>SQL_INTERVAL_HOUR_TO_SECOND</para>
    <para>SQL_INTERVAL_DAY_TO_HOUR</para>
    <para>SQL_INTERVAL_MINUTE_TO_SECOND</para>
    <para>The following table shows the ODBC C data types to which day-time interval SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>C type identifier</para>
          </TD>
          <TD>
            <para>Test</para>
          </TD>
          <TD>
            <para>*<legacyItalic>TargetValuePtr</legacyItalic></para>
          </TD>
          <TD>
            <para>*<legacyItalic>StrLen_or_IndPtr</legacyItalic></para>
          </TD>
          <TD>
            <para>SQLSTATE</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>All day-time C interval types</para>
          </TD>
          <TD>
            <para>Trailing fields portion not truncated</para>
            <para>Trailing fields portion truncated</para>
            <para>Leading precision of target is not big enough to hold data from source</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data</para>
            <para>Length of data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22015</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]</para>
          </TD>
          <TD>
            <para>Interval precision was a single field and the data was converted without truncation</para>
            <para>Interval precision was a single field and truncated fractional</para>
            <para>Interval precision was a single field and truncated whole</para>
            <para>Interval precision was not a single field</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated  data</para>
            <para>Truncated  data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Length of data</para>
            <para>Length of data</para>
            <para>Size of the C data type</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22003</para>
            <para>07006</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BINARY</para>
          </TD>
          <TD>
            <para>Byte length of data &lt;= <legacyItalic>BufferLength</legacyItalic></para>
            <para>Byte length of data &gt; <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>Character byte length &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Size of the C data type</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_WCHAR</para>
          </TD>
          <TD>
            <para>Character length &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Size of the C data type</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
            <para>22003</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   A day-time interval SQL type can be converted to any day-time interval C type.</para>
    <para>[b]   If the interval precision is a single field (one of DAY, HOUR, MINUTE, or SECOND), the interval SQL type can be converted to any exact numeric (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG, or SQL_C_NUMERIC).</para>
    <para>The default conversion of an interval SQL type is to the corresponding C interval data type. The application then binds the column or parameter (or sets the SQL_DESC_DATA_PTR field in the appropriate record of the ARD) to point to the initialized SQL_INTERVAL_STRUCT structure (or passes a pointer to the SQL_ INTERVAL_STRUCT structure as the <legacyItalic>TargetValuePtr</legacyItalic> argument in a call to <legacyBold>SQLGetData</legacyBold>).</para>
    <para>The following example demonstrates how to transfer data from a column of type SQL_INTERVAL_DAY_TO_MINUTE into the SQL_INTERVAL_STRUCT structure such that it comes back as a DAY_TO_HOUR interval.</para>
    <code>SQL_INTERVAL_STRUCT is;
SQLINTEGER    cbValue;
SQLUINTEGER   days, hours;

// Execute a select statement; "interval_column" is a column
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);

// Bind
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &amp;is, sizeof(SQL_INTERVAL_STRUCT), &amp;cbValue);

// Fetch
SQLFetch(hstmt);

// Process data
days = is.intval.day_second.day;
hours = is.intval.day_second.hour;</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>