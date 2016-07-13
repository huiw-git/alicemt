---
title: SQL to C: Time
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL to C: Time
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the time ODBC SQL data type is:</para>
    <para>SQL_TYPE_TIME</para>
    <para>The following table shows the ODBC C data types to which time SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>
              <legacyItalic>9</legacyItalic> &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character byte length</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 9</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data[a]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
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
            <para>
              <legacyItalic>9</legacyItalic> &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character length</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 9</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data[a]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data in characters</para>
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
            <para>Byte length of data &gt; <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIME</para>
          </TD>
          <TD>
            <para>None[b]</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
          <TD>
            <para>6[d]</para>
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
            <para>None[b]</para>
          </TD>
          <TD>
            <para>Data[c]</para>
          </TD>
          <TD>
            <para>16[d]</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The fractional seconds of the time are truncated.</para>
    <para>[b]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[c]   The date fields of the timestamp structure are set to the current date, and the fractional seconds field of the timestamp structure is set to zero.</para>
    <para>[d]   This is the size of the corresponding C data type.</para>
    <para>When time SQL data is converted to character C data, the resulting string is in the "<legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>" format. This format is not affected by the Windows® country setting.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>