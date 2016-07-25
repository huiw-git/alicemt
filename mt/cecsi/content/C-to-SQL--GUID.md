---
title: "C to SQL: GUID"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: GUID
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the GUID ODBC C data type is:</para>
    <para>SQL_C_GUID</para>
    <para>The following table shows the ODBC SQL data types to which GUID C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
          </TD>
          <TD>
            <para>Column byte length &gt;= 36 </para>
          </TD>
          <TD>
            <para>n/a </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_VARCHAR</para>
          </TD>
          <TD>
            <para>Column byte length &lt; 36</para>
          </TD>
          <TD>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LONGVARCHAR</para>
          </TD>
          <TD>
            <para>Data value is not a valid GUID</para>
          </TD>
          <TD>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
          </TD>
          <TD>
            <para>Column character length &gt;= 36 </para>
          </TD>
          <TD>
            <para>n/a </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WVARCHAR</para>
          </TD>
          <TD>
            <para>Column character length &lt; 36</para>
          </TD>
          <TD>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WLONGVARCHAR</para>
          </TD>
          <TD>
            <para>Data value is not a valid GUID</para>
          </TD>
          <TD>
            <para>22018</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_GUID</para>
          </TD>
          <TD>
            <para>None[a]</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   All hexidecimal values are valid as a GUID.</para>
    <para>The driver ignores the length/indicator value when converting data from the GUID C data type and assumes that the size of the data buffer is the size of the GUID C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>