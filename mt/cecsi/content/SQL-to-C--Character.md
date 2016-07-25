---
title: "SQL to C: Character"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL to C: Character
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the character ODBC SQL data types are:</para>
    <para> SQL_CHAR </para>
    <para>SQL_VARCHAR </para>
    <para>SQL_LONGVARCHAR </para>
    <para>SQL_WCHAR </para>
    <para>SQL_WVARCHAR </para>
    <para>SQL_WLONGVARCHAR</para>
    <para>The following table shows the ODBC C data types to which character SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>Byte length of data &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Byte length of data &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data in bytes</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_WCHAR</para>
          </TD>
          <TD>
            <para>Character length of data &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Character length of data &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in characters</para>
            <para>Length of data in characters</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT  SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT  SQL_C_SLONG SQL_C_ULONG SQL_C_LONG  SQL_C_NUMERIC</para>
          </TD>
          <TD>
            <para>Data converted without truncation[b]</para>
            <para>Data converted with truncation of fractional digits[a]</para>
            <para>Conversion of data would result in loss of whole (as opposed to fractional) digits[a]</para>
            <para>Data is not a <legacyItalic>numeric-literal</legacyItalic>[b]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Number of bytes of the C data type</para>
            <para>Number of bytes of the C data type</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22003</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_FLOAT SQL_C_DOUBLE</para>
          </TD>
          <TD>
            <para>Data is within the range of the data type to which the number is being converted[a]</para>
            <para>Data is outside the range of the data type to which the number is being converted[a]</para>
            <para>Data is not a <legacyItalic>numeric-literal</legacyItalic>[b]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BIT</para>
          </TD>
          <TD>
            <para>Data is 0 or 1</para>
            <para>Data is greater than 0, less than 2, and not equal to 1</para>
            <para>Data is less than 0 or greater than or equal to 2</para>
            <para>Data is not a <legacyItalic>numeric-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>1[b]</para>
            <para>1[b]</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22003</para>
            <para>22018</para>
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
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_DATE</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>date-value</legacyItalic>[a]</para>
            <para>Data value is a valid <legacyItalic>timestamp-value</legacyItalic>; time portion is zero[a]</para>
            <para>Data value is a valid <legacyItalic>timestamp-value</legacyItalic>; time portion is nonzero[a],[c]</para>
            <para>Data value is not a valid <legacyItalic>date-value</legacyItalic> or <legacyItalic>timestamp-value</legacyItalic>[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>6[b]</para>
            <para>6[b]</para>
            <para>6[b]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>n/a</para>
            <para>01S07</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIME</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>time-value and the fractional seconds value is 0</legacyItalic>[a]</para>
            <para>Data value is a valid <legacyItalic>timestamp-value or a valid time-value</legacyItalic>; fractional seconds portion is zero[a],[d]</para>
            <para>Data value is a valid <legacyItalic>timestamp-value</legacyItalic>; fractional seconds portion is nonzero[a],[d],[e]</para>
            <para>Data value is not a valid <legacyItalic>time-value</legacyItalic> or <legacyItalic>timestamp-value</legacyItalic>[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>6[b]</para>
            <para>6[b]</para>
            <para>6[b]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>n/a</para>
            <para>01S07</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>timestamp-value or a valid time-value</legacyItalic>; fractional seconds portion not truncated[a]</para>
            <para>Data value is a valid <legacyItalic>timestamp-value or a valid time-value</legacyItalic>; fractional seconds portion truncated[a]</para>
            <para>Data value is a valid <legacyItalic>date-value</legacyItalic>[a]</para>
            <para>Data value is a valid <legacyItalic>time-value</legacyItalic>[a]</para>
            <para>Data value is not a valid <legacyItalic>date-value</legacyItalic>, <legacyItalic>time-value</legacyItalic>, or <legacyItalic>timestamp-value</legacyItalic>[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Data[f]</para>
            <para>Data[g]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>16[b]</para>
            <para>16[b]</para>
            <para>16[b]</para>
            <para>16[b]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>n/a</para>
            <para>n/a</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All C interval types</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>interval value</legacyItalic>; no truncation</para>
            <para>Data value is a valid <legacyItalic>interval value</legacyItalic>; truncation of one or more trailing fields</para>
            <para>Data is valid interval; leading field significant precision is lost</para>
            <para>The data value is not a valid interval value</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data in bytes</para>
            <para>Undefined</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22015</para>
            <para>22018</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of  *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[b]   This is the size of the corresponding C data type.</para>
    <para>[c]   The time portion of the <legacyItalic>timestamp-value</legacyItalic> is truncated.</para>
    <para>[d]   The date portion of the <legacyItalic>timestamp-value</legacyItalic> is ignored.</para>
    <para>[e]   The fractional seconds portion of the timestamp is truncated.</para>
    <para>[f]   The time fields of the timestamp structure are set to zero.</para>
    <para>[g]   The date fields of the timestamp structure are set to the current date.</para>
    <para>When character SQL data is converted to numeric, date, time, timestamp, or interval C data, leading and trailing spaces are ignored.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>