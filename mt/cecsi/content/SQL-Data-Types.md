---
title: SQL Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each DBMS defines its own SQL types. Each ODBC driver exposes only those SQL data types that the associated DBMS defines. Information about how a driver maps DBMS SQL types to the ODBC-defined SQL type identifiers and how a driver maps DBMS SQL types to its own driver-specific SQL type identifiers is returned through a call to <legacyBold>SQLGetTypeInfo</legacyBold>. A driver also returns the SQL data types when describing the data types of columns and parameters through calls to <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLDescribeParam</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, and <legacyBold>SQLSpecialColumns</legacyBold>.</para>
    <alert class="note">
      <para>The SQL data types are contained in the SQL_DESC_ CONCISE_TYPE, SQL_DESC_TYPE, and SQL_DESC_DATETIME_INTERVAL_CODE fields of the implementation descriptors. Characteristics of the SQL data types are contained in the SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, and SQL_DESC_OCTET_LENGTH fields of the implementation descriptors. For more information, see <legacyLink xlink:href="f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab">Data Type Identifiers and Descriptors</legacyLink> later in this appendix.</para>
    </alert>
    <para>A given driver and data source do not necessarily support all the SQL data types that are defined in this appendix. A driver's support for SQL data types depends on the level of SQL-92 that the driver complies with. To determine the level of SQL-92 grammar supported by the driver, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL_CONFORMANCE information type. Additionally, a given driver and data source may support additional, driver-specific SQL data types. To determine which data types a driver supports, an application calls <legacyBold>SQLGetTypeInfo</legacyBold>. For information about driver-specific SQL data types, see the driver's documentation. For information about the data types in a specific data source, see the documentation for that data source.</para>
    <alert class="important">
      <para>The tables throughout this appendix are only guidelines and show typically used names, ranges, and limits of SQL data types. A given data source might support only some of the listed data types, and the characteristics of the supported data types can differ from those listed.</para>
    </alert>
    <para>The following table lists valid SQL type identifiers for all SQL data types. The table also lists the name and description of the corresponding data type from SQL-92 (if one exists).</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type identifier[1]</para>
          </TD>
          <TD>
            <para>Typical SQL data</para>
            <para>type[2]</para>
          </TD>
          <TD>
            <para>Typical type description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_CHAR</para>
          </TD>
          <TD>
            <para>CHAR(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Character string of fixed string length <legacyItalic>n</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_VARCHAR</para>
          </TD>
          <TD>
            <para>VARCHAR(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Variable-length character string with a maximum string length <legacyItalic>n</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LONGVARCHAR</para>
          </TD>
          <TD>
            <para>LONG VARCHAR</para>
          </TD>
          <TD>
            <para>Variable length character data. Maximum length is data source–dependent.[9]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
          </TD>
          <TD>
            <para>WCHAR(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Unicode character string of fixed string length <legacyItalic>n</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WVARCHAR</para>
          </TD>
          <TD>
            <para>VARWCHAR(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Unicode variable-length character string with a maximum string length <legacyItalic>n</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WLONGVARCHAR</para>
          </TD>
          <TD>
            <para>LONGWVARCHAR</para>
          </TD>
          <TD>
            <para>Unicode variable-length character data. Maximum length is data source–dependent</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DECIMAL</para>
          </TD>
          <TD>
            <para>DECIMAL(<legacyItalic>p</legacyItalic>,<legacyItalic>s</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Signed, exact, numeric value with a precision of at least <legacyItalic>p</legacyItalic> and scale <legacyItalic>s. </legacyItalic>(The maximum precision is driver-defined.) (1 &lt;= <legacyItalic>p</legacyItalic> &lt;= 15; <legacyItalic>s</legacyItalic> &lt;= <legacyItalic>p</legacyItalic>).[4]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_NUMERIC</para>
          </TD>
          <TD>
            <para>NUMERIC(<legacyItalic>p</legacyItalic>,<legacyItalic>s</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Signed, exact, numeric value with a precision <legacyItalic>p</legacyItalic> and scale <legacyItalic>s</legacyItalic>  (1 &lt;= <legacyItalic>p</legacyItalic> &lt;= 15; <legacyItalic>s</legacyItalic> &lt;= <legacyItalic>p</legacyItalic>).[4]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SMALLINT</para>
          </TD>
          <TD>
            <para>SMALLINT</para>
          </TD>
          <TD>
            <para>Exact numeric value with precision 5 and scale 0  (signed:  –32,768 &lt;= <legacyItalic>n</legacyItalic> &lt;= 32,767, unsigned:  0 &lt;= <legacyItalic>n</legacyItalic> &lt;= 65,535)[3].</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
          <TD>
            <para>INTEGER</para>
          </TD>
          <TD>
            <para>Exact numeric value with precision 10 and scale 0  (signed:  –2[31] &lt;= <legacyItalic>n</legacyItalic> &lt;= 2[31] – 1, unsigned:  0 &lt;= <legacyItalic>n</legacyItalic> &lt;= 2[32] – 1)[3].</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_REAL</para>
          </TD>
          <TD>
            <para>REAL</para>
          </TD>
          <TD>
            <para>Signed, approximate, numeric value with a binary precision 24 (zero or absolute value 10[–38] to 10[38]).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_FLOAT</para>
          </TD>
          <TD>
            <para>FLOAT(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Signed, approximate, numeric value with a binary precision of at least <legacyItalic>p</legacyItalic>. (The maximum precision is driver-defined.)[5]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DOUBLE</para>
          </TD>
          <TD>
            <para>DOUBLE PRECISION</para>
          </TD>
          <TD>
            <para>Signed, approximate, numeric value with a binary precision 53 (zero or absolute value 10[–308] to 10[308]).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIT</para>
          </TD>
          <TD>
            <para>BIT</para>
          </TD>
          <TD>
            <para>Single bit binary data.[8]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TINYINT</para>
          </TD>
          <TD>
            <para>TINYINT</para>
          </TD>
          <TD>
            <para>Exact numeric value with precision 3 and scale 0  (signed:  –128 &lt;= <legacyItalic>n</legacyItalic> &lt;= 127,  unsigned:  0 &lt;= <legacyItalic>n</legacyItalic> &lt;= 255)[3].</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BIGINT</para>
          </TD>
          <TD>
            <para>BIGINT</para>
          </TD>
          <TD>
            <para>Exact numeric value with precision 19 (if signed) or 20 (if unsigned) and scale 0  (signed:  –2[63] &lt;= <legacyItalic>n</legacyItalic> &lt;= 2[63] – 1,  unsigned: 0 &lt;= <legacyItalic>n</legacyItalic> &lt;= 2[64] – 1)[3],[9].</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_BINARY</para>
          </TD>
          <TD>
            <para>BINARY(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Binary data of fixed length <legacyItalic>n</legacyItalic>.[9]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_VARBINARY</para>
          </TD>
          <TD>
            <para>VARBINARY(<legacyItalic>n</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Variable length binary data of maximum length <legacyItalic>n</legacyItalic>. The maximum is set by the user.[9]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LONGVARBINARY</para>
          </TD>
          <TD>
            <para>LONG VARBINARY</para>
          </TD>
          <TD>
            <para>Variable length binary data. Maximum length is data source–dependent.[9]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE[6]</para>
          </TD>
          <TD>
            <para>DATE</para>
          </TD>
          <TD>
            <para>Year, month, and day fields, conforming to the rules of the Gregorian calendar. (See <legacyLink xlink:href="70667410-c582-4369-8e06-9d98e21cd2bf">Constraints of the Gregorian Calendar</legacyLink>, later in this appendix.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME[6]</para>
          </TD>
          <TD>
            <para>TIME(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Hour, minute, and second fields, with valid values for hours of 00 to 23, valid values for minutes of 00 to 59, and valid values for seconds of 00 to 61. Precision <legacyItalic>p</legacyItalic> indicates the seconds precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP[6]</para>
          </TD>
          <TD>
            <para>TIMESTAMP(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Year, month, day, hour, minute, and second fields, with valid values as defined for the DATE and TIME data types.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_UTCDATETIME</para>
          </TD>
          <TD>
            <para>UTCDATETIME</para>
          </TD>
          <TD>
            <para>Year, month, day, hour, minute, second, utchour, and utcminute fields. The utchour and utcminute fields have 1/10 microsecond precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_UTCTIME</para>
          </TD>
          <TD>
            <para>UTCTIME</para>
          </TD>
          <TD>
            <para>Hour, minute, second, utchour, and utcminute fields. The utchour and utcminute fields have 1/10 microsecond precision..</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_MONTH[7]</para>
          </TD>
          <TD>
            <para>INTERVAL MONTH(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of months between two dates; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_YEAR[7]</para>
          </TD>
          <TD>
            <para>INTERVAL YEAR(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of years between two dates; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_YEAR_TO_MONTH[7]</para>
          </TD>
          <TD>
            <para>INTERVAL YEAR(<legacyItalic>p</legacyItalic>) TO MONTH</para>
          </TD>
          <TD>
            <para>Number of years and months between two dates; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY[7]</para>
          </TD>
          <TD>
            <para>INTERVAL DAY(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of days between two dates; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_HOUR[7]</para>
          </TD>
          <TD>
            <para>INTERVAL HOUR(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of hours between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_MINUTE[7]</para>
          </TD>
          <TD>
            <para>INTERVAL MINUTE(<legacyItalic>p</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of minutes between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_SECOND[7]</para>
          </TD>
          <TD>
            <para>INTERVAL SECOND(<legacyItalic>p</legacyItalic>,<legacyItalic>q</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of seconds between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>q</legacyItalic> is the interval seconds precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY_TO_HOUR[7]</para>
          </TD>
          <TD>
            <para>INTERVAL DAY(<legacyItalic>p</legacyItalic>) TO HOUR</para>
          </TD>
          <TD>
            <para>Number of days/hours between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY_TO_MINUTE[7]</para>
          </TD>
          <TD>
            <para>INTERVAL DAY(<legacyItalic>p</legacyItalic>) TO MINUTE</para>
          </TD>
          <TD>
            <para>Number of days/hours/minutes between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_DAY_TO_SECOND[7]</para>
          </TD>
          <TD>
            <para>INTERVAL DAY(<legacyItalic>p</legacyItalic>) TO SECOND(<legacyItalic>q</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of days/hours/minutes/seconds between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>q</legacyItalic> is the interval seconds precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_HOUR_TO_MINUTE[7]</para>
          </TD>
          <TD>
            <para>INTERVAL HOUR(<legacyItalic>p</legacyItalic>) TO MINUTE</para>
          </TD>
          <TD>
            <para>Number of hours/minutes between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_HOUR_TO_SECOND[7]</para>
          </TD>
          <TD>
            <para>INTERVAL HOUR(<legacyItalic>p</legacyItalic>) TO SECOND(<legacyItalic>q</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of hours/minutes/seconds between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>q</legacyItalic> is the interval seconds precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INTERVAL_MINUTE_TO_SECOND[7]</para>
          </TD>
          <TD>
            <para>INTERVAL MINUTE(<legacyItalic>p</legacyItalic>) TO SECOND(<legacyItalic>q</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Number of minutes/seconds between two date/times; <legacyItalic>p</legacyItalic> is the interval leading precision and <legacyItalic>q</legacyItalic> is the interval seconds precision.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_GUID</para>
          </TD>
          <TD>
            <para>GUID</para>
          </TD>
          <TD>
            <para>Fixed length GUID.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   This is the value returned in the DATA_TYPE column by a call to <legacyBold>SQLGetTypeInfo</legacyBold>.</para>
    <para>[2]   This is the value returned in the NAME and CREATE PARAMS column by a call to <legacyBold>SQLGetTypeInfo</legacyBold>. The NAME column returns the designation—for example, CHAR—whereas the CREATE PARAMS column returns a comma-separated list of creation parameters such as precision, scale, and length.</para>
    <para>[3]   An application uses <legacyBold>SQLGetTypeInfo</legacyBold> or <legacyBold>SQLColAttribute</legacyBold> to determine whether a particular data type or a particular column in a result set is unsigned.</para>
    <para>[4]   SQL_DECIMAL and SQL_NUMERIC data types differ only in their precision. The precision of a DECIMAL(<legacyItalic>p</legacyItalic>,<legacyItalic>s</legacyItalic>) is an implementation-defined decimal precision that is no less than <legacyItalic>p</legacyItalic>, whereas the precision of a NUMERIC(<legacyItalic>p</legacyItalic>,<legacyItalic>s</legacyItalic>) is exactly equal to <legacyItalic>p</legacyItalic>.</para>
    <para>[5]   Depending on the implementation, the precision of SQL_FLOAT can be either 24 or 53: if it is 24, the SQL_FLOAT data type is the same as SQL_REAL; if it is 53, the SQL_FLOAT data type is the same as SQL_DOUBLE.</para>
    <para>[6]   In ODBC 3<legacyItalic>.x</legacyItalic>, the SQL date, time, and timestamp data types are SQL_TYPE_DATE, SQL_TYPE_TIME, and SQL_TYPE_TIMESTAMP, respectively; in ODBC 2.<legacyItalic>x</legacyItalic>, the data types are SQL_DATE, SQL_TIME, and SQL_TIMESTAMP.</para>
    <para>[7]   For more information about the interval SQL data types, see the <legacyLink xlink:href="fba93f65-c1db-44f4-91ba-532f87241cf7">Interval Data Types</legacyLink> section, later in this appendix.</para>
    <para>[8]   The SQL_BIT data type has different characteristics than the BIT type in SQL-92.</para>
    <para>[9]   This data type has no corresponding data type in SQL-92.</para>
    <para>This section provides the following example.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="dc1952cc-7581-4d69-9c72-7dc1cd370836">Example SQLGetTypeInfo Result Set</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>