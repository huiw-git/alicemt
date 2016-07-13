---
title: Datetime Data Type Changes
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Datetime Data Type Changes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In ODBC 3.<legacyItalic>x</legacyItalic>, the identifiers for date, time, and timestamp SQL data types have changed from SQL_DATE, SQL_TIME, and SQL_TIMESTAMP (with instances of <legacyBold>#define</legacyBold> in the header file of 9, 10, and 11) to SQL_TYPE_DATE, SQL_TYPE_TIME, and SQL_TYPE_TIMESTAMP (with instances of <legacyBold>#define</legacyBold> in the header file of 91, 92, and 93), respectively. The corresponding C type identifiers have changed from SQL_C_DATE, SQL_C_TIME, and SQL_C_TIMESTAMP to SQL_C_TYPE_DATE, SQL_C_TYPE_TIME, and SQL_C_TYPE_TIMESTAMP, respectively.</para>
    <para>The column size and decimal digits returned for the SQL datetime data types in ODBC 3.<legacyItalic>x</legacyItalic> are the same as the precision and scale returned for them in ODBC 2.<legacyItalic>x</legacyItalic>. These values are different than the values in the SQL_DESC_PRECISION and SQL_DESC_SCALE descriptor fields. (For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.)</para>
    <para>These changes affect <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLDescribeParam</legacyBold>, and <legacyBold>SQLColAttribute</legacyBold>; <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLBindParameter</legacyBold>, and <legacyBold>SQLGetData</legacyBold>; and <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLGetTypeInfo</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, <legacyBold>SQLStatistics</legacyBold>, and <legacyBold>SQLSpecialColumns</legacyBold>.</para>
    <para>The following table shows how the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager performs mapping of the date, time, and timestamp C data types entered in the <legacyItalic>TargetType</legacyItalic> arguments of <legacyBold>SQLBindCol</legacyBold> and <legacyBold>SQLGetData</legacyBold> or in the <legacyItalic>ValueType</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Data type</para>
            <para>code entered</para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic> app to</para>
            <para>2.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic> app to</para>
            <para>3.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic> app to</para>
            <para>2.<legacyItalic>x </legacyItalic>driver</para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic> app to</para>
            <para>3.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_C_DATE (9)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_DATE (91)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_DATE (91)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_DATE (91)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_C_DATE (9)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TIME (10)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_TIME (92)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_TIME (92)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIME (92)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_C_TIME (10)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TIMESTAMP (11)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP (93)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP (93)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP (93)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_C_TIMESTAMP (11)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   As a result of this, an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver can use the date, time, or timestamp codes returned in the result sets that are returned by the catalog functions.</para>
    <para>[2]   As a result of this, an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 3.<legacyItalic>x</legacyItalic> driver can use the date, time, or timestamp codes returned in the result sets that are returned by the catalog functions.</para>
    <para>The following table shows how the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager performs mapping of the date, time, and timestamp SQL data types entered in the <legacyItalic>ParameterType</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> or in the <legacyItalic>DataType</legacyItalic> argument of <legacyBold>SQLGetTypeInfo</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Data type</para>
            <para>code entered</para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic> app to</para>
            <para>2.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic> app to</para>
            <para>3.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic> app to</para>
            <para>2.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic> app to</para>
            <para>3.<legacyItalic>x</legacyItalic> driver</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_DATE (9)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_TYPE_DATE (91)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_TYPE_DATE (91)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE (91)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_DATE (9)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TIME (10)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIME (92)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIME (92)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME (92)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_TIME (10)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TIMESTAMP (11)</para>
          </TD>
          <TD>
            <para>No mapping</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIMESTAMP (93)</para>
          </TD>
          <TD>
            <para>No mapping[1]</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIMESTAMP (93)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP (93)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>Error (from DM)</para>
          </TD>
          <TD>
            <para>SQL_TIMESTAMP (11)</para>
          </TD>
          <TD>
            <para>No mapping[2]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   As a result of this, an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver can use the date, time, or timestamp codes returned in the result sets that are returned by the catalog functions.</para>
    <para>[2]   As a result of this, an ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 3.<legacyItalic>x</legacyItalic> driver can use the date, time, or timestamp codes returned in the result sets that are returned by the catalog functions.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>