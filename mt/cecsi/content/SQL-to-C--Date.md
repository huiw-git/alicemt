---
title: "SQL to C: Date"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL to C: Date
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the date ODBC SQL data type is:</para>
    <para>SQL_TYPE_DATE</para>
    <para>The following table shows the ODBC C data types to which date SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>
              <legacyItalic>BufferLength</legacyItalic> &gt; Character byte length</para>
            <para>11 &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character byte length</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 11</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>10</para>
            <para>Length of data in bytes</para>
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
            <para>
              <legacyItalic>BufferLength</legacyItalic> &gt; Character length</para>
            <para>11 &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character length</para>
            <para>               <legacyItalic>BufferLength</legacyItalic> &lt; 11</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>10</para>
            <para>Length of data in characters</para>
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
            <para>SQL_C_BINARY</para>
          </TD>
          <TD>
            <para>Byte length of data &lt;= <legacyItalic>BufferLength</legacyItalic></para>
            <para> Byte length of data &gt; <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para> Undefined</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para> Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para> 22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_DATE</para>
          </TD>
          <TD>
            <para>None[a]</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
          <TD>
            <para>6[c]</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>None[a]</para>
          </TD>
          <TD>
            <para>Data[b]</para>
          </TD>
          <TD>
            <para>16[c]</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[b]   The time fields of the timestamp structure are set to zero.</para>
    <para>[c]   This is the size of the corresponding C data type.</para>
    <para>When date SQL data is converted to character C data, the resulting string is in the "<legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic>" format. This format is not affected by the Windows® country setting.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>