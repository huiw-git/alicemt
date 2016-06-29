---
title: SQL to C: Binary
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
translation.priority.ht: 
  - en-gb
---
# SQL to C: Binary
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the binary ODBC SQL data types are:</para>
    <para>SQL_BINARY</para>
    <para>SQL_VARBINARY</para>
    <para>SQL_LONGVARBINARY</para>
    <para>The following table shows the ODBC C data types to which binary SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>(Byte length of data) * 2 &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>(Byte length of data) * 2 &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data in bytes</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_WCHAR</para>
          </TD>
          <TD>
            <para>(Character length of data) * 2 &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>(Character length of data) * 2 &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in characters</para>
            <para>Length of data in characters</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
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
            <para>Truncated data</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data in bytes</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01004</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>When binary SQL data is converted to character C data, each byte (8 bits) of source data is represented as two ASCII characters. These characters are the ASCII character representation of the number in its hexadecimal form. For example, a binary 00000001 is converted to "01" and a binary 11111111 is converted to "FF".</para>
    <para>The driver always converts individual bytes to pairs of hexadecimal digits and terminates the character string with a null byte. Because of this, if <legacyItalic>BufferLength</legacyItalic> is even and is less than the length of the converted data, the last byte of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer is not used. (The converted data requires an even number of bytes, the next-to-last byte is a null byte, and the last byte cannot be used.)</para>
    <alert class="note">
      <para>Application developers are discouraged from binding binary SQL data to a character C data type. This conversion is usually inefficient and slow.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>