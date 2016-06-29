---
title: SQLFetch Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLFetch
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
translation.priority.ht: 
  - en-gb
---
# SQLFetch Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ISO 92</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> fetches the next rowset of data from the result set and returns data for all bound columns.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLFetch</legacyBold>(
     SQLHSTMT     <parameterReference>StatementHandle</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>StatementHandle</parameterReference>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle.</para>
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
      <para>When <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <link xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec Function</link> with a <parameterReference>HandleType</parameterReference> of SQL_HANDLE_STMT and a <parameterReference>Handle</parameterReference> of <parameterReference>StatementHandle</parameterReference>. The following table lists the SQLSTATE values typically returned by <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. If an error occurs on a single column, <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink> can be called with a <parameterReference>DiagIdentifier</parameterReference> of SQL_DIAG_COLUMN_NUMBER to determine the column the error occurred on; and <unmanagedCodeEntityReference>SQLGetDiagField</unmanagedCodeEntityReference> can be called with a <parameterReference>DiagIdentifier</parameterReference> of SQL_DIAG_ROW_NUMBER to determine the row that contains that column. </para>
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
              <para>01S07</para>
            </TD>
            <TD>
              <para>Fractional truncation</para>
            </TD>
            <TD>
              <para>The data returned for a column was truncated. For numeric data types, the fractional part of the number was truncated. For time, timestamp, and interval data types that contain a time component, the fractional part of the time was truncated. </para>
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
              <para>Returning the numeric value as numeric or string for one or more bound columns would have caused the whole (as opposed to fractional) part of the number to be truncated.</para>
              <para>For more information, see <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink> in Appendix D: Data Types.</para>
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
              <para>The driver was unable to allocate memory that is required to support execution or completion of the function.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>Or, the <unmanagedCodeEntityReference> SQLFetch</unmanagedCodeEntityReference> function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
        <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns the next rowset in the result set. It can be called only while a result set exists: that is, after a call that creates a result set and before the cursor over that result set is closed. If any columns are bound, it returns the data in those columns. If the application has specified a pointer to a row status array or a buffer in which to return the number of rows fetched, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> also returns this information. Calls to <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> can be mixed with calls to <legacyBold>SQLFetchScroll</legacyBold> but cannot be mixed with calls to <legacyBold>SQLExtendedFetch</legacyBold>. For more information, see <legacyLink xlink:href="16d4a380-0d83-456b-aeee-f10738944e86">Fetching a Row of Data</legacyLink>.</para>
      <para>If an ODBC 3<legacyItalic>.x</legacyItalic> application works with an ODBC 2<legacyItalic>.x</legacyItalic> driver, the Driver Manager maps <legacyBold>SQLFetch</legacyBold> calls to <legacyBold>SQLExtendedFetch</legacyBold> for an ODBC 2<legacyItalic>.x</legacyItalic> driver that supports <legacyBold>SQLExtendedFetch</legacyBold>. If the ODBC 2<legacyItalic>.x</legacyItalic> driver does not support <legacyBold>SQLExtendedFetch</legacyBold>, the Driver Manager maps <legacyBold>SQLFetch</legacyBold> calls to <legacyBold>SQLFetch</legacyBold> in the ODBC 2<legacyItalic>.x</legacyItalic> driver, which can fetch only a single row.</para>
      <para>For more information, see <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    </content>
  </section>
  <section>
    <title>Positioning the Cursor</title>
    <content>
      <para>When the result set is created, the cursor is positioned before the start of the result set. <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> fetches the next rowset. It is equivalent to calling <legacyBold>SQLFetchScroll</legacyBold> with <legacyItalic>FetchOrientation</legacyItalic> set to SQL_FETCH_NEXT. For more information about cursors, see <legacyLink xlink:href="0b114352-3c63-4d33-9220-182ede90e4aa">Cursors</legacyLink> and <legacyLink xlink:href="1a92b5d8-7c6e-4ce5-8c99-600a387026aa">Block Cursors</legacyLink>.</para>
      <para>The SQL_ATTR_ROW_ARRAY_SIZE statement attribute specifies the number of rows in the rowset. If the rowset being fetched by <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> overlaps the end of the result set, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns a partial rowset. That is, if S + R – 1 is greater than L, where S is the starting row of the rowset being fetched, R is the rowset size, and L is the last row in the result set, then only the first L – S + 1 rows of the rowset are valid. The remaining rows are empty and have a status of SQL_ROW_NOROW.</para>
      <para>After <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns, the current row is the first row of the rowset.</para>
      <para>The rules listed in the following table describe cursor positioning after a call to <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference>, based on the conditions listed in the second table in this section.</para>
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
              <para>Before start</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart</legacyItalic> &lt;= <legacyItalic>LastResultRow – RowsetSize</legacyItalic>[1]</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart</legacyItalic> + <legacyItalic>RowsetSize</legacyItalic>[2]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart</legacyItalic> &gt; <legacyItalic>LastResultRow – RowsetSize</legacyItalic>[1]</para>
            </TD>
            <TD>
              <para>After end</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>After end</para>
            </TD>
            <TD>
              <para>After end</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   If the rowset size is changed between fetches, this is the rowset size that was used with the previous fetch.</para>
      <para>[2]   If the rowset size is changed between fetches, this is the rowset size that was used with the new fetch.</para>
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
              <para>Before start</para>
            </TD>
            <TD>
              <para>The block cursor is positioned before the start of the result set. If the first row of the new rowset is before the start of the result set, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQL_NO_DATA.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>After end</para>
            </TD>
            <TD>
              <para>The block cursor is positioned after the end of the result set. If the first row of the new rowset is after the end of the result set, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQL_NO_DATA.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>CurrRowsetStart</legacyItalic> </para>
            </TD>
            <TD>
              <para>The number of the first row in the current rowset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>LastResultRow</legacyItalic> </para>
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
        </tbody>
      </table>
      <para>For example, suppose a result set has 100 rows and the rowset size is 5. The following table shows the rowset and return code returned by <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> for different starting positions.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Current rowset</para>
            </TD>
            <TD>
              <para>Return code</para>
            </TD>
            <TD>
              <para>New rowset</para>
            </TD>
            <TD>
              <para># of rows fetched</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Before start</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>1 to 5</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>1 to 5</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>6 to 10</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>52 to 56</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>57 to 61</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>91 to 95</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>96 to 100</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>93 to 97</para>
            </TD>
            <TD>
              <para>SQL_SUCCESS</para>
            </TD>
            <TD>
              <para>98 to 100. Rows 4 and 5 of the row status array are set to SQL_ROW_NOROW.</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>96 to 100</para>
            </TD>
            <TD>
              <para>SQL_NO_DATA</para>
            </TD>
            <TD>
              <para>None.</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>99 to 100</para>
            </TD>
            <TD>
              <para>SQL_NO_DATA</para>
            </TD>
            <TD>
              <para>None.</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>After end</para>
            </TD>
            <TD>
              <para>SQL_NO_DATA</para>
            </TD>
            <TD>
              <para>None.</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Returning Data in Bound Columns</title>
    <content>
      <para>As <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns each row, it puts the data for each bound column in the buffer bound to that column. If no columns are bound, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns no data but does move the block cursor forward. The data can still be retrieved by using <legacyBold>SQLGetData</legacyBold>. If the cursor is a multirow cursor (that is, the SQL_ATTR_ROW_ARRAY_SIZE is greater than 1), <legacyBold>SQLGetData</legacyBold> can be called only if SQL_GD_BLOCK is returned when <legacyBold>SQLGetInfo</legacyBold> is called with an <legacyItalic>InfoType</legacyItalic> of SQL_GETDATA_EXTENSIONS. (For more information, see <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>.)</para>
      <para>For each bound column in a row, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> does the following:  </para>
      <list class="ordered">
        <listItem>
          <para>Sets the length/indicator buffer to SQL_NULL_DATA and proceeds to the next column if the data is NULL. If the data is NULL and no length/indicator buffer was bound, <legacyBold>SQLFetch</legacyBold> returns SQLSTATE 22002 (Indicator variable required but not supplied) for the row and proceeds to the next row. For information about how to determine the address of the length/indicator buffer, see "Buffer Addresses" in <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>. </para>
          <para>If the data for the column is not NULL, <legacyBold>SQLFetch</legacyBold> proceeds to step 2. </para>
        </listItem>
        <listItem>
          <para>If the SQL_ATTR_MAX_LENGTH statement attribute is set to a nonzero value and the column contains character or binary data, the data is truncated to SQL_ATTR_MAX_LENGTH bytes. </para>
          <alert class="note">
            <para>The SQL_ATTR_MAX_LENGTH statement attribute is intended to reduce network traffic. It is generally implemented by the data source, which truncates the data before returning it over the network. Drivers and data sources are not required to support it. Therefore, to guarantee that data is truncated to a particular size, an application should allocate a buffer of that size and specify the size in the <legacyItalic>cbValueMax</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Converts the data to the type specified by <legacyItalic>TargetType</legacyItalic> in <legacyBold>SQLBindCol</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>If the data was converted to a variable-length data type, such as character or binary, <legacyBold>SQLFetch</legacyBold> checks whether the length of the data exceeds the length of the data buffer. If the length of character data (including the null-termination character) exceeds the length of the data buffer, <legacyBold>SQLFetch</legacyBold> truncates the data to the length of the data buffer less the length of a null-termination character. It then null-terminates the data. If the length of binary data exceeds the length of the data buffer, <legacyBold>SQLFetch</legacyBold> truncates it to the length of the data buffer. The length of the data buffer is specified with <legacyItalic>BufferLength</legacyItalic> in <legacyBold>SQLBindCol</legacyBold>. </para>
          <para>
            <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> never truncates data converted to fixed-length data types; it always assumes that the length of the data buffer is the size of the data type. </para>
        </listItem>
        <listItem>
          <para>Puts the converted (and possibly truncated) data in the data buffer. For information about how to determine the address of the data buffer, see "Buffer Addresses" in <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>Puts the length of the data in the length/indicator buffer. If the indicator pointer and the length pointer were both set to the same buffer (as a call to <legacyBold>SQLBindCol</legacyBold> does), the length is written in the buffer for valid data and SQL_NULL_DATA is written in the buffer for NULL data. If no length/indicator buffer was bound, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> does not return the length. </para>
          <list class="bullet">
            <listItem>
              <para>For character or binary data, this is the length of the data after conversion and before truncation because of the data buffer being too small. If the driver cannot determine the length of the data after conversion, as is sometimes the case with long data, it sets the length to SQL_NO_TOTAL. If data was truncated because of the SQL_ATTR_MAX_LENGTH statement attribute, the value of this attribute is put in the length/indicator buffer instead of the actual length . This is because this attribute is designed to truncate data on the server before conversion, so that the driver has no way of figuring out what the actual length is.</para>
            </listItem>
            <listItem>
              <para>For all other data types, this is the length of the data after conversion; that is, it is the size of the type to which the data was converted.</para>
            </listItem>
          </list>
          <para>For information about how to determine the address of the length/indicator buffer, see "Buffer Addresses" in <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>. </para>
        </listItem>
        <listItem>
          <para>If the data is truncated during conversion without a loss of significant digits (for example, the real number 1.234 is truncated to the integer 1 when converted), <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQLSTATE 01S07 (Fractional truncation) and SQL_SUCCESS_WITH_INFO. If the data is truncated because the length of the data buffer is too small (for example, the string "abcdef" is put in a 4-byte buffer), <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQLSTATE 01004 (Data truncated) and SQL_SUCCESS_WITH_INFO. If data is truncated because of the SQL_ATTR_MAX_LENGTH statement attribute, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQL_SUCCESS and does not return SQLSTATE 01S07 (Fractional truncation) or SQLSTATE 01004 (Data truncated). If data is truncated during conversion with a loss of significant digits (for example, if an SQL_INTEGER value greater than 100,000 were converted to an SQL_C_TINYINT), <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQLSTATE 22003 (Numeric value out of range) and SQL_ERROR (if the rowset size is 1) or SQL_SUCCESS_WITH_INFO (if the rowset size is greater than 1).</para>
        </listItem>
      </list>
      <para>The contents of the bound data buffer and the length/indicator buffer are undefined if <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference> does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO.</para>
    </content>
  </section>
  <section>
    <title>Row Status Array</title>
    <content>
      <para>The row status array is used to return the status of each row in the rowset. The address of this array is specified with the SQL_ATTR_ROW_STATUS_PTR statement attribute. The array is allocated by the application and must have as many elements as are specified by the SQL_ATTR_ROW_ARRAY_SIZE statement attribute. Its values are set by <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, and <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> (except when they have been called after the cursor has been positioned by <legacyBold>SQLExtendedFetch</legacyBold>). If the value of the SQL_ATTR_ROW_STATUS_PTR statement attribute is a null pointer, these functions do not return the row status.</para>
      <para>The contents of the row status array buffer are undefined if <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference> does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO.</para>
      <para>The following values are returned in the row status array.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Row status array value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ROW_SUCCESS</para>
            </TD>
            <TD>
              <para>The row was successfully fetched and has not changed since it was last fetched from this result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_SUCCESS_WITH_INFO</para>
            </TD>
            <TD>
              <para>The row was successfully fetched and has not changed since it was last fetched from this result set. However, a warning was returned about the row.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_ERROR</para>
            </TD>
            <TD>
              <para>An error occurred while fetching the row.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_UPDATED[1],[2], and [3]</para>
            </TD>
            <TD>
              <para>The row was successfully fetched and has changed since it was last fetched from this result set. If the row is fetched again from this result set or is refreshed by <legacyBold>SQLSetPos</legacyBold>, the status is changed to the row's new status.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_DELETED[3]</para>
            </TD>
            <TD>
              <para>The row has been deleted since it was last fetched from this result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_ADDED[4]</para>
            </TD>
            <TD>
              <para>The row was inserted by <legacyBold>SQLBulkOperations</legacyBold>. If the row is fetched again from this result set or is refreshed by <legacyBold>SQLSetPos</legacyBold>, its status is SQL_ROW_SUCCESS.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_NOROW</para>
            </TD>
            <TD>
              <para>The rowset overlapped the end of the result set, and no row was returned that corresponded to this element of the row status array.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   For keyset, mixed, and dynamic cursors, if a key value is updated, the row of data is considered to have been deleted and a new row added.</para>
      <para>[2]   Some drivers cannot detect updates to data and therefore cannot return this value. To determine whether a driver can detect updates to refetched rows, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_ROW_UPDATES option.</para>
      <para>[3]   <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> can return this value only when it is intermixed with calls to <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference>. This is because <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> moves forward through the result set and when it is used exclusively, does not refetch any rows. Because no rows are refetched, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> does not detect changes that were made to previously fetched rows. However, if <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference> positions the cursor before any previously fetched rows and <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> is used to fetch those rows, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> can detect any changes to those rows.</para>
      <para>[4]   Returned by SQLBulkOperations only. Not set by <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference>.</para>
    </content>
    <sections>
      <section>
        <title>Rows Fetched Buffer</title>
        <content>
          <para>The rows fetched buffer is used to return the number of rows fetched, including those rows for which no data was returned because an error occurred while they were being fetched. In other words, it is the number of rows for which the value in the row status array is not SQL_ROW_NOROW. The address of this buffer is specified with the SQL_ATTR_ROWS_FETCHED_PTR statement attribute. The buffer is allocated by the application. It is set by <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference>. If the value of the SQL_ATTR_ROWS_FETCHED_PTR statement attribute is a null pointer, these functions do not return the number of rows fetched. To determine the number of the current row in the result set, an application can call <legacyBold>SQLGetStmtAttr</legacyBold> with the SQL_ATTR_ROW_NUMBER attribute.</para>
          <para>The contents of the rows fetched buffer are undefined if <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>SQLFetchScroll</unmanagedCodeEntityReference> does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, except when SQL_NO_DATA is returned, in which case the value in the rows fetched buffer is set to 0.</para>
        </content>
      </section>
      <section>
        <title>Error Handling</title>
        <content>
          <para>Errors and warnings can apply to individual rows or to the whole function. For more information about diagnostic records, see <legacyLink xlink:href="450abd88-90a1-4fbc-b417-8efbdd8e1dea">Diagnostics</legacyLink> and <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>.</para>
        </content>
        <sections>
          <section>
            <title>Errors and Warnings on the Entire Function</title>
            <content>
              <para>If an error applies to the entire function, such as SQLSTATE HYT00 (Timeout expired) or SQLSTATE 24000 (Invalid cursor state), <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQL_ERROR and the applicable SQLSTATE. The contents of the rowset buffers are undefined and the cursor position is unchanged.</para>
              <para>If a warning applies to the entire function, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> returns SQL_SUCCESS_WITH_INFO and the applicable SQLSTATE. The status records for warnings that apply to the entire function are returned before the status records that apply to individual rows.</para>
            </content>
          </section>
          <section>
            <title>Errors and Warnings in Individual Rows</title>
            <content>
              <para>If an error (such as SQLSTATE 22012 (Division by zero)) or a warning (such as SQLSTATE 01004 (Data truncated)) applies to a single row, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference><legacyBold> </legacyBold>does the following:  </para>
              <list class="bullet">
                <listItem>
                  <para>Sets the corresponding element of the row status array to SQL_ROW_ERROR for errors or SQL_ROW_SUCCESS_WITH_INFO for warnings.</para>
                </listItem>
                <listItem>
                  <para>Adds zero or more status records that contain SQLSTATEs for the error or warning.</para>
                </listItem>
                <listItem>
                  <para>Sets the row and column number fields in the status records. If <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> cannot determine a row or column number, it sets that number to SQL_ROW_NUMBER_UNKNOWN or SQL_COLUMN_NUMBER_UNKNOWN, respectively. If the status record does not apply to a particular column, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> sets the column number to SQL_NO_COLUMN_NUMBER.</para>
                </listItem>
              </list>
              <para>
                <legacyBold>SQLFetch</legacyBold> continues fetching rows until it has fetched all the rows in the rowset. It returns SQL_SUCCESS_WITH_INFO unless an error occurs in every row of the rowset (not including rows with status SQL_ROW_NOROW), in which case it returns SQL_ERROR. In particular, if the rowset size is 1 and an error occurs in that row, <legacyBold>SQLFetch</legacyBold> returns SQL_ERROR.</para>
              <para>
                <legacyBold>SQLFetch</legacyBold> returns the status records in row number order. That is, it returns all status records for unknown rows (if any); next it returns all status records for the first row (if any), and then it returns all status records for the second row (if any), and so on. The status records for each row are ordered according to the normal rules for ordering status records; for more information, see "Sequence of Status Records" in <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Descriptors and SQLFetch</title>
        <content>
          <para>The following sections describe how <legacyBold>SQLFetch</legacyBold> interacts with descriptors.</para>
        </content>
        <sections>
          <section>
            <title>Argument Mappings</title>
            <content>
              <para>The driver does not set any descriptor fields based on the arguments of <legacyBold>SQLFetch</legacyBold>.</para>
            </content>
          </section>
          <section>
            <title>Other Descriptor Fields</title>
            <content>
              <para>The following descriptor fields are used by <legacyBold>SQLFetch</legacyBold>.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Descriptor field</para>
                    </TD>
                    <TD>
                      <para>Desc.</para>
                    </TD>
                    <TD>
                      <para>Field in</para>
                    </TD>
                    <TD>
                      <para>Set through</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>SQL_DESC_ARRAY_SIZE</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>SQL_ATTR_ROW_ARRAY_SIZE statement attribute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_ARRAY_STATUS_PTR</para>
                    </TD>
                    <TD>
                      <para>IRD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>SQL_ATTR_ROW_STATUS_PTR statement attribute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_BIND_OFFSET_PTR</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_BIND_TYPE</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>SQL_ATTR_ROW_BIND_TYPE statement attribute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_COUNT</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>ColumnNumber</legacyItalic> argument of <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_DATA_PTR</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>records</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>TargetValuePtr</legacyItalic> argument of <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_INDICATOR_PTR</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>records</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_OCTET_LENGTH</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>records</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>BufferLength</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_OCTET_LENGTH_PTR</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>records</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
                    </TD>
                    <TD>
                      <para>IRD</para>
                    </TD>
                    <TD>
                      <para>header</para>
                    </TD>
                    <TD>
                      <para>SQL_ATTR_ROWS_FETCHED_PTR statement attribute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SQL_DESC_TYPE</para>
                    </TD>
                    <TD>
                      <para>ARD</para>
                    </TD>
                    <TD>
                      <para>records</para>
                    </TD>
                    <TD>
                      <para>
                        <legacyItalic>TargetType</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold></para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>All descriptor fields can also be set through <legacyBold>SQLSetDescField</legacyBold>.</para>
            </content>
          </section>
          <section>
            <title>Separate Length and Indicator Buffers</title>
            <content>
              <para>Applications can bind a single buffer or two separate buffers that can be used to hold length and indicator values. When an application calls <legacyBold>SQLBindCol</legacyBold>, the driver sets the SQL_DESC_OCTET_LENGTH_PTR and SQL_DESC_INDICATOR_PTR fields of the ARD to the same address, which is passed in the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument. When an application calls <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>, it can set these two fields to different addresses.</para>
              <para>
                <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> determines whether the application has specified separate length and indicator buffers. In this case, when the data is not NULL, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> sets the indicator buffer to 0 and returns the length in the length buffer. When the data is NULL, <unmanagedCodeEntityReference>SQLFetch</unmanagedCodeEntityReference> sets the indicator buffer to SQL_NULL_DATA and does not modify the length buffer.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Code Example</title>
        <content>
          <para>See <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>, <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns</legacyLink>, <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>, and <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures</legacyLink>.</para>
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
                  <para>Fetching a block of data or scrolling through a result set</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>
                  </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Closing the cursor on the statement</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink>
                  </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Fetching part or all of a column of data</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData Function</legacyLink>
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
                  <para>Preparing a statement for execution</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare Function</legacyLink>
                  </para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>