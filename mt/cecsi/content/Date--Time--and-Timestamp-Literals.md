---
title: Date, Time, and Timestamp Literals
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Date, Time, and Timestamp Literals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The escape sequence for date, time, and timestamp literals is</para>
    <para>
      <legacyBold>{</legacyBold>
      <legacyItalic> -type</legacyItalic> <legacyBold>'</legacyBold><legacyItalic>value</legacyItalic><legacyBold>'}</legacyBold></para>
    <para>where <legacyItalic>literal-type</legacyItalic> is one of the values listed in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>
              <legacyItalic>literal-type</legacyItalic> </para>
          </TD>
          <TD>
            <para>Meaning</para>
          </TD>
          <TD>
            <para>Format of <legacyItalic>value</legacyItalic></para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>d</legacyBold> </para>
          </TD>
          <TD>
            <para>Date</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>t</legacyBold> </para>
          </TD>
          <TD>
            <para>Time*</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>ts</legacyBold> </para>
          </TD>
          <TD>
            <para>Timestamp</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic> <legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>[.<legacyItalic>f...</legacyItalic>][1]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   The number of digits to the right of the decimal point in a time or timestamp interval literal containing a seconds component is dependent on the seconds precision, as contained in the SQL_DESC_PRECISION descriptor field. (For more information, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.)</para>
    <para>For more information about the date, time, and timestamp escape sequences, see <legacyLink xlink:href="67b7dee0-e5b1-4469-a626-0c7767852b80">Date, Time, and Timestamp Escape Sequences</legacyLink> in Appendix C: SQL Grammar.</para>
    <para>For example, both of the following SQL statements update the open date of sales order 1023 in the Orders table. The first statement uses the escape sequence syntax. The second statement uses the Oracle Rdb native syntax for the DATE column and is not interoperable.</para>
    <code>UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023</code>
    <para>The escape sequence for a date, time, or timestamp literal also can be placed in a character variable bound to a date, time, or timestamp parameter. For example, the following code uses a date parameter bound to a character variable to update the open date of sales order 1023 in the Orders table:</para>
    <code>SQLCHAR      OpenDate[56]; // The size of a date literal is 55.
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;

// Bind the parameter.
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,
                  OpenDate, sizeof(OpenDate), &amp;OpenDateLenOrInd);

// Place the date in the OpenDate variable. In addition to the escape
// sequence shown, it would also be possible to use either of the
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter
// is data source-specific.
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");

// Execute the statement.
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);</code>
    <para>However, it is usually more efficient to bind the parameter directly to a date structure:</para>
    <code>SQL_DATE_STRUCT   OpenDate;
SQLINTEGER        OpenDateInd = 0;

// Bind the parameter.
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,
                  &amp;OpenDate, 0, &amp;OpenDateLen);

// Place the date in the dsOpenDate structure.
OpenDate.year = 1995;
OpenDate.month = 1;
OpenDate.day = 15;

// Execute the statement.
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);</code>
    <para>To determine whether a driver supports the ODBC escape sequences for date, time, or timestamp literals, an application calls <legacyBold>SQLGetTypeInfo</legacyBold>. If the data source supports a date, time, or timestamp data type, it must also support the corresponding escape sequence.</para>
    <para>Data sources can also support the datetime literals defined in the ANSI SQL-92 specification, which are different from the ODBC escape sequences for date, time, or timestamp literals. To determine whether a data source supports the ANSI literals, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_ANSI_SQL_DATETIME_LITERALS option.</para>
    <para>To determine whether a driver supports the ODBC escape sequences for interval literals, an application calls <legacyBold>SQLGetTypeInfo</legacyBold>. If the data source supports a datetime interval data type, it must also support the corresponding escape sequence.</para>
    <para>Data sources can also support the datetime literals defined in the ANSI SQL-92 specification, which are different from the ODBC escape sequences for datetime interval literals. To determine whether a data source supports the ANSI literals, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_ANSI_SQL_DATETIME_LITERALS option.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>