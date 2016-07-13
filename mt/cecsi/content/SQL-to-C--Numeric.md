---
title: SQL to C: Numeric
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76f8b5d5-4bd0-4dcb-a90a-698340e0d36e
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL to C: Numeric
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifiers for the numeric ODBC SQL data types are:</para>
    <para>SQL_DECIMAL</para>
    <para>SQL_BIGINT </para>
    <para>SQL_NUMERIC</para>
    <para>SQL_REAL</para>
    <para>SQL_TINYINT</para>
    <para>SQL_FLOAT</para>
    <para>SQL_SMALLINT</para>
    <para>SQL_DOUBLE SQL_INTEGER</para>
    <para>The following table shows the ODBC C data types to which numeric SQL data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>.</para>
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
            <para>Character byte length &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
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
            <para>Character length &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &lt; <legacyItalic>BufferLength</legacyItalic></para>
            <para>Number of whole (as opposed to fractional) digits &gt;= <legacyItalic>BufferLength</legacyItalic></para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
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
            <para>SQL_C_NUMERIC</para>
          </TD>
          <TD>
            <para>Data converted without truncation[a]</para>
            <para>Data converted with truncation of fractional digits[a]</para>
            <para>Conversion of data would result in loss of whole (as opposed to fractional) digits[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Size of the C data type</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_FLOAT</para>
            <para>SQL_C_DOUBLE</para>
          </TD>
          <TD>
            <para>Data is within the range of the data type to which the number is being converted[a]</para>
            <para>Data is outside the range of the data type to which the number is being converted[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Size of the C data type</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_BIT</para>
          </TD>
          <TD>
            <para>Data is 0 or 1[a]</para>
            <para>Data is greater than 0, less than 2, and not equal to 1[a]</para>
            <para>Data is less than 0 or greater than or equal to 2[a]</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>1[b]</para>
            <para>1[b]</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
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
            <para>Length of data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22003</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_INTERVAL_MONTH[c] SQL_C_INTERVAL_YEAR[c] SQL_C_INTERVAL_DAY[c] SQL_C_INTERVAL_HOUR[c] SQL_C_INTERVAL_MINUTE[c] SQL_C_INTERVAL_SECOND[c]</para>
          </TD>
          <TD>
            <para>Data not truncated</para>
            <para>Fractional seconds portion truncated</para>
            <para>Whole part of number truncated</para>
          </TD>
          <TD>
            <para>Data</para>
            <para>Truncated data</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Length of data in bytes</para>
            <para>Length of data in bytes</para>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>01S07</para>
            <para>22015</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND</para>
          </TD>
          <TD>
            <para>Whole part of number truncated</para>
          </TD>
          <TD>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>Undefined</para>
          </TD>
          <TD>
            <para>22015</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The value of <legacyItalic>BufferLength</legacyItalic> is ignored for this conversion. The driver assumes that the size of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the C data type.</para>
    <para>[b]   This is the size of the corresponding C data type.</para>
    <para>[c]   This conversion is supported only for the exact numeric data types (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, and SQL_BIGINT). It is not supported for the approximate numeric data types (SQL_REAL, SQL_FLOAT, or SQL_DOUBLE).</para>
  </introduction>
  <section>
    <title>SQL_C_NUMERIC and SQLSetDescField</title>
    <content>
      <para>The <link xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</link> is required to perform manual binding with SQL_C_NUMERIC values. (Note that SQLSetDescField was added in ODBC 3.0.) To perform manual binding, you must first get the descriptor handle.</para>
      <code>if (fCType == SQL_C_NUMERIC) { 
   // special processing required for NUMERIC to get right scale &amp; precision
   // Modify the fields in the implicit application parameter descriptor
   SQLHDESC hdesc=NULL;

   // Use SQL_ATTR_APP_ROW_DESC for calls to SQLBindCol()
   // Use SQL_ATTR_APP_PARAM_DESC for calls to SQLBindParameter()
   //
   // retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_ROW_DESC, &amp;hdesc, 0, NULL);
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &amp;hdesc, 0, NULL);
   if (!ODBC_CALL_SUCCESS(retcode)) {
      printf ("\nSQLGetStmtAttr failed");
      i = 1;
      sqlstate[7] = '\0';
      while (SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, sqlstate, &amp;NativeError, wrkbuf, sizeof(wrkbuf), &amp;len) != SQL_NO_DATA) {
         printf("\niTestCase = %d Failed...Precision = %d, Scale = %d\nNativeError=%d, State=%s, \n  Message=%s", 
            iTestCase, Precision, Scale, NativeError, sqlstate, wrkbuf);
         i++;
      }
      continue;
   }
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);
   if (!ODBC_CALL_SUCCESS(retcode))
      goto error;
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_PRECISION, (SQLPOINTER)num.precision, 0);
   if (!ODBC_CALL_SUCCESS(retcode))
      goto error;
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_SCALE, (SQLPOINTER)num.scale, 0);
   if (!ODBC_CALL_SUCCESS(retcode))
      goto error;
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_DATA_PTR, (SQLPOINTER) &amp;(num), sizeof(num));</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>