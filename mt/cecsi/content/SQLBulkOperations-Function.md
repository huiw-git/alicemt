---
title: SQLBulkOperations Function
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
  - SQLBulkOperations
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBulkOperations Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLBulkOperations</legacyBold> performs bulk insertions and bulk bookmark operations, including update, delete, and fetch by bookmark.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLBulkOperations</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLUSMALLINT   <parameterReference>Operation</parameterReference>);</legacySyntax>
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
          <legacyItalic>Operation</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Operation to perform:</para>
          <para>SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK   </para>
          <para>For more information, see "Comments." </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLBulkOperations</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLBulkOperations</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. </para>
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
              <para>String data right truncation</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK, and string or binary data returned for a column or columns with a data type of SQL_C_CHAR or SQL_C_BINARY resulted in the truncation of nonblank character or non-NULL binary data.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, and an error occurred in one or more rows while performing the operation but at least one row was successfully added. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>(This error is raised only when an application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver.)</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK, the data type of the application buffer was not SQL_C_CHAR or SQL_C_BINARY, and the data returned to application buffers for one or more columns was truncated. (For numeric C data types, the fractional part of the number was truncated. For time, timestamp, and interval C data types that contain a time component, the fractional portion of the time was truncated.) </para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK, and the data value of a column in the result set could not be converted to the data type specified by the <legacyItalic>TargetType</legacyItalic> argument in the call to <legacyBold>SQLBindCol</legacyBold>.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE_BY_BOOKMARK or SQL_ADD, and the data value in the application buffers could not be converted to the data type of a column in the result set.</para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_ADD, and a column was bound with a column number greater than the number of columns in the result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>21S02</para>
            </TD>
            <TD>
              <para>Degree of derived table does not match column list</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_UPDATE_BY_BOOKMARK; and no columns were updatable because all columns were either unbound or read-only, or the value in the bound length/indicator buffer was SQL_COLUMN_IGNORE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22001</para>
            </TD>
            <TD>
              <para>String data right truncation</para>
            </TD>
            <TD>
              <para>The assignment of a character or binary value to a column in the result set resulted in the truncation of nonblank (for characters) or non-null (for binary) characters or bytes.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK, and the assignment of a numeric value to a column in the result set caused the whole (as opposed to fractional) part of the number to be truncated.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_FETCH_BY_BOOKMARK, and returning the numeric value for one or more bound columns would have caused a loss of significant digits.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK, and the assignment of a date or timestamp value to a column in the result set caused the year, month, or day field to be out of range.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_FETCH_BY_BOOKMARK, and returning the date or timestamp value for one or more bound columns would have caused the year, month, or day field to be out of range.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22008</para>
            </TD>
            <TD>
              <para>Date/time field overflow</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK, and the performance of datetime arithmetic on data being sent to a column in the result set resulted in a datetime field (the year, month, day, hour, minute, or second field) of the result falling outside the permissible range of values for the field or being invalid based on the Gregorian calendar's natural rules for datetimes.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK, and the performance of datetime arithmetic on data being retrieved from the result set resulted in a datetime field (the year, month, day, hour, minute, or second field) of the result falling outside the permissible range of values for the field or being invalid based on the Gregorian calendar's natural rules for datetimes.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK, and the assignment of an exact numeric or interval C type to an interval SQL data type caused a loss of significant digits.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK; when assigning to an interval SQL type, there was no representation of the value of the C type in the interval SQL type.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK, and assigning from an exact numeric or interval SQL type to an interval C type caused a loss of significant digits in the leading field.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK; when assigning to an interval C type, there was no representation of the value of the SQL type in the interval C type.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_FETCH_BY_BOOKMARK; the C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_ADD or SQL_UPDATE_BY_BOOKMARK; the SQL type was an exact or approximate numeric, a datetime, or an interval data type; the C type was SQL_C_CHAR; and the value in the column was not a valid literal of the bound SQL type. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>23000</para>
            </TD>
            <TD>
              <para>Integrity constraint violation</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, SQL_DELETE_BY_BOOKMARK, or SQL_UPDATE_BY_BOOKMARK, and an integrity constraint was violated.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, and a column that was not bound is defined as NOT NULL and has no default.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, the length specified in the bound <legacyItalic>StrLen_or_IndPtr</legacyItalic> buffer was SQL_COLUMN_IGNORE, and the column did not have a default value.</para>
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
              <para>40001</para>
            </TD>
            <TD>
              <para>Serialization failure</para>
            </TD>
            <TD>
              <para>The transaction was rolled back because of a resource deadlock with another transaction.</para>
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
              <para>42000</para>
            </TD>
            <TD>
              <para>Syntax error or access violation</para>
            </TD>
            <TD>
              <para>The driver was unable to lock the row as needed to perform the operation requested in the <legacyItalic>Operation</legacyItalic> argument.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>44000</para>
            </TD>
            <TD>
              <para>WITH CHECK OPTION violation</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK, and the insert or update was performed on a viewed table (or a table derived from the viewed table) that was created by specifying <legacyBold>WITH CHECK OPTION</legacyBold>, in such a way that one or more rows affected by the insert or update will no longer be present in the viewed table.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY001</para>
            </TD>
            <TD>
              <para>Memory allocation error</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLBulkOperations</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) The specified <legacyItalic>StatementHandle</legacyItalic> was not in an executed state. The function was called without first calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or a catalog function.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) The driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver, and <legacyBold>SQLBulkOperations</legacyBold> was called for a <legacyItalic>StatementHandle</legacyItalic> before <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLFetch</legacyBold> was called.</para>
              <para>(DM) <legacyBold>SQLBulkOperations</legacyBold> was called after <legacyBold>SQLExtendedFetch</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY011</para>
            </TD>
            <TD>
              <para>Attribute cannot be set now</para>
            </TD>
            <TD>
              <para>(DM) The driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver, and the SQL_ATTR_ROW_STATUS_PTR statement attribute was set between calls to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLBulkOperations</legacyBold>.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD or SQL_UPDATE_BY_BOOKMARK; a data value was not a null pointer; the C data type was SQL_C_BINARY or SQL_C_CHAR; and the column length value was less than 0, but not equal to SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS, or SQL_NULL_DATA, or less than or equal to SQL_LEN_DATA_AT_EXEC_OFFSET.</para>
              <para>The value in a length/indicator buffer was SQL_DATA_AT_EXEC; the SQL type was either SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type; and the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y".</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, the SQL_ATTR_USE_BOOKMARK statement attribute was set to SQL_UB_VARIABLE, and column 0 was bound to a buffer whose length was not equal to the maximum length for the bookmark for this result set. (This length is available in the SQL_DESC_OCTET_LENGTH field of the IRD and can be obtained by calling <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLColAttribute</legacyBold>, or <legacyBold>SQLGetDescField</legacyBold>.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY092</para>
            </TD>
            <TD>
              <para>Invalid attribute identifier</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the <legacyItalic>Operation</legacyItalic> argument was invalid.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ADD, SQL_UPDATE_BY_BOOKMARK, or SQL_DELETE_BY_BOOKMARK, and the SQL_ATTR_CONCURRENCY statement attribute was set to SQL_CONCUR_READ_ONLY.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK, or SQL_UPDATE_BY_BOOKMARK, and the bookmark column was not bound or the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
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
              <para>The driver or data source does not support the operation requested in the <legacyItalic>Operation</legacyItalic> argument.</para>
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
              <para>The query timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtAttr </legacyBold>with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_QUERY_TIMEOUT.</para>
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
      <alert class="caution">
        <para>For information about what statement states <legacyBold>SQLBulkOperations</legacyBold> can be called in and what it must do for compatibility with ODBC 2.<legacyItalic>x</legacyItalic> applications, see the <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink> section in Appendix G: Driver Guidelines for Backward Compatibility.</para>
      </alert>
      <para>An application uses <legacyBold>SQLBulkOperations</legacyBold> to perform the following operations on the base table or view that corresponds to the current query:  </para>
      <list class="bullet">
        <listItem>
          <para>Add new rows.</para>
        </listItem>
        <listItem>
          <para>Update a set of rows where each row is identified by a bookmark.</para>
        </listItem>
        <listItem>
          <para>Delete a set of rows where each row is identified by a bookmark.</para>
        </listItem>
        <listItem>
          <para>Fetch a set of rows where each row is identified by a bookmark.</para>
        </listItem>
      </list>
      <para>After a call to <legacyBold>SQLBulkOperations</legacyBold>, the block cursor position is undefined. The application has to call <legacyBold>SQLFetchScroll</legacyBold> to set the cursor position. An application should call <legacyBold>SQLFetchScroll</legacyBold> only with a <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE, or SQL_FETCH_BOOKMARK. The cursor position is undefined if the application calls <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_PRIOR, SQL_FETCH_NEXT, or SQL_FETCH_RELATIVE.</para>
      <para>A column can be ignored in bulk operations performed by a call to <legacyBold>SQLBulkOperations</legacyBold> by setting the column length/indicator buffer specified in the call to <legacyBold>SQLBindCol</legacyBold>, to SQL_COLUMN_IGNORE.</para>
      <para>It is not necessary for the application to set the SQL_ATTR_ROW_OPERATION_PTR statement attribute when it calls <legacyBold>SQLBulkOperations</legacyBold> because rows cannot be ignored when performing bulk operations with this function.</para>
      <para>The buffer pointed to by the SQL_ATTR_ROWS_FETCHED_PTR statement attribute contains the number of rows affected by a call to <legacyBold>SQLBulkOperations</legacyBold>.</para>
      <para>When the <legacyItalic>Operation</legacyItalic> argument is SQL_ADD or SQL_UPDATE_BY_BOOKMARK and the select-list of the query specification associated with the cursor contains more than one reference to the same column, it is driver-defined whether an error is generated or the driver ignores the duplicated references and performs the requested operations.</para>
      <para>For more information about how to use <legacyBold>SQLBulkOperations</legacyBold>, see <legacyLink xlink:href="7645a704-341e-4267-adbe-061a9fda225b">Updating Data with SQLBulkOperations</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Performing Bulk Inserts</title>
    <content>
      <para>To insert data with <legacyBold>SQLBulkOperations</legacyBold>, an application performs the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Executes a query that returns a result set.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows that it wants to insert.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> to bind the data that it wants to insert. The data is bound to an array with a size equal to the value of SQL_ATTR_ROW_ARRAY_SIZE. </para>
          <alert class="note">
            <para>The size of the array pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute should either be equal to SQL_ATTR_ROW_ARRAY_SIZE or SQL_ATTR_ROW_STATUS_PTR should be a null pointer. </para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBulkOperations</legacyBold>(<legacyItalic>StatementHandle, </legacyItalic>SQL_ADD) to perform the insertion.</para>
        </listItem>
        <listItem>
          <para>If the application has set the SQL_ATTR_ROW_STATUS_PTR statement attribute, it can inspect this array to see the result of the operation. </para>
        </listItem>
      </list>
      <para>If an application binds column 0 before it calls <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_ADD, the driver will update the bound column 0 buffers with the bookmark values for the newly inserted row. For this to occur, the application must have set the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE before executing the statement. (This does not work with an ODBC 2.<legacyItalic>x</legacyItalic> driver.)</para>
      <para>Long data can be added in parts by SQLBulkOperations, by using calls to SQLParamData and SQLPutData. For more information, see "Providing Long Data for Bulk Inserts and Updates" later in this function reference.</para>
      <para>It is not necessary for the application to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> before it calls <legacyBold>SQLBulkOperations</legacyBold> (except when going against an ODBC 2.<legacyItalic>x</legacyItalic> driver; see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>).</para>
      <para>The behavior is driver-defined if <legacyBold>SQLBulkOperations</legacyBold>, with an <legacyItalic>Operation</legacyItalic> argument of SQL_ADD, is called on a cursor that contains duplicate columns. The driver can return a driver-defined SQLSTATE, add the data to the first column that appears in the result set, or perform other driver-defined behavior.</para>
    </content>
  </section>
  <section>
    <title>Performing Bulk Updates by Using Bookmarks</title>
    <content>
      <para>To perform bulk updates by using bookmarks with <legacyBold>SQLBulkOperations</legacyBold>, an application performs the following steps in sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>Sets the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE.</para>
        </listItem>
        <listItem>
          <para>Executes a query that returns a result set.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows that it wants to update.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> to bind the data that it wants to update. The data is bound to an array with a size equal to the value of SQL_ATTR_ROW_ARRAY_SIZE. It also calls <legacyBold>SQLBindCol</legacyBold> to bind column 0 (the bookmark column).</para>
        </listItem>
        <listItem>
          <para>Copies the bookmarks for rows that it is interested in updating into the array bound to column 0.</para>
        </listItem>
        <listItem>
          <para>Updates the data in the bound buffers. </para>
          <alert class="note">
            <para>The size of the array pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute should be equal to SQL_ATTR_ROW_ARRAY_SIZE or SQL_ATTR_ROW_STATUS_PTR should be a null pointer.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBulkOperations</legacyBold>(<legacyItalic>StatementHandle, </legacyItalic>SQL_UPDATE_BY_BOOKMARK). </para>
          <alert class="note">
            <para>If the application has set the SQL_ATTR_ROW_STATUS_PTR statement attribute, it can inspect this array to see the result of the operation.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Optionally calls <legacyBold>SQLBulkOperations</legacyBold>(<legacyItalic>StatementHandle</legacyItalic>, SQL_FETCH_BY_BOOKMARK) to fetch data into the bound application buffers to verify that the update has occurred.</para>
        </listItem>
        <listItem>
          <para>If data has been updated, the driver changes the value in the row status array for the appropriate rows to SQL_ROW_UPDATED.</para>
        </listItem>
      </list>
      <para>Bulk updates performed by <legacyBold>SQLBulkOperations</legacyBold> can include long data by using calls to <legacyBold>SQLParamData</legacyBold> and <legacyBold>SQLPutData</legacyBold>. For more information, see "Providing Long Data for Bulk Inserts and Updates" later in this function reference.</para>
      <para>If bookmarks persist across cursors, the application does not need to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> before updating by bookmarks. It can use bookmarks that it has stored from a previous cursor. If bookmarks do not persist across cursors, the application has to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> to retrieve the bookmarks.</para>
      <para>The behavior is driver-defined if <legacyBold>SQLBulkOperations</legacyBold>, with an <legacyItalic>Operation</legacyItalic> argument of SQL_UPDATE_BY_BOOKMARK, is called on a cursor that contains duplicate columns. The driver can return a driver-defined SQLSTATE, update the first column that appears in the result set, or perform other driver-defined behavior.</para>
    </content>
  </section>
  <section>
    <title>Performing Bulk Fetches Using Bookmarks</title>
    <content>
      <para>To perform bulk fetches using bookmarks with <legacyBold>SQLBulkOperations</legacyBold>, an application performs the following steps in sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>Sets the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE.</para>
        </listItem>
        <listItem>
          <para>Executes a query that returns a result set.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows that it wants to fetch.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> to bind the data that it wants to fetch. The data is bound to an array with a size equal to the value of SQL_ATTR_ROW_ARRAY_SIZE. It also calls <legacyBold>SQLBindCol</legacyBold> to bind column 0 (the bookmark column).</para>
        </listItem>
        <listItem>
          <para>Copies the bookmarks for rows that it is interested in fetching into the array bound to column 0. (This assumes that the application has already obtained the bookmarks separately.) </para>
          <alert class="note">
            <para>The size of the array pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute should be equal to SQL_ATTR_ROW_ARRAY_SIZE or SQL_ATTR_ROW_STATUS_PTR should be a null pointer.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBulkOperations</legacyBold>(<legacyItalic>StatementHandle, </legacyItalic>SQL_FETCH_BY_BOOKMARK).</para>
        </listItem>
        <listItem>
          <para>If the application has set the SQL_ATTR_ROW_STATUS_PTR statement attribute, it can inspect this array to see the result of the operation.</para>
        </listItem>
      </list>
      <para>If bookmarks persist across cursors, the application does not need to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> before fetching by bookmarks. It can use bookmarks that it has stored from a previous cursor. If bookmarks do not persist across cursors, the application has to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll </legacyBold>one time to retrieve the bookmarks.</para>
    </content>
  </section>
  <section>
    <title>Performing Bulk Deletes Using Bookmarks</title>
    <content>
      <para>To perform bulk deletes using bookmarks with <legacyBold>SQLBulkOperations</legacyBold>, an application performs the following steps in sequence:  </para>
      <list class="ordered">
        <listItem>
          <para>Sets the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE.</para>
        </listItem>
        <listItem>
          <para>Executes a query that returns a result set.</para>
        </listItem>
        <listItem>
          <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows that it wants to delete.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBindCol</legacyBold> to bind column 0 (the bookmark column).</para>
        </listItem>
        <listItem>
          <para>Copies the bookmarks for rows that it is interested in deleting into the array bound to column 0. </para>
          <alert class="note">
            <para>The size of the array pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute should be equal to SQL_ATTR_ROW_ARRAY_SIZE or SQL_ATTR_ROW_STATUS_PTR should be a null pointer.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLBulkOperations</legacyBold>(<legacyItalic>StatementHandle, </legacyItalic>SQL_DELETE_BY_BOOKMARK).</para>
        </listItem>
        <listItem>
          <para>If the application has set the SQL_ATTR_ROW_STATUS_PTR statement attribute, it can inspect this array to see the result of the operation.</para>
        </listItem>
      </list>
      <para>If bookmarks persist across cursors, the application does not have to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> before deleting by bookmarks. It can use bookmarks that it has stored from a previous cursor. If bookmarks do not persist across cursors, the application has to call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll </legacyBold>one time to retrieve the bookmarks.</para>
    </content>
  </section>
  <section>
    <title>Providing Long Data for Bulk Inserts and Updates</title>
    <content>
      <para>Long data can be provided for bulk inserts and updates performed by calls to <legacyBold>SQLBulkOperations</legacyBold>. To insert or update long data, an application performs the following steps in addition to the steps described in the "Performing Bulk Inserts" and "Performing Bulk Updates Using Bookmarks" sections earlier in this topic.  </para>
      <list class="ordered">
        <listItem>
          <para>When it binds the data by using <legacyBold>SQLBindCol</legacyBold>, the application places an application-defined value, such as the column number, in the <legacyItalic>*TargetValuePtr</legacyItalic> buffer for data-at-execution columns. The value can be used later to identify the column. </para>
          <para>The application places the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro in the <legacyItalic>*StrLen_or_IndPtr</legacyItalic> buffer. If the SQL data type of the column is SQL_LONGVARBINARY, SQL_LONGVARCHAR, or a long data source–specific data type and the driver returns "Y" for the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold>, <legacyItalic>length</legacyItalic> is the number of bytes of data to be sent for the parameter; otherwise, it must be a nonnegative value and is ignored. </para>
        </listItem>
        <listItem>
          <para>When <legacyBold>SQLBulkOperations</legacyBold> is called, if there are data-at-execution columns, the function returns SQL_NEED_DATA and proceeds to step 3, which follows. (If there are no data-at-execution columns, the process is complete.)</para>
        </listItem>
        <listItem>
          <para>The application calls <legacyBold>SQLParamData</legacyBold> to retrieve the address of the <legacyItalic>*TargetValuePtr</legacyItalic> buffer for the first data-at-execution column to be processed. <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA. The application retrieves the application-defined value from the <legacyItalic>*TargetValuePtr</legacyItalic> buffer. </para>
          <alert class="note">
            <para>Although data-at-execution parameters resemble data-at-execution columns, the value returned by <legacyBold>SQLParamData</legacyBold> is different for each.</para>
          </alert>
          <para>Data-at-execution columns are columns in a rowset for which data will be sent with <legacyBold>SQLPutData</legacyBold> when a row is updated or inserted with <legacyBold>SQLBulkOperations</legacyBold>. They are bound with <legacyBold>SQLBindCol</legacyBold>. The value returned by <legacyBold>SQLParamData</legacyBold> is the address of the row in the *<legacyItalic>TargetValuePtr</legacyItalic> buffer that is being processed. </para>
        </listItem>
        <listItem>
          <para>The application calls <legacyBold>SQLPutData</legacyBold> one or more times to send data for the column. More than one call is needed if all the data value cannot be returned in the <legacyItalic>*TargetValuePtr</legacyItalic> buffer specified in <legacyBold>SQLPutData</legacyBold>; multiple calls to <legacyBold>SQLPutData</legacyBold> for the same column are allowed only when sending character C data to a column with a character, binary, or data source–specific data type or when sending binary C data to a column with a character, binary, or data source–specific data type.</para>
        </listItem>
        <listItem>
          <para>The application calls <legacyBold>SQLParamData</legacyBold> again to signal that all data has been sent for the column. </para>
          <list class="bullet">
            <listItem>
              <para>If there are more data-at-execution columns, <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA and the address of the <legacyItalic>TargetValuePtr</legacyItalic> buffer for the next data-at-execution column to be processed. The application repeats steps 4 and 5.</para>
            </listItem>
            <listItem>
              <para>If there are no more data-at-execution columns, the process is complete. If the statement was executed successfully, <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO; if the execution failed, it returns SQL_ERROR. At this point, <legacyBold>SQLParamData</legacyBold> can return any SQLSTATE that can be returned by <legacyBold>SQLBulkOperations</legacyBold>.</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>If the operation is canceled or an error occurs in <legacyBold>SQLParamData</legacyBold> or <legacyBold>SQLPutData</legacyBold> after <legacyBold>SQLBulkOperations</legacyBold> returns SQL_NEED_DATA and before data is sent for all data-at-execution columns, the application can call only <legacyBold>SQLCancel</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, <legacyBold>SQLGetDiagRec</legacyBold>, <legacyBold>SQLGetFunctions</legacyBold>, <legacyBold>SQLParamData</legacyBold>, or <legacyBold>SQLPutData</legacyBold> for the statement or the connection associated with the statement. If it calls any other function for the statement or the connection associated with the statement, the function returns SQL_ERROR and SQLSTATE HY010 (Function sequence error).</para>
      <para>If the application calls <legacyBold>SQLCancel</legacyBold> while the driver still needs data for data-at-execution columns, the driver cancels the operation. The application can then call <legacyBold>SQLBulkOperations</legacyBold> again; canceling does not affect the cursor state or the current cursor position.</para>
    </content>
  </section>
  <section>
    <title>Row Status Array</title>
    <content>
      <para>The row status array contains status values for each row of data in the rowset after a call to <legacyBold>SQLBulkOperations</legacyBold>. The driver sets the status values in this array after a call to <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLSetPos</legacyBold>, or <legacyBold>SQLBulkOperations</legacyBold>. This array is initially populated by a call to <legacyBold>SQLBulkOperations</legacyBold> if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not been called before <legacyBold>SQLBulkOperations</legacyBold>. This array is pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute. The number of elements in the row status arrays must equal the number of rows in the rowset (as defined by the SQL_ATTR_ROW_ARRAY_SIZE statement attribute). For information about this row status array, see <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>The following example fetches 10 rows of data at a time from the Customers table. It then prompts the user for an action to take. To reduce network traffic, the example buffer updates, deletes, and inserts locally in the bound arrays, but at offsets past the rowset data. When the user chooses to send updates, deletes, and inserts to the data source, the code sets the binding offset appropriately and calls <legacyBold>SQLBulkOperations</legacyBold>. For simplicity, the user cannot buffer more than 10 updates, deletes, or inserts.</para>
      <code>// SQLBulkOperations_Function.cpp
// compile with: ODBC32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#include "stdio.h"

#define UPDATE_ROW 100
#define DELETE_ROW 101
#define ADD_ROW 102
#define SEND_TO_DATA_SOURCE 103
#define UPDATE_OFFSET 10
#define INSERT_OFFSET 20
#define DELETE_OFFSET 30

// Define structure for customer data (assume 10 byte maximum bookmark size).
typedef struct tagCustStruct {
   SQLCHAR Bookmark[10];
   SQLINTEGER BookmarkLen;
   SQLUINTEGER CustomerID;
   SQLINTEGER CustIDInd;
   SQLCHAR CompanyName[51];
   SQLINTEGER NameLenOrInd;
   SQLCHAR Address[51];
   SQLINTEGER AddressLenOrInd;
   SQLCHAR Phone[11];
   SQLINTEGER PhoneLenOrInd;
} CustStruct;

// Allocate 40 of these structures. Elements 0-9 are for the current rowset,
// elements 10-19 are for the buffered updates, elements 20-29 are for
// the buffered inserts, and elements 30-39 are for the buffered deletes.
CustStruct CustArray[40];
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,
NumDeletes = 0;
SQLLEN BindOffset = 0;
SQLRETURN retcode;
SQLHENV henv = NULL;
SQLHDBC hdbc = NULL;
SQLHSTMT hstmt = NULL;

int main() {
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 

   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   // Set the following statement attributes:
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise
   // SQL_ATTR_ROW_ARRAY_SIZE:        10
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &amp;BindOffset, 0);

   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &amp;CustArray[0].BookmarkLen);
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &amp;CustArray[0].CustomerID, 0, &amp;CustArray[0].CustIDInd);
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &amp;CustArray[0].NameLenOrInd);
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &amp;CustArray[0].AddressLenOrInd);
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &amp;CustArray[0].PhoneLenOrInd);

   // Execute a statement to retrieve rows from the Customers table.
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);

   // Fetch and display the first 10 rows.
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);
   // DisplayCustData(CustArray, 10);

   // Call GetAction to get an action and a row number from the user.
   // while (GetAction(&amp;Action, &amp;RowNum)) {
   Action = SQL_FETCH_NEXT;
   RowNum = 2;
   switch (Action) {
      case SQL_FETCH_NEXT:
      case SQL_FETCH_PRIOR:
      case SQL_FETCH_FIRST:
      case SQL_FETCH_LAST:
      case SQL_FETCH_ABSOLUTE:
      case SQL_FETCH_RELATIVE:
         // Fetch and display the requested data.
         SQLFetchScroll(hstmt, Action, RowNum);
         // DisplayCustData(CustArray, 10);
         break;

      case UPDATE_ROW:
         // Check if we have reached the maximum number of buffered updates.
         if (NumUpdates &lt; 10) {
            // Get the new customer data and place it in the next available element of
            // the buffered updates section of CustArray, copy the bookmark of the row
            // being updated to the same element, and increment the update counter.
            // Checking to see we have not already buffered an update for this
            // row not shown.
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,
               CustArray[RowNum - 1].Bookmark,
               CustArray[RowNum - 1].BookmarkLen);
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =
               CustArray[RowNum - 1].BookmarkLen;
            NumUpdates++;
         } else {
            printf("Buffers full. Send buffered changes to the data source.");
         }
         break;
      case DELETE_ROW:
         // Check if we have reached the maximum number of buffered deletes.
         if (NumDeletes &lt; 10) {
            // Copy the bookmark of the row being deleted to the next available element
            // of the buffered deletes section of CustArray and increment the delete
            // counter. Checking to see we have not already buffered an update for
            // this row not shown.
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,
               CustArray[RowNum - 1].Bookmark,
               CustArray[RowNum - 1].BookmarkLen);

            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =
               CustArray[RowNum - 1].BookmarkLen;

            NumDeletes++;
         } else
            printf("Buffers full. Send buffered changes to the data source.");
         break;

      case ADD_ROW:
         // reached maximum number of buffered inserts?
         if (NumInserts &lt; 10) {
            // Get the new customer data and place it in the next available element of
            // the buffered inserts section of CustArray and increment insert counter.
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);
            NumInserts++;
         } else
            printf("Buffers full. Send buffered changes to the data source.");
         break;

      case SEND_TO_DATA_SOURCE:
         // If there are any buffered updates, inserts, or deletes, set the array size
         // to that number, set the binding offset to use the data in the buffered
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to
         // do the updates, inserts, or deletes. Because we will never have more than
         // 10 updates, inserts, or deletes, we can use the same row status array.
         if (NumUpdates) {
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);
            NumUpdates = 0;
         }

         if (NumInserts) {
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);
            SQLBulkOperations(hstmt, SQL_ADD);
            NumInserts = 0;
         }

         if (NumDeletes) {
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);
            NumDeletes = 0;
         }

         // If there were any updates, inserts, or deletes, reset the binding offset
         // and array size to their original values.
         if (NumUpdates || NumInserts || NumDeletes) {
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);
            BindOffset = 0;
         }
         break;
   }
   // }

   // Close the cursor.
   SQLFreeStmt(hstmt, SQL_CLOSE);
}</code>
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
              <para>Getting a single field of a descriptor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting multiple fields of a descriptor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a single field of a descriptor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting multiple fields of a descriptor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Positioning the cursor, refreshing data in the rowset, or updating or deleting data in the rowset</para>
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