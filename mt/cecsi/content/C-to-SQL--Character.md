---
title: C to SQL: Character
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Character
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the character ODBC C data type are:</para>
    <para>SQL_C_CHAR</para>
    <para>SQL_C_WCHAR</para>
    <para>The following table shows the ODBC SQL data types to which C character data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
    <alert class="note">
      <para>When character C data is converted to Unicode SQL data, the length of the Unicode data must be an even number.</para>
    </alert>
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
            <para>SQL_CHAR</para>
            <para>SQL_VARCHAR</para>
            <para>SQL_LONGVARCHAR </para>
          </TD>
          <TD>
            <para>Byte length of data &lt;= Column length.</para>
            <para>Byte length of data &gt; Column length.</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
            <para>SQL_WVARCHAR</para>
            <para>SQL_WLONGVARCHAR</para>
          </TD>
          <TD>
            <para>Character length of data &lt;= Column length.</para>
            <para>Character length of data &gt; Column length.</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL</para>
            <para>SQL_NUMERIC</para>
            <para>SQL_TINYINT</para>
            <para>SQL_SMALLINT</para>
            <para>SQL_INTEGER SQL_BIGINT</para>
          </TD>
          <TD>
            <para>Data converted without truncation</para>
            <para>Data converted with truncation of fractional digits[e]</para>
            <para>Conversion of data would result in loss of whole (as opposed to fractional) digits[e]</para>
            <para>Data value is not a <legacyItalic>numeric-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22001</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL </para>
            <para>SQL_FLOAT </para>
            <para>SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>Data is within the range of the data type to which the number is being converted</para>
            <para>Data is outside the range of the data type to which the number is being converted</para>
            <para>Data value is not a <legacyItalic>numeric-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>Data is 0 or 1</para>
            <para>Data is greater than 0, less than 2, and not equal to 1</para>
            <para>Data is less than 0 or greater than or equal to 2</para>
            <para>Data is not a <legacyItalic>numeric-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22003</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BINARY </para>
            <para>SQL_VARBINARY</para>
            <para>SQL_LONGVARBINARY</para>
          </TD>
          <TD>
            <para>(Byte length of data) / 2 &lt;= column byte length</para>
            <para>(Byte length of data) / 2 &gt; column byte length</para>
            <para>Data value is not a hexadecimal value</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>ODBC-date-literal</legacyItalic></para>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; time portion is zero</para>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; time portion is nonzero[a]</para>
            <para>Data value is not a valid <legacyItalic>ODBC-date-literal</legacyItalic> or <legacyItalic>ODBC-timestamp-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>n/a</para>
            <para>22008</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>ODBC-time-literal</legacyItalic></para>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; fractional seconds portion is zero[b]</para>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; fractional seconds portion is nonzero[b]</para>
            <para>Data value is not a valid <legacyItalic>ODBC-time-literal</legacyItalic> or <legacyItalic>ODBC-timestamp-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>n/a</para>
            <para>22008</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; fractional seconds portion not truncated</para>
            <para>Data value is a valid <legacyItalic>ODBC-timestamp-literal</legacyItalic>; fractional seconds portion truncated</para>
            <para>Data value is a valid <legacyItalic>ODBC-date-literal</legacyItalic>[c]</para>
            <para>Data value is a valid <legacyItalic>ODBC-time-literal</legacyItalic>[d]</para>
            <para>Data value is not a valid <legacyItalic>ODBC-date-literal</legacyItalic>, <legacyItalic>ODBC-time-literal</legacyItalic>, or <legacyItalic>ODBC-timestamp-literal</legacyItalic></para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22008</para>
            <para>n/a</para>
            <para>n/a</para>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All SQL interval types</para>
          </TD>
          <TD>
            <para>Data value is a valid <legacyItalic>interval value</legacyItalic>; no truncation occurs</para>
            <para>Data value is a valid <legacyItalic>interval value</legacyItalic>; the value in one of the fields is truncated</para>
            <para>The data value is not a valid interval literal</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22015</para>
            <para>22018</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The time portion of the timestamp is truncated.</para>
    <para>[b]   The date portion of the timestamp is ignored.</para>
    <para>[c]   The time portion of the timestamp is set to zero.</para>
    <para>[d]   The date portion of the timestamp is set to the current date.</para>
    <para>[e]   The driver/data source effectively waits until the entire string has been received (even if the character data is sent in pieces by calls to <legacyBold>SQLPutData</legacyBold>) before attempting to perform the conversion.</para>
    <para>When character C data is converted to numeric, date, time, or timestamp SQL data, leading and trailing blanks are ignored.</para>
    <para>When character C data is converted to binary SQL data, each two bytes of character data are converted to a single byte (8 bits) of binary data. Each two bytes of character data represent a number in hexadecimal form. For example, "01" is converted to a binary 00000001 and "FF" is converted to a binary 11111111.</para>
    <para>The driver always converts pairs of hexadecimal digits to individual bytes and ignores the null-termination byte. Because of this, if the length of the character string is odd, the last byte of the string (excluding the null-termination byte, if any) is not converted.</para>
    <alert class="note">
      <para>Application developers are discouraged from binding character C data to a binary SQL data type. This conversion is usually inefficient and slow.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>