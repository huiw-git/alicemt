---
title: "C to SQL: Binary"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Binary
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the binary ODBC C data type is:</para>
    <para>SQL_C_BINARY</para>
    <para>The following table shows the ODBC SQL data types to which binary C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
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
            <para>Byte length of data &lt;= Column byte length</para>
            <para>Byte length of data &gt; Column byte length</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
            <para>SQL_WVARCHAR</para>
            <para>SQL_WLONGVARCHAR </para>
          </TD>
          <TD>
            <para>Character length of data &lt;= Column character length</para>
            <para>Character length of data &gt; Column character length</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL</para>
            <para>SQL_NUMERIC </para>
            <para>SQL_TINYINT</para>
            <para>SQL_SMALLINT</para>
            <para>SQL_INTEGER</para>
            <para>SQL_BIGINT</para>
            <para>SQL_REAL</para>
            <para>SQL_FLOAT</para>
            <para>SQL_DOUBLE</para>
            <para>SQL_BIT SQL_TYPE_DATE</para>
            <para>SQL_TYPE_TIME</para>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Byte length of data = SQL data length</para>
            <para>Byte length of data &lt;&gt; SQL data length</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BINARY</para>
            <para>SQL_VARBINARY</para>
            <para>SQL_LONGVARBINARY</para>
          </TD>
          <TD>
            <para>Length of data &lt;= column length</para>
            <para>Length of data &gt; column length</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>