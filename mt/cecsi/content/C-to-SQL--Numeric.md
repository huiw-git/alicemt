---
title: C to SQL: Numeric
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
translation.priority.ht: 
  - en-gb
---
# C to SQL: Numeric
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the numeric ODBC C data types are:</para>
    <para>SQL_C_STINYINT</para>
    <para>SQL_C_SLONG</para>
    <para>SQL_C_UTINYINT</para>
    <para>SQL_C_ULONG</para>
    <para>SQL_C_TINYINT</para>
    <para>SQL_C_LONG</para>
    <para>SQL_C_SSHORT</para>
    <para>SQL_C_FLOAT</para>
    <para>SQL_C_USHORT</para>
    <para>SQL_C_DOUBLE</para>
    <para>SQL_C_SHORT</para>
    <para>SQL_C_NUMERIC</para>
    <para>SQL_C_SBIGINT</para>
    <para>SQL_C_UBIGINT</para>
    <para>The following table shows the ODBC SQL data types to which numeric C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
            <para>SQL_LONGVARCHAR</para>
          </TD>
          <TD>
            <para>Number of digits &lt;= Column byte length</para>
            <para>Number of digits &gt; Column byte length</para>
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
            <para>Number of characters &lt;= Column character length</para>
            <para>Number of characters &gt; Column character length</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL[b]</para>
            <para>SQL_NUMERIC[b]</para>
            <para>SQL_TINYINT[b]</para>
            <para>SQL_SMALLINT[b]</para>
            <para>SQL_INTEGER[b]</para>
            <para>SQL_BIGINT[b]</para>
          </TD>
          <TD>
            <para>Data converted without truncation or with truncated of fractional digits</para>
            <para>Data converted with truncation of whole digits</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para> 22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL</para>
            <para>SQL_FLOAT</para>
            <para>SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>Data is within the range of the data type to which the number is being converted</para>
            <para>Data is outside the range of the data type to which the number is being converted</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
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
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_YEAR[a]</para>
            <para>SQL_INTERVAL_MONTH[a]</para>
            <para>SQL_INTERVAL_DAY[a]</para>
            <para>SQL_INTERVAL_HOUR[a]</para>
            <para>SQL_INTERVAL_MINUTE[a]</para>
            <para>SQL_INTERVAL_SECOND[a]</para>
          </TD>
          <TD>
            <para>Data not truncated.</para>
            <para>Data truncated.</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22015</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   These conversions are supported only for the exact numeric data types (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG, or SQL_C_NUMERIC). They are not supported for the approximate numeric data types (SQL_C_FLOAT or SQL_C_DOUBLE). Exact numeric C data types cannot be converted to an interval SQL type whose interval precision is not a single field.</para>
    <para>[b]   For the "n/a" case, a driver may optionally return SQL_SUCCESS_WITH_INFO and 01S07 when there is a fractional truncation.</para>
    <para>The driver ignores the length/indicator value when converting data from the numeric C data types and assumes that the size of the data buffer is the size of the numeric C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>