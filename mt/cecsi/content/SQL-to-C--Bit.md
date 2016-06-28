---
title: SQL to C: Bit
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
translation.priority.ht: 
  - en-gb
---
# SQL to C: Bit
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the bit ODBC SQL data type is:</para>
    <para>SQL_BIT</para>
    <para>The following table shows the ODBC C data types to which bit SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>SQL_C_WCHAR</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &gt; 1</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt;= 1</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>1</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_STINYINT</para>
            <para>SQL_C_UTINYINT</para>
            <para>SQL_C_TINYINT</para>
            <para>SQL_C_SBIGINT</para>
            <para>SQL_C_UBIGINT</para>
            <para>SQL_C_SSHORT</para>
            <para>SQL_C_USHORT</para>
            <para>SQL_C_SHORT</para>
            <para>SQL_C_SLONG</para>
            <para>SQL_C_ULONG</para>
            <para>SQL_C_LONG</para>
            <para>SQL_C_FLOAT</para>
            <para>SQL_C_DOUBLE</para>
            <para>SQL_C_NUMERIC</para>
          </TD>
          <TD>
            <para>None[a]</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BIT</para>
          </TD>
          <TD>
            <para>None[a]</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
          <TD>
            <para>1[b]</para>
          </TD>
          <TD>
            <para>n/a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BINARY</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &gt;= 1</para>
            <para>
              <legacyItalic>BufferLength</legacyItalic> &lt; 1</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>1</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[b]   This is the size of the corresponding C data type.</para>
    <para>When bit SQL data is converted to character C data, the possible values are "0" and "1".</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>