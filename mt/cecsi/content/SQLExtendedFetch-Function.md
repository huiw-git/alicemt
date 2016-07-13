---
title: SQLExtendedFetch Function
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLExtendedFetch
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLExtendedFetch Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: Deprecated </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLExtendedFetch</legacyBold> fetches the specified rowset of data from the result set and returns data for all bound columns. Rowsets can be specified at an absolute or relative position or by bookmark.</para>
        <alert class="note">
          <para>In ODBC 3<legacyItalic>.x</legacyItalic>, <legacyBold>SQLExtendedFetch</legacyBold> has been replaced by <legacyBold>SQLFetchScroll</legacyBold>. ODBC 3<legacyItalic>.x</legacyItalic> applications should not call <legacyBold>SQLExtendedFetch</legacyBold>; instead they should call <legacyBold>SQLFetchScroll</legacyBold>. The Driver Manager maps <legacyBold>SQLFetchScroll</legacyBold> to <legacyBold>SQLExtendedFetch</legacyBold> when working with an ODBC 2<legacyItalic>.x</legacyItalic> driver. ODBC 3<legacyItalic>.x</legacyItalic> drivers should support <legacyBold>SQLExtendedFetch</legacyBold> if they want to work with ODBC 2<legacyItalic>.x</legacyItalic> applications that call it. For more information, see "Comments" and <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLExtendedFetch</legacyBold>(
      SQLHSTMT         <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT     <parameterReference>FetchOrientation</parameterReference>,
      SQLLEN           <parameterReference>FetchOffset</parameterReference>,
      SQLULEN *        <parameterReference>RowCountPtr</parameterReference>,
      SQLUSMALLINT *   <parameterReference>RowStatusArray</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FetchOrientation</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of fetch. This is the same as <legacyItalic>FetchOrientation</legacyItalic> in <legacyBold>SQLFetchScroll</legacyBold>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FetchOffset</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Number of the row to fetch. This is the same as <legacyItalic>FetchOffset</legacyItalic> in <legacyBold>SQLFetchScroll</legacyBold>, with one exception. When <legacyItalic>FetchOrientation</legacyItalic> is SQL_FETCH_BOOKMARK, <legacyItalic>FetchOffset</legacyItalic> is a fixed-length bookmark, not an offset from a bookmark. In other words, <legacyBold>SQLExtendedFetch</legacyBold> retrieves the bookmark from this argument, not the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute. It does not support variable-length bookmarks and does not support fetching a rowset at an offset (other than 0) from a bookmark.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RowCountPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the number of rows actually fetched. This buffer is used in the same manner as the buffer specified by the SQL_ATTR_ROWS_FETCHED_PTR statement attribute. This buffer is used only by <legacyBold>SQLExtendedFetch</legacyBold>. It is not used by <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RowStatusArray</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to an array in which to return the status of each row. This array is used in the same manner as the array specified by the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
          <para>However, the address of this array is not stored in the SQL_DESC_STATUS_ARRAY_PTR field in the IRD. Furthermore, this array is used only by <legacyBold>SQLExtendedFetch</legacyBold> and by <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD or <legacyBold>SQLSetPos</legacyBold> when it is called after <legacyBold>SQLExtendedFetch</legacyBold>. It is not used by <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, and it is not used by <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> when they are called after <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. It is also not used when <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD is called before any fetch function is called. In other words, it is used only in statement state S7. It is not used in statement states S5 or S6. For more information, see <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink> in Appendix B: ODBC State Transition Tables.   </para>
          <para>Applications should provide a valid pointer in the <legacyItalic>RowStatusArray</legacyItalic> argument; if not, the behavior of <legacyBold>SQLExtendedFetch</legacyBold> and the behavior of calls to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> after a cursor has been positioned by <legacyBold>SQLExtendedFetch</legacyBold> are undefined. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLExtendedFetch</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLError</legacyBold>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLExtendedFetch</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. If an error occurs on a single column, <legacyBold>SQLGetDiagField</legacyBold> can be called with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_COLUMN_NUMBER to determine the column the error occurred on; and <legacyBold>SQLGetDiagField</legacyBold> can be called with a <legacyItalic>DiagIdentifier</legacyItalic> of SQL_DIAG_ROW_NUMBER to determine the row containing that column.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLSTATE</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>General warning</para>
            </TD>
            <TD>
              <para>Driver-specific informational message. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01004</para>
            </TD>
            <TD>
              <para>String data, right truncated</para>
            </TD>
            <TD>
              <para>String or binary data returned for a column resulted in the truncation of nonblank character or non-NULL binary data. If it was a string value, it was right-truncated. If it was a numeric value, the fractional part of the number was truncated.  (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S01</para>
            </TD>
            <TD>
              <para>Error in row</para>
            </TD>
            <TD>
              <para>An error occurred while fetching one or more rows. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S06</para>
            </TD>
            <TD>
              <para>Attempt to fetch before the result set returned the first rowset</para>
            </TD>
            <TD>
              <para>The requested rowset overlapped the start of the result set when the current position was beyond the first row, and either <legacyItalic>FetchOrientation</legacyItalic> was SQL_PRIOR or <legacyItalic>FetchOrientation</legacyItalic> was SQL_RELATIVE with a negative <legacyItalic>FetchOffset</legacyItalic> whose absolute value was less than or equal to the current SQL_ROWSET_SIZE. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S07</para>
            </TD>
            <TD>
              <para>Fractional truncation</para>
            </TD>
            <TD>
              <para>The data returned for a column was truncated. For numeric data types, the fractional part of the number was truncated. For time, timestamp, and interval data types containing a time component, the fractional portion of the time was truncated. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07006</para>
            </TD>
            <TD>
              <para>Restricted data type attribute violation</para>
            </TD>
            <TD>
              <para>A data value could not be converted to the C data type specified by <legacyItalic>TargetType</legacyItalic> in <legacyBold>SQLBindCol</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07009</para>
            </TD>
            <TD>
              <para>Invalid descriptor index</para>
            </TD>
            <TD>
              <para>Column 0 was bound with <legacyBold>SQLBindCol</legacyBold>, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08S01</para>
            </TD>
            <TD>
              <para>Communication link failure</para>
            </TD>
            <TD>
              <para>The communication link between the driver and the data source to which the driver was connected failed before the function completed processing.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22002</para>
            </TD>
            <TD>
              <para>Indicator variable required but not supplied</para>
            </TD>
            <TD>
              <para>NULL data was fetched into a column whose <legacyItalic>StrLen_or_IndPtr</legacyItalic> set by <legacyBold>SQLBindCol</legacyBold> was a null pointer. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22003</para>
            </TD>
            <TD>
              <para>Numeric value out of range</para>
            </TD>
            <TD>
              <para>Returning the numeric value (as numeric or string) for one or more columns would have caused the whole (as opposed to fractional) part of the number to be truncated. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>For more information, see <legacyLink xlink:href="28a879a1-666e-4183-b731-d36b584d5d86">Guidelines for Interval and Numeric Data Types</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22007</para>
            </TD>
            <TD>
              <para>Invalid datetime format</para>
            </TD>
            <TD>
              <para>A character column in the result set was bound to a date, time, or timestamp C structure, and a value in the column was, respectively, an invalid date, time, or timestamp. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22012</para>
            </TD>
            <TD>
              <para>Division by zero</para>
            </TD>
            <TD>
              <para>A value from an arithmetic expression was returned, which resulted in division by zero. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22015</para>
            </TD>
            <TD>
              <para>Interval field overflow</para>
            </TD>
            <TD>
              <para>Assigning from an exact numeric or interval SQL type to an interval C type caused a loss of significant digits in the leading field.</para>
              <para>When fetching data to an interval C type, there was no representation of the value of the SQL type in the interval C type. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22018</para>
            </TD>
            <TD>
              <para>Invalid character value for cast specification</para>
            </TD>
            <TD>
              <para>The C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type.</para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>Invalid cursor state</para>
            </TD>
            <TD>
              <para>The <legacyItalic>StatementHandle</legacyItalic> was in an executed state, but no result set was associated with the <legacyItalic>StatementHandle</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLError</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY001</para>
            </TD>
            <TD>
              <para>Memory allocation  error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory required to support execution or completion of the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY008</para>
            </TD>
            <TD>
              <para>Operation canceled</para>
            </TD>
            <TD>
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>, and then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLExtendedFetch</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) The specified <legacyItalic>StatementHandle</legacyItalic> was not in an executed state. The function was called without first calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or a catalog function.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) <legacyBold>SQLExtendedFetch</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> after <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> was called and before <legacyBold>SQLFreeStmt</legacyBold> was called with the SQL_CLOSE option.</para>
              <para>(DM) <legacyBold>SQLBulkOperations</legacyBold> was called for a statement before <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLExtendedFetch</legacyBold> was called, and then <legacyBold>SQLExtendedFetch</legacyBold> was called before <legacyBold>SQLFreeStmt</legacyBold> was called with the SQL_CLOSE option.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY013</para>
            </TD>
            <TD>
              <para>Memory management error</para>
            </TD>
            <TD>
              <para>The function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY106</para>
            </TD>
            <TD>
              <para>Fetch type out of range</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>FetchOrientation</legacyItalic> was invalid. (See "Comments.")</para>
              <para>The argument <legacyItalic>FetchOrientation</legacyItalic> was SQL_FETCH_BOOKMARK, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
              <para>The value of the SQL_CURSOR_TYPE statement option was SQL_CURSOR_FORWARD_ONLY, and the value of argument <legacyItalic>FetchOrientation</legacyItalic> was not SQL_FETCH_NEXT. </para>
              <para>The argument <legacyItalic>FetchOrientation</legacyItalic> was SQL_FETCH_RESUME.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY107</para>
            </TD>
            <TD>
              <para>Row value out of range</para>
            </TD>
            <TD>
              <para>The value specified with the SQL_CURSOR_TYPE statement option was SQL_CURSOR_KEYSET_DRIVEN, but the value specified with the SQL_KEYSET_SIZE statement attribute was greater than 0 and less than the value specified with the SQL_ROWSET_SIZE statement attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY111</para>
            </TD>
            <TD>
              <para>Invalid bookmark value</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>FetchOrientation</legacyItalic> was SQL_FETCH_BOOKMARK, and the bookmark specified in the <legacyItalic>FetchOffset</legacyItalic> argument was not valid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY117</para>
            </TD>
            <TD>
              <para>Connection is suspended due to unknown transaction state. Only disconnect and read-only functions are allowed.</para>
            </TD>
            <TD>
              <para>(DM) For more information about suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYC00</para>
            </TD>
            <TD>
              <para>Optional feature not implemented</para>
            </TD>
            <TD>
              <para>Driver or data source does not support the specified fetch type.</para>
              <para>The driver or data source does not support the conversion specified by the combination of the <legacyItalic>TargetType</legacyItalic> in <legacyBold>SQLBindCol</legacyBold> and the SQL data type of the corresponding column. This error applies only when the SQL data type of the column was mapped to a driver-specific SQL data type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT00</para>
            </TD>
            <TD>
              <para>Timeout expired</para>
            </TD>
            <TD>
              <para>The query timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtOption</legacyBold>, SQL_QUERY_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT01</para>
            </TD>
            <TD>
              <para>Connection timeout expired</para>
            </TD>
            <TD>
              <para>The connection timeout period expired before the data source responded to the request. The connection timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_CONNECTION_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM001</para>
            </TD>
            <TD>
              <para>Driver does not support this function</para>
            </TD>
            <TD>
              <para>(DM) The driver associated with the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The behavior of <legacyBold>SQLExtendedFetch</legacyBold> is identical to that of <legacyBold>SQLFetchScroll</legacyBold>, with the following exceptions:  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> use different methods to return the number of rows fetched. <legacyBold>SQLExtendedFetch</legacyBold> returns the number of rows fetched in <legacyItalic>*RowCountPtr</legacyItalic>; <legacyBold>SQLFetchScroll</legacyBold> returns the number of rows fetched directly to the buffer pointed to by SQL_ATTR_ROWS_FETCHED_PTR. For more information, see the <legacyItalic>RowCountPtr</legacyItalic> argument.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> return the status of each row in different arrays. For more information, see the <legacyItalic>RowStatusArray</legacyItalic> argument.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> use different methods to retrieve the bookmark when <legacyItalic>FetchOrientation</legacyItalic> is SQL_FETCH_BOOKMARK. <legacyBold>SQLExtendedFetch</legacyBold> does not support variable-length bookmarks or fetching rowsets at an offset other than 0 from a bookmark. For more information, see the <legacyItalic>FetchOffset</legacyItalic> argument.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> use different rowset sizes. <legacyBold>SQLExtendedFetch</legacyBold> uses the value of the SQL_ROWSET_SIZE statement attribute, and <legacyBold>SQLFetchScroll</legacyBold> uses the value of the SQL_ATTR_ROW_ARRAY_SIZE statement attribute.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> has slightly different error handling semantics than <legacyBold>SQLFetchScroll</legacyBold>. For more information, see "Error Handling" in the "Comments" section of <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLExtendedFetch</legacyBold> does not support binding offsets (the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute).</para>
        </listItem>
        <listItem>
          <para>Calls to <legacyBold>SQLExtendedFetch</legacyBold> cannot be mixed with calls to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, and if <legacyBold>SQLBulkOperations</legacyBold> is called before any fetch function is called, <legacyBold>SQLExtendedFetch</legacyBold> cannot be called until the cursor is closed and reopened. That is, <legacyBold>SQLExtendedFetch</legacyBold> can be called only in statement state S7. For more information, see <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink> in Appendix B: ODBC State Transition Tables.</para>
        </listItem>
      </list>
      <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> while using an ODBC 2<legacyItalic>.x</legacyItalic> driver, the Driver Manager maps this call to <legacyBold>SQLExtendedFetch</legacyBold>. For more information, see "SQLFetchScroll and ODBC 2<legacyItalic>.x</legacyItalic> Drivers" in <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink>.</para>
      <para>In ODBC 2<legacyItalic>.x</legacyItalic>, <legacyBold>SQLExtendedFetch</legacyBold> was called to fetch multiple rows and <legacyBold>SQLFetch</legacyBold> was called to fetch a single row. In ODBC 3<legacyItalic>.x</legacyItalic>, on the other hand, <legacyBold>SQLFetch</legacyBold> can be called to fetch multiple rows.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Binding a buffer to a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Performing bulk insert, update, or delete operations</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the number of result set columns</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Positioning the cursor, refreshing data in the rowset, or updating or deleting data in the result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>