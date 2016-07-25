---
title: "C to SQL: Day-Time Intervals"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Day-Time Intervals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the day-time interval ODBC C data types are:</para>
    <para>SQL_C_INTERVAL_DAY</para>
    <para>SQL_C_INTERVAL_HOUR</para>
    <para>SQL_C_INTERVAL_MINUTE </para>
    <para>SQL_C_INTERVAL_SECOND</para>
    <para>SQL_C_INTERVAL_DAY_TO_HOUR</para>
    <para>SQL_C_INTERVAL_DAY_TO_MINUTE</para>
    <para>SQL_C_INTERVAL_DAY_TO_SECOND</para>
    <para>SQL_C_INTERVAL_HOUR_TO_MINUTE</para>
    <para>SQL_C_INTERVAL_HOUR_TO_SECOND</para>
    <para>SQL_C_INTERVAL_MINUTE_TO_SECOND</para>
    <para>The following table shows the ODBC SQL data types to which interval C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type identifier</para>
          </TD>
          <TD>
            <para>Test</para>
          </TD>
          <TD>
            <para>SQLSTATE</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_CHAR[a]</para>
            <para>SQL_VARCHAR[a]</para>
            <para>SQL_LONGVARCHAR[a]</para>
          </TD>
          <TD>
            <para>Column byte length &gt;= Character byte length</para>
            <para>Column byte length &lt; Character byte length[a]</para>
            <para>Data value is not a valid interval literal</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para> 22015</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR[a]</para>
            <para>SQL_WVARCHAR[a]</para>
            <para>SQL_WLONGVARCHAR[a]</para>
          </TD>
          <TD>
            <para>Column character length &gt;= Character length of data</para>
            <para>Column character length &lt; Character length of data[a]</para>
            <para>Data value is not a valid interval literal</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para> 22015</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TINYINT[b]</para>
            <para>SQL_SMALLINT[b] SQL_INTEGER[b]</para>
            <para>SQL_BIGINT[b] SQL_NUMERIC[b]</para>
            <para>SQL_DECIMAL[b]</para>
          </TD>
          <TD>
            <para>Conversion of a single-field interval did not result in truncation of whole digits</para>
            <para>Conversion resulted in truncation of whole digits</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY</para>
            <para>SQL_INTERVAL_HOUR</para>
            <para>SQL_INTERVAL_MINUTE</para>
            <para>SQL_INTERVAL_SECOND</para>
            <para>SQL_INTERVAL_DAY_TO_HOUR</para>
            <para>SQL_INTERVAL_DAY_TO_MINUTE</para>
            <para>SQL_INTERVAL_DAY_TO_SECOND</para>
            <para>SQL_INTERVAL_HOUR_TO_MINUTE</para>
            <para>SQL_INTERVAL_HOUR_TO_SECOND</para>
            <para>SQL_INTERVAL_MINUTE_TO_SECOND</para>
          </TD>
          <TD>
            <para>Data value was converted without truncation of any fields</para>
            <para>One or more fields of data value were truncated during conversion</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22015</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   All C interval data types can be converted to a character data type.</para>
    <para>[b]   If the type field in the interval structure is such that the interval is a single field (SQL_DAY, SQL_HOUR, SQL_MINUTE, or SQL_SECOND), the interval C type can be converted to any exact numeric (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL, or SQL_NUMERIC).</para>
    <para>The default conversion of an interval C type is to the corresponding day-time interval SQL type.</para>
    <para>The driver ignores the length/indicator value when converting data from the interval C data type and assumes that the size of the data buffer is the size of the interval C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
    <para>The following example demonstrates how to send interval C data stored in the SQL_INTERVAL_STRUCT structure into a database column. The interval structure contains a DAY_TO_SECOND interval; it will be stored in a database column of type SQL_INTERVAL_DAY_TO_MINUTE.</para>
    <code>SQL_INTERVAL_STRUCT is;
SQLINTEGER cbValue;

// Initialize the interval struct to contain the DAY_TO_SECOND
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"
is.intval.day_second.day      = 154;
is.intval.day_second.hour     = 22;
is.intval.day_second.minute   = 44;
is.intval.day_second.second   = 10;
is.interval_sign              = SQL_FALSE;

// Bind the dynamic parameter
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &amp;is,
                  sizeof(SQL_INTERVAL_STRUCT), &amp;cbValue);

// Execute an insert statement; "interval_column" is a column
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>