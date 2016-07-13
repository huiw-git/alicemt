---
title: SQLFetchScroll Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLFetchScroll
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFetchScroll Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0 Standards Compliance: ISO 92 </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLFetchScroll</legacyBold> fetches the specified rowset of data from the result set and returns data for all bound columns. Rowsets can be specified at an absolute or relative position or by bookmark.</para>
        <para>When working with an ODBC 2.x driver, the Driver Manager maps this function to <legacyBold>SQLExtendedFetch</legacyBold>. For more information, see <link xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN SQLFetchScroll(
      SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
      SQLSMALLINT   <parameterReference>FetchOrientation</parameterReference>,
      SQLLEN        <parameterReference>FetchOffset</parameterReference>);</legacySyntax>
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
          <para>[Input]</para>
          <para>Type of fetch: </para>
          <para>SQL_FETCH_NEXT</para>
          <para>SQL_FETCH_PRIOR</para>
          <para>SQL_FETCH_FIRST</para>
          <para>SQL_FETCH_LAST</para>
          <para>SQL_FETCH_ABSOLUTE</para>
          <para>SQL_FETCH_RELATIVE</para>
          <para>SQL_FETCH_BOOKMARK </para>
          <para>For more information, see "Positioning the Cursor" in the "Comments" section.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FetchOffset</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input]</para>
          <para>Number of the row to fetch. The interpretation of this argument depends on the value of the <parameterReference>FetchOrientation</parameterReference> argument. For more information, see "Positioning the Cursor" in the "Comments" section.</para>
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
      <para>When <legacyBold>SQLFetchScroll</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a HandleType of SQL_HANDLE_STMT and a Handle of StatementHandle. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLFetchScroll</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. If an error occurs on a single column, <legacyBold>SQLGetDiagField</legacyBold> can be called with a DiagIdentifier of SQL_DIAG_COLUMN_NUMBER to determine the column the error occurred on; and <legacyBold>SQLGetDiagField</legacyBold> can be called with a DiagIdentifier of SQL_DIAG_ROW_NUMBER to determine the row containing that column. </para>
      <para>For all those SQLSTATEs that can return SQL_SUCCESS_WITH_INFO or SQL_ERROR (except 01xxx SQLSTATEs), SQL_SUCCESS_WITH_INFO is returned if an error occurs on one or more, but not all, rows of a multirow operation, and SQL_ERROR is returned if an error occurs on a single-row operation.</para>
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
              <para>String or binary data returned for a column resulted in the truncation of nonblank character or non-NULL binary data. If it was a string value, it was right-truncated.</para>
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
              <para>An error occurred while fetching one or more rows. </para>
              <para>(If this SQLSTATE is returned when an ODBC 3<legacyItalic>.x</legacyItalic> application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, it can be ignored.)</para>
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
              <para>The requested rowset overlapped the start of the result set when FetchOrientation was SQL_FETCH_PRIOR, the current position was beyond the first row, and the number of the current row is less than or equal to the rowset size. </para>
              <para>The requested rowset overlapped the start of the result set when FetchOrientation was SQL_FETCH_PRIOR, the current position was beyond the end of the result set, and the rowset size was greater than the result set size.</para>
              <para>The requested rowset overlapped the start of the result set when FetchOrientation was SQL_FETCH_RELATIVE, FetchOffset was negative, and the absolute value of FetchOffset was less than or equal to the rowset size.</para>
              <para>The requested rowset overlapped the start of the result set when FetchOrientation was SQL_FETCH_ABSOLUTE, FetchOffset was negative, and the absolute value of FetchOffset was greater than the result set size but less than or equal to the rowset size.</para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The data value of a column in the result set could not be converted to the data type specified by <legacyItalic>TargetType</legacyItalic> in <legacyBold>SQLBindCol</legacyBold>.</para>
              <para>Column 0 was bound with a data type of SQL_C_BOOKMARK, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_VARIABLE. </para>
              <para>Column 0 was bound with a data type of SQL_C_VARBOOKMARK, and the SQL_ATTR_USE_BOOKMARKS statement attribute was not set to SQL_UB_VARIABLE.</para>
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
              <para>The driver was an ODBC 2<legacyItalic>.x</legacyItalic> driver that does not support <legacyBold>SQLExtendedFetch</legacyBold>, and a column number specified in the binding for a column was 0. </para>
              <para>Column 0 was bound, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
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
              <para>22001</para>
            </TD>
            <TD>
              <para>String data, right truncated</para>
            </TD>
            <TD>
              <para>A variable-length bookmark returned for a column was truncated.</para>
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
              <para>NULL data was fetched into a column whose <legacyItalic>StrLen_or_IndPtr</legacyItalic> set by <legacyBold>SQLBindCol</legacyBold> (or SQL_DESC_INDICATOR_PTR set by <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>) was a null pointer. </para>
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
              <para>Returning the numeric value (as numeric or string) for one or more bound columns would have caused the whole (as opposed to fractional) part of the number to be truncated.</para>
              <para>For more information, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink> in <link xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</link>.</para>
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
              <para>A character column in the result set was bound to a character C buffer, and the column contained a character for which there was no representation in the character set of the buffer.</para>
              <para>The C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type. </para>
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
              <para>The <legacyItalic>StatementHandle</legacyItalic> was in an executed state but no result set was associated with the <legacyItalic>StatementHandle</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>40001</para>
            </TD>
            <TD>
              <para>Serialization failure</para>
            </TD>
            <TD>
              <para>The transaction in which the fetch was executed was terminated to prevent deadlock.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>40003</para>
            </TD>
            <TD>
              <para>Statement completion unknown</para>
            </TD>
            <TD>
              <para>The associated connection failed during the execution of this function, and the state of the transaction cannot be determined.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause. </para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) The specified <legacyItalic>StatementHandle</legacyItalic> was not in an executed state. The function was called without first calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold> or a catalog function.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) <legacyBold>SQLFetch</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> after <legacyBold>SQLExtendedFetch</legacyBold> was called and before <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option was called.</para>
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
              <para>HY090</para>
            </TD>
            <TD>
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>The SQL_ATTR_USE_BOOKMARK statement attribute was set to SQL_UB_VARIABLE, and column 0 was bound to a buffer whose length was not equal to the maximum length for the bookmark for this result set. (This length is available in the SQL_DESC_OCTET_LENGTH field of the IRD and can be obtained by calling <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLColAttribute</legacyBold>, or <legacyBold>SQLGetDescField</legacyBold>.)</para>
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
              <para>DM) The value specified for the argument FetchOrientation was invalid. </para>
              <para>(DM) The argument FetchOrientation was SQL_FETCH_BOOKMARK, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
              <para>The value of the SQL_ATTR_CURSOR_TYPE statement attribute was SQL_CURSOR_FORWARD_ONLY, and the value of argument FetchOrientation was not SQL_FETCH_NEXT. </para>
              <para>The value of the SQL_ATTR_CURSOR_SCROLLABLE statement attribute was SQL_NONSCROLLABLE, and the value of argument FetchOrientation was not SQL_FETCH_NEXT.</para>
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
              <para>The value specified with the SQL_ATTR_CURSOR_TYPE statement attribute was SQL_CURSOR_KEYSET_DRIVEN, but the value specified with the SQL_ATTR_KEYSET_SIZE statement attribute was greater than 0 and less than the value specified with the SQL_ATTR_ROW_ARRAY_SIZE statement attribute.</para>
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
              <para>The argument FetchOrientation was SQL_FETCH_BOOKMARK, and the bookmark pointed to by the value in the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute was not valid or was a null pointer.</para>
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
              <para>The driver or data source does not support the conversion specified by the combination of the <legacyItalic>TargetType</legacyItalic> in <legacyBold>SQLBindCol</legacyBold> and the SQL data type of the corresponding column.</para>
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
              <para>The query timeout period expired before the data source returned the requested result set. The timeout period is set through SQLSetStmtAttr, SQL_ATTR_QUERY_TIMEOUT.</para>
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
          <tr>
            <TD>
              <para>IM017</para>
            </TD>
            <TD>
              <para>Polling is disabled in asynchronous notification mode</para>
            </TD>
            <TD>
              <para>Whenever the notification model is used, polling is disabled.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM018</para>
            </TD>
            <TD>
              <para>
                <languageKeyword>SQLCompleteAsync</languageKeyword> has not been called to complete the previous asynchronous operation on this handle.</para>
            </TD>
            <TD>
              <para>If the previous function call on the handle returns SQL_STILL_EXECUTING and if notification mode is enabled, <languageKeyword>SQLCompleteAsync</languageKeyword> must be called on the handle to do post-processing and complete the operation.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> returns a specified rowset from the result set. Rowsets can be specified by absolute or relative position or by bookmark. <legacyBold>SQLFetchScroll</legacyBold> can be called only while a result set exists — that is, after a call that creates a result set and before the cursor over that result set is closed. If any columns are bound, it returns the data in those columns. If the application has specified a pointer to a row status array or a buffer in which to return the number of rows fetched, <legacyBold>SQLFetchScroll</legacyBold> returns this information as well. Calls to <legacyBold>SQLFetchScroll</legacyBold> can be mixed with calls to <legacyBold>SQLFetch</legacyBold> but cannot be mixed with calls to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
      <para>For more information, see <link xlink:href="2aad7d6b-216e-47e7-b3cb-f95ad096f21a">Using Block Cursors</link> and <link xlink:href="c5d795ba-70b0-420f-a944-b1894061a755">Using Scrollable Cursors</link>.</para>
    </content>
  </section>
  <section>
    <title>Positioning the Cursor</title>
    <content>
      <para>When the result set is created, the cursor is positioned before the start of the result set. <legacyBold>SQLFetchScroll</legacyBold> positions the block cursor based on the values of the <legacyItalic>FetchOrientation</legacyItalic> and <legacyItalic>FetchOffset</legacyItalic> arguments as shown in the following table. The exact rules for determining the start of the new rowset are shown in the next section.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>FetchOrientation</para>
            </TD>
            <TD>
              <para>Meaning</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_FETCH_NEXT</para>
            </TD>
            <TD>
              <para>Return the next rowset. This is equivalent to calling <legacyBold>SQLFetch</legacyBold>. </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold> ignores the value of <legacyItalic>FetchOffset</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_PRIOR</para>
            </TD>
            <TD>
              <para>Return the prior rowset. </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold> ignores the value of <legacyItalic>FetchOffset</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_RELATIVE</para>
            </TD>
            <TD>
              <para>Return the rowset <legacyItalic>FetchOffset</legacyItalic> from the start of the current rowset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_ABSOLUTE</para>
            </TD>
            <TD>
              <para>Return the rowset starting at row <legacyItalic>FetchOffset</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_FIRST</para>
            </TD>
            <TD>
              <para>Return the first rowset in the result set. </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold> ignores the value of <legacyItalic>FetchOffset</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_LAST</para>
            </TD>
            <TD>
              <para>Return the last complete rowset in the result set. </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold> ignores the value of <legacyItalic>FetchOffset</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_BOOKMARK</para>
            </TD>
            <TD>
              <para>Return the rowset FetchOffset rows from the bookmark specified by the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Drivers are not required to support all fetch orientations; an application calls <legacyBold>SQLGetInfo</legacyBold> with an information type of SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 (depending on the type of the cursor) to determine which fetch orientations are supported by the driver. The application should look at the SQL_CA1_NEXT, SQL_CA1_RELATIVE, SQL_CA1_ABSOLUTE, and WQL_CA1_BOOKMARK bitmasks in these information types. Furthermore, if the cursor is forward-only and FetchOrientation is not SQL_FETCH_NEXT, <legacyBold>SQLFetchScroll</legacyBold> returns SQLSTATE HY106 (Fetch type out of range).</para>
      <para>The SQL_ATTR_ROW_ARRAY_SIZE statement attribute specifies the number of rows in the rowset. If the rowset being fetched by <legacyBold>SQLFetchScroll</legacyBold> overlaps the end of the result set, <legacyBold>SQLFetchScroll</legacyBold> returns a partial rowset. That is, if S + R – 1 is greater than L, where S is the starting row of the rowset being fetched, R is the rowset size, and L is the last row in the result set, then only the first L – S + 1 rows of the rowset are valid. The remaining rows are empty and have a status of SQL_ROW_NOROW.</para>
      <para>After <legacyBold>SQLFetchScroll</legacyBold> returns, the current row is the first row of the rowset.</para>
    </content>
  </section>
  <section>
    <title>Cursor Positioning Rules</title>
    <content>
      <para>The following sections describe the exact rules for each value of FetchOrientation. These rules use the following notation.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Notation</para>
            </TD>
            <TD>
              <para>Meaning</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The block cursor is positioned before the start of the result set. If the first row of the new rowset is before the start of the result set, <legacyBold>SQLFetchScroll</legacyBold> returns SQL_NO_DATA.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The block cursor is positioned after the end of the result set. If the first row of the new rowset is after the end of the result set, <legacyBold>SQLFetchScroll</legacyBold> returns SQL_NO_DATA.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The number of the first row in the current rowset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The number of the last row in the result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>RowsetSize</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The rowset size.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The value of the <legacyItalic>FetchOffset</legacyItalic> argument.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>BookmarkRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The row corresponding to the bookmark specified by the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_NEXT</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart + RowsetSize</legacyItalic>[1]<legacyItalic> &lt;= LastResultRow</legacyItalic></para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart + RowsetSize</legacyItalic>[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart + RowsetSize</legacyItalic>[1]<legacyItalic>&gt; LastResultRow</legacyItalic></para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   If the rowset size has been changed since the previous call to fetch rows, this is the rowset size that was used with the previous call.</para>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_PRIOR</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart = 1</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>1 &lt; CurrRowsetStart &lt;= RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
                <superscript>[1]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart &gt; RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart – RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>After end AND LastResultRow &lt; RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
                <superscript>[1]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>After end AND LastResultRow &gt;= RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>LastResultRow – RowsetSize + 1</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold>SQLFetchScroll</legacyBold> returns SQLSTATE 01S06 (Attempt to fetch before the result set returned the first rowset) and SQL_SUCCESS_WITH_INFO.</para>
      <para>[2]   If the rowset size has been changed since the previous call to fetch rows, this is the new rowset size.</para>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_RELATIVE</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>(Before start AND FetchOffset &gt; 0) OR (After end AND FetchOffset &lt; 0)</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>--</legacyItalic>
                <superscript>[1]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>BeforeStart AND FetchOffset &lt;= 0</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart = 1 AND FetchOffset &lt; 0</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart &gt; 1 AND CurrRowsetStart + FetchOffset &lt; 1 AND | FetchOffset | &gt; RowsetSize</legacyItalic>
                <superscript>[3]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart &gt; 1 AND CurrRowsetStart + FetchOffset &lt; 1 AND | FetchOffset | &lt;= RowsetSize</legacyItalic>
                <superscript>[3]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>1 &lt;= CurrRowsetStart + FetchOffset &lt;= LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart + FetchOffset</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart + FetchOffset &gt; LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>After end AND FetchOffset &gt;= 0</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold><legacyItalic>SQLFetchScroll</legacyItalic></legacyBold> returns the same rowset as if it was called with FetchOrientation set to SQL_FETCH_ABSOLUTE. For more information, see the "SQL_FETCH_ABSOLUTE" section.</para>
      <para>[2]   <legacyBold>SQLFetchScroll</legacyBold> returns SQLSTATE 01S06 (Attempt to fetch before the result set returned the first rowset) and SQL_SUCCESS_WITH_INFO. </para>
      <para>[3]   If the rowset size has been changed since the previous call to fetch rows, this is the new rowset size.</para>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_ABSOLUTE</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset &lt; 0 AND | FetchOffset | &lt;= LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>LastResultRow + FetchOffset + 1</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset &lt; 0 AND | FetchOffset | &gt; LastResultRow AND | FetchOffset | &gt; RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset &lt; 0 AND | FetchOffset | &gt; LastResultRow AND | FetchOffset | &lt;= RowsetSize</legacyItalic>
                <superscript>[2]</superscript>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
                <superscript>[1]</superscript>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset = 0</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>1 &lt;= FetchOffset &lt;= LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>FetchOffset</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>FetchOffset &gt; LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold>SQLFetchScroll</legacyBold> returns SQLSTATE 01S06 (Attempt to fetch before the result set returned the first rowset) and SQL_SUCCESS_WITH_INFO. </para>
      <para>[2]   If the rowset size has been changed since the previous call to fetch rows, this is the new rowset size.</para>
      <para>An absolute fetch performed against a dynamic cursor cannot provide the required result because row positions in a dynamic cursor are undetermined. Such an operation is equivalent to a fetch first followed by a fetch relative; it is not an atomic operation, as is an absolute fetch on a static cursor.</para>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_FIRST</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Any</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_LAST</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>RowsetSize</legacyItalic> <superscript>[1]</superscript> &lt;= LastResultRow</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>LastResultRow – RowsetSize + 1</legacyItalic>
                <superscript>[1]</superscript> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>RowsetSize</legacyItalic> <superscript>[1]</superscript> &gt; LastResultRow</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>1</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   If the rowset size has been changed since the previous call to fetch rows, this is the new rowset size.</para>
    </content>
  </section>
  <section>
    <title>SQL_FETCH_BOOKMARK</title>
    <content>
      <para>The following rules apply.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Condition</para>
            </TD>
            <TD>
              <para>First row of new rowset</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>BookmarkRow + FetchOffset &lt; 1</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Before start</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>1 &lt;= BookmarkRow + FetchOffset &lt;= LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>BookmarkRow + FetchOffset</legacyItalic>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>BookmarkRow + FetchOffset &gt; LastResultRow</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>After end</legacyItalic>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For information about bookmarks, see <link xlink:href="1d7cccc5-f847-4321-b240-28570854ee5c">Bookmarks_ODBC</link>.</para>
    </content>
  </section>
  <section>
    <title>Effect of Deleted, Added, and Error Rows on Cursor Movement</title>
    <content>
      <para>Static and keyset-driven cursors sometimes detect rows added to the result set and remove rows deleted from the result set. By calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_STATIC_CURSOR_ATTRIBUTES2 and SQL_KEYSET_CURSOR_ATTRIBUTES2 options and looking at the SQL_CA2_SENSITIVITY_ADDITIONS, SQL_CA2_SENSITIVITY_DELETIONS, and SQL_CA2_SENSITIVITY_UPDATES bitmasks, an application determines whether the cursors implemented by a particular driver do this. For drivers that can detect deleted rows and remove them, the following paragraphs describe the effects of this behavior. For drivers that can detect deleted rows but cannot remove them, deletions have no effect on cursor movements, and the following paragraphs do not apply.</para>
      <para>If the cursor detects rows added to the result set or removes rows deleted from the result set, it appears as if it detects these changes only when it fetches data. This includes the case when <legacyBold>SQLFetchScroll</legacyBold> is called with FetchOrientation set to SQL_FETCH_RELATIVE and FetchOffset set to 0 to refetch the same rowset, but does not include the case when SQLSetPos is called with fOption set to SQL_REFRESH. In the latter case, the data in the rowset buffers is refreshed, but not refetched, and deleted rows are not removed from the result set. Thus, when a row is deleted from or inserted into the current rowset, the cursor does not modify the rowset buffers. Instead, it detects the change when it fetches any rowset that previously included the deleted row or now includes the inserted row.</para>
      <para>For example:</para>
      <code>// Fetch the next rowset.
SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);
// Delete third row of the rowset. Does not modify the rowset buffers.
SQLSetPos(hstmt, 3, SQL_DELETE, SQL_LOCK_NO_CHANGE);
// The third row has a status of SQL_ROW_DELETED after this call.
SQLSetPos(hstmt, 3, SQL_REFRESH, SQL_LOCK_NO_CHANGE);
// Refetch the same rowset. The third row is removed, replaced by what
// was previously the fourth row.
SQLFetchScroll(hstmt, SQL_FETCH_RELATIVE, 0);</code>
      <para>When <legacyBold>SQLFetchScroll</legacyBold> returns a new rowset that has a position relative to the current rowset — that is, FetchOrientation is SQL_FETCH_NEXT, SQL_FETCH_PRIOR, or SQL_FETCH_RELATIVE — it does not include changes to the current rowset when calculating the starting position of the new rowset. However, it does include changes outside the current rowset if it is capable of detecting them. Furthermore, when <legacyBold>SQLFetchScroll</legacyBold> returns a new rowset that has a position independent of the current rowset — that is, FetchOrientation is SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE, or SQL_FETCH_BOOKMARK — it includes all changes it is capable of detecting, even if they are in the current rowset.</para>
      <para>When determining whether newly added rows are inside or outside the current rowset, a partial rowset is considered to end at the last valid row; that is, the last row for which the row status is not SQL_ROW_NOROW. For example, suppose the cursor is capable of detecting newly added rows, the current rowset is a partial rowset, the application adds new rows, and the cursor adds these rows to the end of the result set. If the application calls <legacyBold>SQLFetchScroll</legacyBold> with FetchOrientation set to SQL_FETCH_NEXT, <legacyBold>SQLFetchScroll</legacyBold> returns the rowset starting with the first newly added row.</para>
      <para>For example, suppose the current rowset comprises rows 21 to 30, the rowset size is 10, the cursor removes rows deleted from the result set, and the cursor detects rows added to the result set. The following table shows the rows <legacyBold>SQLFetchScroll</legacyBold> returns in various situations.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Change</para>
            </TD>
            <TD>
              <para>Fetch type</para>
            </TD>
            <TD>
              <para>FetchOffset</para>
            </TD>
            <TD>
              <para>New rowset<subscript>[1]</subscript></para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Delete row 21</para>
            </TD>
            <TD>
              <para>NEXT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>31 to 40</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 31</para>
            </TD>
            <TD>
              <para>NEXT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>32 to 41</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 21 and 22</para>
            </TD>
            <TD>
              <para>NEXT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>31 to 40</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 30 and 31</para>
            </TD>
            <TD>
              <para>NEXT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>Inserted row, 31 to 39</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 21</para>
            </TD>
            <TD>
              <para>PRIOR</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>11 to 20</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 20</para>
            </TD>
            <TD>
              <para>PRIOR</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>10 to 19</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 21 and 22</para>
            </TD>
            <TD>
              <para>PRIOR</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>11 to 20</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 20 and 21</para>
            </TD>
            <TD>
              <para>PRIOR</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>12 to 20, inserted row</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 21</para>
            </TD>
            <TD>
              <para>RELATIVE</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>22 to 31<superscript>[2]</superscript></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 21</para>
            </TD>
            <TD>
              <para>RELATIVE</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>22 to 31</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 21 and 22</para>
            </TD>
            <TD>
              <para>RELATIVE</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>21, inserted row, 22 to 29</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 21 and 22</para>
            </TD>
            <TD>
              <para>RELATIVE</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>22 to 31</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 21</para>
            </TD>
            <TD>
              <para>ABSOLUTE</para>
            </TD>
            <TD>
              <para>21</para>
            </TD>
            <TD>
              <para>22 to 31<superscript>[2]</superscript></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delete row 22</para>
            </TD>
            <TD>
              <para>ABSOLUTE</para>
            </TD>
            <TD>
              <para>21</para>
            </TD>
            <TD>
              <para>21, 23 to 31</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Insert row between rows 21 and 22</para>
            </TD>
            <TD>
              <para>ABSOLUTE</para>
            </TD>
            <TD>
              <para>22</para>
            </TD>
            <TD>
              <para>Inserted row, 22 to 29</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This column uses the row numbers before any rows were inserted or deleted.</para>
      <para>[2]   In this case, the cursor attempts to return rows starting with row 21. Because row 21 has been deleted, the first row it returns is row 22.</para>
      <para>Error rows (that is, rows with a status of SQL_ROW_ERROR) do not affect cursor movement. For example, if the current rowset starts with row 11 and the status of row 11 is SQL_ROW_ERROR, calling <legacyBold>SQLFetchScroll</legacyBold> with FetchOrientation set to SQL_FETCH_RELATIVE and FetchOffset set to 5 returns the rowset starting with row 16, just as it would if the status for row 11 was SQL_SUCCESS.</para>
    </content>
  </section>
  <section>
    <title>Returning Data in Bound Columns</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> returns data in bound columns in the same way as <legacyBold>SQLFetch</legacyBold>. For more information, see "Returning Data in Bound Columns" in <link xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</link>.</para>
      <para>If no columns are bound, <legacyBold>SQLFetchScroll</legacyBold> does not return data but does move the block cursor to the specified position. Whether data can be retrieved from unbound columns of a block cursor with <legacyBold>SQLGetData</legacyBold> depends on the driver. This capability is supported if a call to <legacyBold>SQLGetInfo</legacyBold> returns the SQL_GD_BLOCK bit for the SQL_GETDATA_EXTENSIONS information type.</para>
    </content>
  </section>
  <section>
    <title>Buffer Addresses</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> uses the same formula to determine the address of data and length/indicator buffers as <legacyBold>SQLFetch</legacyBold>. For more information, see "Buffer Addresses" in <link xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</link>.</para>
    </content>
  </section>
  <section>
    <title>Row Status Array</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> sets values in the row status array in the same manner as SQLFetch. For more information, see "Row Status Array" in <link xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</link>.</para>
    </content>
  </section>
  <section>
    <title>Rows Fetched Buffer</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> returns the number of rows fetched in the rows fetched buffer in the same manner as <legacyBold>SQLFetch</legacyBold>. For more information, see "Rows Fetched Buffer" in <link xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</link>.</para>
    </content>
  </section>
  <section>
    <title>Error Handling</title>
    <content>
      <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 3.x driver, the Driver Manager calls <legacyBold>SQLFetchScroll</legacyBold> in the driver. When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.x driver, the Driver Manager calls SQLExtendedFetch in the driver. Because <legacyBold>SQLFetchScroll</legacyBold> and SQLExtendedFetch handle errors in a slightly different manner, the application sees slightly different error behavior when it calls <legacyBold>SQLFetchScroll</legacyBold> in ODBC 2.x and ODBC 3.x drivers.</para>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> returns errors and warnings in the same manner as <legacyBold>SQLFetch</legacyBold>; for more information, see "Error Handling" in <legacyBold>SQLFetch</legacyBold>. <legacyBold>SQLExtendedFetch</legacyBold> returns errors in the same manner as <legacyBold>SQLFetch</legacyBold>, with the following exceptions: </para>
      <para>When a warning occurs that applies to a particular row in the rowset, SQLExtendedFetch sets the corresponding entry in the row status array to SQL_ROW_SUCCESS, not SQL_ROW_SUCCESS_WITH_INFO. </para>
      <para>If errors occur in every row in the rowset, SQLExtendedFetch returns SQL_SUCCESS_WITH_INFO, not SQL_ERROR. </para>
      <para>In each group of status records that applies to an individual row, the first status record returned by SQLExtendedFetch must contain SQLSTATE 01S01 (Error in row); <legacyBold>SQLFetchScroll</legacyBold> does not return this SQLSTATE. If SQLExtendedFetch is unable to return additional SQLSTATEs, it still must return this SQLSTATE. </para>
    </content>
  </section>
  <section>
    <title>SQLFetchScroll and Optimistic Concurrency</title>
    <content>
      <para>If a cursor uses optimistic concurrency — that is, the SQL_ATTR_CONCURRENCY statement attribute has a value of SQL_CONCUR_VALUES or SQL_CONCUR_ROWVER — <legacyBold>SQLFetchScroll</legacyBold> updates the optimistic concurrency values used by the data source to detect whether a row has changed. This happens whenever <legacyBold>SQLFetchScroll</legacyBold> fetches a new rowset, including when it refetches the current rowset. (It is called with FetchOrientation set to SQL_FETCH_RELATIVE and FetchOffset set to 0.)</para>
    </content>
  </section>
  <section>
    <title>SQLFetchScroll and ODBC 2.x Drivers</title>
    <content>
      <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.x driver, the Driver Manager maps this call to <legacyBold>SQLExtendedFetch</legacyBold>. It passes the following values for the arguments of <legacyBold>SQLExtendedFetch</legacyBold>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLExtendedFetch argument</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>StatementHandle</para>
            </TD>
            <TD>
              <para>StatementHandle in <legacyBold>SQLFetchScroll</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FetchOrientation</para>
            </TD>
            <TD>
              <para>FetchOrientation in <legacyBold>SQLFetchScroll</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FetchOffset</para>
            </TD>
            <TD>
              <para>If FetchOrientation is not SQL_FETCH_BOOKMARK, the value of the FetchOffset argument in <legacyBold>SQLFetchScroll</legacyBold> is used. </para>
              <para>If FetchOrientation is SQL_FETCH_BOOKMARK, the value stored at the address specified by the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute is used.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RowCountPtr</para>
            </TD>
            <TD>
              <para>The address specified by the SQL_ATTR_ROWS_FETCHED_PTR statement attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RowStatusArray</para>
            </TD>
            <TD>
              <para>The address specified by the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For more information, see <link xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</link> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    </content>
  </section>
  <section>
    <title>Descriptors and SQLFetchScroll</title>
    <content>
      <para>
        <legacyBold>SQLFetchScroll</legacyBold> interacts with descriptors in the same manner as <legacyBold>SQLFetch</legacyBold>. For more information, see the "Descriptors and SQLFetchScroll" section in <link xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</link>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <link xlink:href="86d37637-3a25-455d-9c82-a0d7bff8d70d">Column-Wise Binding</link>, <link xlink:href="4f622cf4-0603-47a1-a48b-944c4ef46364">Row-Wise Binding</link>, <link xlink:href="0eafba50-02c7-46ca-a439-ef3307b935dc">Positioned Update and Delete Statements</link>, and <link xlink:href="d83a8c2a-5aa8-4f19-947c-79a817167ee1">Updating Rows in the Rowset with SQLSetPos</link>.</para>
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
                <link xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Performing bulk insert, update, or delete operations</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a column in a result set</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a single row or a block of data in a forward-only direction</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Closing the cursor on the statement</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the number of result set columns</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Positioning the cursor, refreshing data in the rowset, or updating or deleting data in the result set</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</link>
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