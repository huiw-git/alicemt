---
title: Explicit Data Type Conversion Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Explicit Data Type Conversion Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Explicit data type conversion is specified in terms of SQL data type definitions.</para>
  </introduction>
  <section>
    <content>
      <para>The ODBC syntax for the explicit data type conversion function does not restrict conversions. The validity of specific conversions of one data type to another data type will be determined by each driver-specific implementation. The driver will, as it translates the ODBC syntax into the native syntax, reject those conversions that, although legal in the ODBC syntax, are not supported by the data source. The ODBC function <legacyBold>SQLGetInfo</legacyBold>, with the conversion options (such as SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH, and so on), provides a way to inquire about conversions supported by the data source.</para>
      <para>The format of the <legacyBold>CONVERT</legacyBold> function is:</para>
      <para>
        <legacyBold>CONVERT(</legacyBold>
        <legacyItalic>value_exp</legacyItalic>, <legacyItalic>data_type</legacyItalic><legacyBold>)</legacyBold></para>
      <para>The function returns the value specified by <legacyItalic>value_exp</legacyItalic> converted to the specified <legacyItalic>data_type</legacyItalic>, where <legacyItalic>data_type</legacyItalic> is one of the following keywords:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_BIGINT</para>
            </TD>
            <TD>
              <para>SQL_INTERVAL_HOUR_TO_MINUTE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BINARY</para>
            </TD>
            <TD>
              <para>SQL_INTERVAL_HOUR_TO_SECOND </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BIT</para>
            </TD>
            <TD>
              <para>SQL_INTERVAL_MINUTE_TO_SECOND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CHAR</para>
            </TD>
            <TD>
              <para>SQL_LONGVARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DECIMAL</para>
            </TD>
            <TD>
              <para>SQL_LONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DOUBLE</para>
            </TD>
            <TD>
              <para>SQL_NUMERIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FLOAT</para>
            </TD>
            <TD>
              <para>SQL_REAL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GUID</para>
            </TD>
            <TD>
              <para>SQL_SMALLINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTEGER</para>
            </TD>
            <TD>
              <para>SQL_DATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_MONTH</para>
            </TD>
            <TD>
              <para>SQL_TIME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_YEAR </para>
            </TD>
            <TD>
              <para>SQL_TIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_YEAR_TO_MONTH </para>
            </TD>
            <TD>
              <para>SQL_TINYINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_DAY </para>
            </TD>
            <TD>
              <para>SQL_VARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_HOUR </para>
            </TD>
            <TD>
              <para>SQL_VARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_MINUTE </para>
            </TD>
            <TD>
              <para>SQL_WCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_SECOND </para>
            </TD>
            <TD>
              <para>SQL_WLONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_DAY_TO_HOUR </para>
            </TD>
            <TD>
              <para>SQL_WVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_DAY_TO_MINUTE </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTERVAL_DAY_TO_SECOND </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The ODBC syntax for the explicit data type conversion function does not support specification of conversion format. If specification of explicit formats is supported by the underlying data source, a driver must specify a default value or implement format specification.</para>
      <para>The argument <legacyItalic>value_exp</legacyItalic> can be a column name, the result of another scalar function, or a numeric or string literal. For example:</para>
      <code>{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }</code>
      <para>converts the output of the CURDATE scalar function to a character string.</para>
      <para>Because ODBC does not mandate a data type for return values from scalar functions (because the functions are often data source–specific), applications should use the CONVERT scalar function whenever possible to force data type conversion.</para>
      <para>The following two examples illustrate the use of the <legacyBold>CONVERT</legacyBold> function. These examples assume the existence of a table called EMPLOYEES, with an EMPNO column of type SQL_SMALLINT and an EMPNAME column of type SQL_CHAR. </para>
      <para>If an application specifies the following SQL statement:</para>
      <code>SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'</code>
      <list class="bullet">
        <listItem>
          <para>A driver for ORACLE translates the SQL statement to:
</para>
          <code>SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'</code>
        </listItem>
        <listItem>
          <para>A driver for SQL Server translates the SQL statement to:
</para>
          <code>SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'</code>
        </listItem>
      </list>
      <para>If an application specifies the following SQL statement:</para>
      <code>SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}
   FROM EMPLOYEES WHERE EMPNO &lt;&gt; 0</code>
      <list class="bullet">
        <listItem>
          <para>A driver for ORACLE translates the SQL statement to:
</para>
          <code>SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO &lt;&gt; 0</code>
        </listItem>
        <listItem>
          <para>A driver for SQL Server translates the SQL statement to:
</para>
          <code>SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES
   WHERE EMPNO &lt;&gt; 0</code>
        </listItem>
        <listItem>
          <para>A driver for Ingres translates the SQL statement to:
</para>
          <code>SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO &lt;&gt; 0</code>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>