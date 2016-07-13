---
title: C to SQL: Date
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Date
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the date ODBC C data type is:</para>
    <para>SQL_C_TYPE_DATE</para>
    <para>The following table shows the ODBC SQL data types to which date C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
            <para>Column byte length &gt;= 10</para>
            <para>Column byte length &lt; 10</para>
            <para>Data value is not a valid date</para>
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
            <para>Column character length &gt;= 10</para>
            <para>Column character length &lt; 10</para>
            <para>Data value is not a valid date</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22008</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE</para>
          </TD>
          <TD>
            <para>Data value is a valid date</para>
            <para>Data value is not a valid date</para>
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
            <para>Data value is a valid date[a]</para>
            <para>Data value is not a valid date</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22007</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The time portion of the timestamp is set to zero.</para>
    <para>For information about what values are valid in a SQL_C_TYPE_DATE structure, see <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink>, earlier in this appendix.</para>
    <para>When date C data is converted to character SQL data, the resulting character data is in the "<legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic>" format.</para>
    <para>The driver ignores the length/indicator value when converting data from the date C data type and assumes that the size of the data buffer is the size of the date C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>