---
title: SQL to C: Timestamp
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL to C: Timestamp
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the timestamp ODBC SQL data type is:</para>
    <para>SQL_TYPE_TIMESTAMP</para>
    <para>The following table shows the ODBC C data types to which timestamp SQL data can be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>20 &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character byte length</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 20</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data[b]</para>
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
            <para>20 &lt;= <legacyItalic>BufferLength</legacyItalic> &lt;= Character length</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 20</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data[b]</para>
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
            <para>SQL_C_TYPE_DATE</para>
          </TD>
          <TD>
            <para>Time portion of timestamp is zero[a]</para>
            <para>Time portion of timestamp is nonzero[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data[c]</para>
          </TD>
          <TD>
            <para>6[f]</para>
            <para>6[f]</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIME</para>
          </TD>
          <TD>
            <para>Fractional seconds portion of timestamp is zero[a]</para>
            <para>Fractional seconds portion of timestamp is nonzero[a]</para>
          </TD>
          <TD>
            <para>Data[d]</para>
            <para>Truncated data[d], [e]</para>
          </TD>
          <TD>
            <para>6[f]</para>
            <para>6[f]</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Fractional seconds portion of timestamp is not truncated[a]</para>
            <para>Fractional seconds portion of timestamp is truncated[a]</para>
          </TD>
          <TD>
            <para>Data[e]</para>
            <para>Truncated data[e]</para>
          </TD>
          <TD>
            <para>16[f]</para>
            <para>16[f]</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[b]   The fractional seconds of the timestamp are truncated.</para>
    <para>[c]   The time portion of the timestamp is truncated.</para>
    <para>[d]   The date portion of the timestamp is ignored.</para>
    <para>[e]   The fractional seconds portion of the timestamp is truncated.</para>
    <para>[f]   This is the size of the corresponding C data type.</para>
    <para>When timestamp SQL data is converted to character C data, the resulting string is in the "<legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic> <legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>[.<legacyItalic>f...</legacyItalic>]" format, where up to nine digits can be used for fractional seconds. This format is not affected by the Windows® country setting. (Except for the decimal point and fractional seconds, the entire format must be used, regardless of the precision of the timestamp SQL data type.)</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>