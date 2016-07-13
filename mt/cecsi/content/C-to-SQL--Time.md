---
title: C to SQL: Time
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Time
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the time ODBC C data type is:</para>
    <para>SQL_C_TYPE_TIME</para>
    <para>The following table shows the ODBC SQL data types to which time C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
            <para>Column byte length &gt;= 8</para>
            <para>Column byte length &lt; 8</para>
            <para>Data value is not a valid time</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22008</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
            <para>SQL_WVARCHAR</para>
            <para>SQL_WLONGVARCHAR</para>
          </TD>
          <TD>
            <para>Column character length &gt;= 8</para>
            <para>Column character length &lt; 8</para>
            <para>Data value is not a valid time</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22008</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>Data value is a valid time</para>
            <para>Data value is not a valid time</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22007</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Data value is a valid time[a]</para>
            <para>Data value is not a valid time</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22007</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The date portion of the timestamp is set to the current date, and the fractional seconds portion of the timestamp is set to zero.</para>
    <para>For information about what values are valid in a SQL_C_TYPE_TIME structure, see <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink>, earlier in this appendix.</para>
    <para>When time C data is converted to character SQL data, the resulting character data is in the "<legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>" format.</para>
    <para>The driver ignores the length/indicator value when converting data from the time C data type and assumes that the size of the data buffer is the size of the time C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>