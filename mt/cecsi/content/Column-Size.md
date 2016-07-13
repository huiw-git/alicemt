---
title: Column Size
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Column Size
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The column (or parameter) size of numeric data types is defined as the maximum number of digits used by the data type of the column or parameter, or the precision of the data. For character types, this is the length in characters of the data; for binary data types, column size is defined as the length in bytes of the data. For the time, timestamp, and all interval data types, this is the number of characters in the character representation of this data. The column size defined for each concise SQL data type is shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type identifier</para>
          </TD>
          <TD>
            <para>Column size</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>All character types[a],[b]</para>
          </TD>
          <TD>
            <para>The defined or maximum column size in characters of the column or parameter (as contained in the SQL_DESC_LENGTH descriptor field). For example, the column size of a single-byte character column defined as CHAR(10) is 10.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL SQL_NUMERIC</para>
          </TD>
          <TD>
            <para>The defined number of digits. For example, the precision of a column defined as NUMERIC(10,3) is 10.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT[c]</para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TINYINT[c]</para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SMALLINT[c]</para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTEGER[c]</para>
          </TD>
          <TD>
            <para>10</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIGINT[c]</para>
          </TD>
          <TD>
            <para>19 (if signed) or 20 (if unsigned)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL[c]</para>
          </TD>
          <TD>
            <para>7</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_FLOAT[c]</para>
          </TD>
          <TD>
            <para>15</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DOUBLE[c]</para>
          </TD>
          <TD>
            <para>15</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All binary types[a],[b]</para>
          </TD>
          <TD>
            <para>The defined or maximum length in bytes of the column or parameter. For example, the length of a column defined as BINARY(10) is 10.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE[c]</para>
          </TD>
          <TD>
            <para>10 (the number of characters in the <legacyItalic>yyyy-mm-dd</legacyItalic> format).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME[c]</para>
          </TD>
          <TD>
            <para>8 (the number of characters in the <legacyItalic>hh-mm-ss</legacyItalic> format), or 9 + <legacyItalic>s</legacyItalic> (the number of characters in the <legacyItalic>hh:mm:ss</legacyItalic>[.fff...] format, where <legacyItalic>s</legacyItalic> is the seconds precision).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>16 (the number of characters in the <legacyItalic>yyyy-mm-dd hh:mm</legacyItalic> format)</para>
            <para>19 (the number of characters in the <legacyItalic>yyyy-mm-dd</legacyItalic> <legacyItalic>hh:mm:ss</legacyItalic> format)</para>
            <para>or</para>
            <para>20 + <legacyItalic>s</legacyItalic> (the number of characters in the <legacyItalic>yyyy-mm-dd hh:mm:ss</legacyItalic>[.fff...] format, where <legacyItalic>s</legacyItalic> is the seconds precision).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_SECOND</para>
          </TD>
          <TD>
            <para>Where <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>s</legacyItalic> is the seconds precision, <legacyItalic>p</legacyItalic> (if <legacyItalic>s</legacyItalic>=0) or <legacyItalic>p</legacyItalic>+<legacyItalic>s</legacyItalic>+1 (if <legacyItalic>s</legacyItalic>&gt;0).[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY_TO_SECOND</para>
          </TD>
          <TD>
            <para>Where <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>s</legacyItalic> is the seconds precision, 9+<legacyItalic>p</legacyItalic> (if <legacyItalic>s</legacyItalic>=0) or 10+<legacyItalic>p</legacyItalic>+<legacyItalic>s</legacyItalic> (if <legacyItalic>s</legacyItalic>&gt;0).[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_HOUR_TO_SECOND</para>
          </TD>
          <TD>
            <para>Where <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>s</legacyItalic> is the seconds precision, 6+<legacyItalic>p</legacyItalic> (if <legacyItalic>s</legacyItalic>=0) or 7+<legacyItalic>p</legacyItalic>+<legacyItalic>s</legacyItalic> (if <legacyItalic>s</legacyItalic>&gt;0).[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_MINUTE_TO_SECOND</para>
          </TD>
          <TD>
            <para>Where <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>s</legacyItalic> is the seconds precision, 3+<legacyItalic>p</legacyItalic> (if <legacyItalic>s</legacyItalic>=0) or 4+<legacyItalic>p</legacyItalic>+<legacyItalic>s</legacyItalic> (if <legacyItalic>s</legacyItalic>&gt;0).[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_YEAR  SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE</para>
          </TD>
          <TD>
            <para>               <legacyItalic>p</legacyItalic>, where <legacyItalic>p</legacyItalic> is the interval leading precision.[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR</para>
          </TD>
          <TD>
            <para>3+<legacyItalic>p</legacyItalic>, where <legacyItalic>p</legacyItalic> is the interval leading precision.[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY_TO_MINUTE</para>
          </TD>
          <TD>
            <para>6+<legacyItalic>p</legacyItalic>, where <legacyItalic>p</legacyItalic> is the interval leading precision.[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_HOUR_TO_MINUTE</para>
          </TD>
          <TD>
            <para>3+<legacyItalic>p</legacyItalic>, where <legacyItalic>p</legacyItalic> is the interval leading precision.[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_GUID</para>
          </TD>
          <TD>
            <para>36 (the number of characters in the <legacyItalic>aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee</legacyItalic> format)</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   For an ODBC 1.0 application calling <legacyBold>SQLSetParam</legacyBold> in an ODBC 2.0 driver, and for an ODBC 2.0 application calling <legacyBold>SQLBindParameter</legacyBold> in an ODBC 1.0 driver, when *<legacyItalic>StrLen_or_IndPtr</legacyItalic> is SQL_DATA_AT_EXEC for a SQL_LONGVARCHAR or SQL_LONGVARBINARY type, <legacyItalic>ColumnSize</legacyItalic> must be set to the total length of the data to be sent, not the precision as defined in this table.</para>
    <para>[b]   If the driver cannot determine the column or parameter length for a variable type, it returns SQL_NO_TOTAL.</para>
    <para>[c]   The <legacyItalic>ColumnSize</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> is ignored for this data type.</para>
    <para>[d]   For general rules about column length in interval data types, see <legacyLink xlink:href="e9eb38d8-f9db-4401-8c62-aa394054cbbf">Interval Data Type Length</legacyLink>, earlier in this appendix.</para>
    <para>The values returned for the column (or parameter) size do not correspond to the values in any one descriptor field. The values can come from either the SQL_DESC_PRECISION or the SQL_DESC_LENGTH field, depending on the type of data, as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type</para>
          </TD>
          <TD>
            <para>Descriptor field corresponding to</para>
            <para>column or parameter size</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>All character and binary types</para>
          </TD>
          <TD>
            <para>LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All numeric types</para>
          </TD>
          <TD>
            <para>PRECISION</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All datetime and interval types</para>
          </TD>
          <TD>
            <para>LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>LENGTH</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>