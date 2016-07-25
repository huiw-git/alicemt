---
title: "C Data Types"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
caps.latest.revision: 17
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC C data types indicate the data type of C buffers used to store data in the application.</para>
    <para>All drivers must support all C data types. This is required because all drivers must support all C types to which SQL types that they support can be converted, and all drivers support at least one character SQL type. Because the character SQL type can be converted to and from all C types, all drivers must support all C types.</para>
    <para>The C data type is specified in the <legacyBold>SQLBindCol </legacyBold>and <legacyBold>SQLGetData</legacyBold> functions with the <legacyItalic>TargetType</legacyItalic> argument and in the <legacyBold>SQLBindParameter</legacyBold> function with the <legacyItalic>ValueType</legacyItalic> argument. It can also be specified by calling <legacyBold>SQLSetDescField</legacyBold> to set the SQL_DESC_CONCISE_TYPE field of an ARD or APD, or by calling <legacyBold>SQLSetDescRec</legacyBold> with the <legacyItalic>Type</legacyItalic> argument (and the <legacyItalic>SubType</legacyItalic> argument if needed) and the <legacyItalic>DescriptorHandle</legacyItalic> argument set to the handle of an ARD or APD.</para>
    <para>The following table lists valid type identifiers for the C data types. The table also lists the ODBC C data type that corresponds to each identifier and the definition of this data type.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>C type identifier</para>
          </TD>
          <TD>
            <para>ODBC C typedef</para>
          </TD>
          <TD>
            <para>C type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>SQLCHAR *</para>
          </TD>
          <TD>
            <para>unsigned char *</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_WCHAR</para>
          </TD>
          <TD>
            <para>SQLWCHAR *</para>
          </TD>
          <TD>
            <para>wchar_t *</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_SSHORT[j]</para>
          </TD>
          <TD>
            <para>SQLSMALLINT</para>
          </TD>
          <TD>
            <para>short int</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_USHORT[j]</para>
          </TD>
          <TD>
            <para>SQLUSMALLINT</para>
          </TD>
          <TD>
            <para>unsigned short int</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_SLONG[j]</para>
          </TD>
          <TD>
            <para>SQLINTEGER</para>
          </TD>
          <TD>
            <para>long int</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_ULONG[j]</para>
          </TD>
          <TD>
            <para>SQLUINTEGER</para>
          </TD>
          <TD>
            <para>unsigned long int</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_FLOAT</para>
          </TD>
          <TD>
            <para>SQLREAL</para>
          </TD>
          <TD>
            <para>float</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_DOUBLE</para>
          </TD>
          <TD>
            <para>SQLDOUBLE, SQLFLOAT</para>
          </TD>
          <TD>
            <para>double</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BIT</para>
          </TD>
          <TD>
            <para>SQLCHAR</para>
          </TD>
          <TD>
            <para>unsigned char</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_STINYINT[j]</para>
          </TD>
          <TD>
            <para>SQLSCHAR</para>
          </TD>
          <TD>
            <para>signed char</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_UTINYINT[j]</para>
          </TD>
          <TD>
            <para>SQLCHAR</para>
          </TD>
          <TD>
            <para>unsigned char</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_SBIGINT</para>
          </TD>
          <TD>
            <para>SQLBIGINT</para>
          </TD>
          <TD>
            <para>_int64[h]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_UBIGINT</para>
          </TD>
          <TD>
            <para>SQLUBIGINT</para>
          </TD>
          <TD>
            <para>unsigned _int64[h]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BINARY</para>
          </TD>
          <TD>
            <para>SQLCHAR *</para>
          </TD>
          <TD>
            <para>unsigned char *</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BOOKMARK[i]</para>
          </TD>
          <TD>
            <para>BOOKMARK</para>
          </TD>
          <TD>
            <para>unsigned long int[d]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_VARBOOKMARK</para>
          </TD>
          <TD>
            <para>SQLCHAR *</para>
          </TD>
          <TD>
            <para>unsigned char *</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_DATE[c]</para>
          </TD>
          <TD>
            <para>SQL_DATE_STRUCT</para>
          </TD>
          <TD>
            <code>struct tagDATE_STRUCT {
   SQLSMALLINT year;
   SQLUSMALLINT month;
   SQLUSMALLINT day;  
} DATE_STRUCT;[a]</code>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIME[c]</para>
          </TD>
          <TD>
            <para>SQL_TIME_STRUCT</para>
          </TD>
          <TD>
            <code>struct tagTIME_STRUCT {
   SQLUSMALLINT hour;
   SQLUSMALLINT minute;
   SQLUSMALLINT second;
} TIME_STRUCT;[a]</code>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_TYPE_TIMESTAMP[c]</para>
          </TD>
          <TD>
            <para>SQL_TIMESTAMP_STRUCT</para>
          </TD>
          <TD>
            <code>struct tagTIMESTAMP_STRUCT {
   SQLSMALLINT year;
   SQLUSMALLINT month;
   SQLUSMALLINT day;
   SQLUSMALLINT hour;
   SQLUSMALLINT minute;
   SQLUSMALLINT second;
   SQLUINTEGER fraction;[b] 
} TIMESTAMP_STRUCT;[a]</code>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_NUMERIC</para>
          </TD>
          <TD>
            <para>SQL_NUMERIC_STRUCT</para>
          </TD>
          <TD>
            <code>struct tagSQL_NUMERIC_STRUCT {
   SQLCHAR precision;
   SQLSCHAR scale;
   SQLCHAR sign[g];
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f] 
} SQL_NUMERIC_STRUCT;</code>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_GUID</para>
          </TD>
          <TD>
            <para>SQLGUID</para>
          </TD>
          <TD>
            <code>struct tagSQLGUID {
   DWORD Data1;
   WORD Data2;
   WORD Data3;
   BYTE Data4[8];
} SQLGUID;[k]</code>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All C interval data types</para>
          </TD>
          <TD>
            <para>SQL_INTERVAL_STRUCT</para>
          </TD>
          <TD>
            <para>See the <legacyLink xlink:href="52b42b56-50aa-4ce6-8d79-0963c7a71437">C Interval Structure</legacyLink> section, later in this appendix.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The values of the year, month, day, hour, minute, and second fields in the datetime C data types must conform to the constraints of the Gregorian calendar. (See <legacyLink xlink:href="70667410-c582-4369-8e06-9d98e21cd2bf">Constraints of the Gregorian Calendar</legacyLink> later in this appendix.)</para>
    <para>[b]   The value of the fraction field is the number of billionths of a second and ranges from 0 through 999,999,999 (1 less than 1 billion). For example, the value of the fraction field for a half-second is 500,000,000, for a thousandth of a second (one millisecond) is 1,000,000, for a millionth of a second (one microsecond) is 1,000, and for a billionth of a second (one nanosecond) is 1.</para>
    <para>[c]   In ODBC 2.<legacyItalic>x</legacyItalic>, the C date, time, and timestamp data types are SQL_C_DATE, SQL_C_TIME, and SQL_C_TIMESTAMP.</para>
    <para>[d]   ODBC 3<legacyItalic>.x</legacyItalic> applications should use SQL_C_VARBOOKMARK, not SQL_C_BOOKMARK. When an ODBC 3<legacyItalic>.x</legacyItalic> application works with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager will map SQL_C_VARBOOKMARK to SQL_C_BOOKMARK.</para>
    <para>[e]   A number is stored in the <legacyItalic>val</legacyItalic> field of the SQL_NUMERIC_STRUCT structure as a scaled integer, in little endian mode (the leftmost byte being the least-significant byte). For example, the number 10.001 base 10, with a scale of 4, is scaled to an integer of 100010. Because this is 186AA in hexadecimal format, the value in SQL_NUMERIC_STRUCT would be "AA 86 01 00 00 ... 00", with the number of bytes defined by the SQL_MAX_NUMERIC_LEN <legacyBold>#define</legacyBold>.</para>
    <para>For more information about <languageKeyword>SQL_NUMERIC_STRUCT</languageKeyword>, see <externalLink><linkText>HOWTO: Retrieving Numeric Data with SQL_NUMERIC_STRUCT</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=147596</linkUri></externalLink> and <externalLink><linkText>INF: How to Use SQL_C_NUMERIC Data Type with Numeric Data</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=147597</linkUri></externalLink>.</para>
    <para>[f]   The precision and scale fields of the SQL_C_NUMERIC data type areused for input from an application and for output from the driver to the application. When the driver writes a numeric value into the SQL_NUMERIC_STRUCT, it will use its own driver-specific default as the value for the <legacyItalic>precision</legacyItalic> field, and it will use the value in the SQL_DESC_SCALE field of the application descriptor (which defaults to 0) for the <legacyItalic>scale</legacyItalic> field. An application can provide its own values for precision and scale by setting the SQL_DESC_PRECISION and SQL_DESC_SCALE fields of the application descriptor.</para>
    <para>[g]   The sign field is 1 if positive, 0 if negative.</para>
    <para>[h]   _int64 might not be supplied by some compilers.</para>
    <para>[i]   _SQL_C_BOOKMARK has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>.</para>
    <para>[j]   _SQL_C_SHORT, SQL_C_LONG, and SQL_C_TINYINT have been replaced in ODBC by signed and unsigned types: SQL_C_SSHORT and SQL_C_USHORT, SQL_C_SLONG and SQL_C_ULONG, and SQL_C_STINYINT and SQL_C_UTINYINT. An ODBC 3<legacyItalic>.x</legacyItalic> driver that should work with ODBC 2.<legacyItalic>x</legacyItalic> applications should support SQL_C_SHORT, SQL_C_LONG, and SQL_C_TINYINT, because when they are called, the Driver Manager passes them through to the driver.</para>
    <para>[k]   SQL_C_GUID can be converted only to SQL_CHAR or SQL_WCHAR.</para>
    <para>This section contains the following topic. </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="ac80c798-d9b2-4430-85ed-bd2461db0ac7">64-Bit Integer Structures</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>