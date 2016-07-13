---
title: C to SQL: Bit
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 267c9fa9-599e-4ee6-b51b-0cae43f09183
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Bit
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the bit ODBC C data type is:</para>
    <para>SQL_C_BIT</para>
    <para>The following table shows the ODBC SQL data types to which bit C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
            <para>SQL_CHAR SQL_VARCHAR</para>
            <para>SQL_LONGVARCHAR</para>
            <para>SQL_WCHAR SQL_WVARCHAR</para>
            <para>SQL_WLONGVARCHAR </para>
          </TD>
          <TD>
            <para>None</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL SQL_NUMERIC</para>
            <para>SQL_TINYINT SQL_SMALLINT</para>
            <para>SQL_INTEGER SQL_BIGINT</para>
            <para>SQL_REAL SQL_FLOAT</para>
            <para>SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>None</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>None</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The driver ignores the length/indicator value when converting data from the bit C data type and assumes that the size of the data buffer is the size of the bit C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>