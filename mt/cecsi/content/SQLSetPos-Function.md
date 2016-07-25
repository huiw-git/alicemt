---
title: "SQLSetPos Function"
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
  - SQLSetPos
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
caps.latest.revision: 30
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetPos Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ODBC </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLSetPos</legacyBold> sets the cursor position in a rowset and allows an application to refresh data in the rowset or to update or delete data in the result set.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetPos</legacyBold>(
      SQLHSTMT        <parameterReference>StatementHandle</parameterReference>,
      SQLSETPOSIROW   <parameterReference>RowNumber</parameterReference>,
      SQLUSMALLINT    <parameterReference>Operation</parameterReference>,
      SQLUSMALLINT    <parameterReference>LockType</parameterReference>);</legacySyntax>
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
          <legacyItalic>RowNumber</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Position of the row in the rowset on which to perform the operation specified with the <legacyItalic>Operation</legacyItalic> argument. If <legacyItalic>RowNumber</legacyItalic> is 0, the operation applies to every row in the rowset.</para>
          <para>For additional information, see "Comments." </para>
        </definition>
        <definedTerm>
          <legacyItalic>Operation</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Operation to perform:</para>
          <para>SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE   </para>
          <alert class="note">
            <para>The SQL_ADD value for the <legacyItalic>Operation</legacyItalic> argument has been deprecated for ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3.<legacyItalic>x</legacyItalic> drivers will need to support SQL_ADD for backward compatibility. This functionality has been replaced by a call to <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD. When an ODBC 3.<legacyItalic>x</legacyItalic> application works with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the Driver Manager maps a call to <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD.</para>
          </alert>
          <para>For more information, see "Comments." </para>
        </definition>
        <definedTerm>
          <legacyItalic>LockType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Specifies how to lock the row after performing the operation specified in the <legacyItalic>Operation</legacyItalic> argument.</para>
          <para>SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK </para>
          <para>For more information, see "Comments." </para>
        </definition>
      </definitionTable>
      <para>
        <legacyBold>Returns</legacyBold>
      </para>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLSetPos</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetPos</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise. </para>
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
              <para>01001</para>
            </TD>
            <TD>
              <para>Cursor operation conflict</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_DELETE or SQL_UPDATE, and no rows or more than one row were deleted or updated. (For more information about updates to more than one row, see the description of the SQL_ATTR_SIMULATE_CURSOR <legacyItalic>Attribute</legacyItalic> in <legacyBold>SQLSetStmtAttr</legacyBold>.) (Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_DELETE or SQL_UPDATE, and the operation failed because of optimistic concurrency. (Function returns SQL_SUCCESS_WITH_INFO.) </para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_REFRESH, and string or binary data returned for a column or columns with a data type of SQL_C_CHAR or SQL_C_BINARY resulted in the truncation of nonblank character or non-NULL binary data.</para>
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
              <para>The <legacyItalic>RowNumber</legacyItalic> argument was 0, and an error occurred in one or more rows while performing the operation specified with the <legacyItalic>Operation</legacyItalic> argument. </para>
              <para>(SQL_SUCCESS_WITH_INFO is returned if an error occurs on one or more, but not all, rows of a multirow operation, and SQL_ERROR is returned if an error occurs on a single-row operation.)</para>
              <para>(This SQLSTATE is returned only when <legacyBold>SQLSetPos</legacyBold> is called after <legacyBold>SQLExtendedFetch</legacyBold>, if the driver is an ODBC 2.<legacyItalic>x</legacyItalic> driver and the cursor library is not used.)</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_REFRESH, the data type of the application buffer was not SQL_C_CHAR or SQL_C_BINARY, and the data returned to application buffers for one or more columns was truncated. For numeric data types, the fractional part of the number was truncated. For time, timestamp, and interval data types containing a time component, the fractional portion of the time was truncated. </para>
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
              <para>The data value of a column in the result set could not be converted to the data type specified by <legacyItalic>TargetType</legacyItalic> in the call to <legacyBold>SQLBindCol</legacyBold>.</para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_REFRESH or SQL_UPDATE, and a column was bound with a column number greater than the number of columns in the result set.</para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_UPDATE, and no columns were updatable because all columns were either unbound, read-only, or the value in the bound length/indicator buffer was SQL_COLUMN_IGNORE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22001</para>
            </TD>
            <TD>
              <para>String data, right truncation</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, and the assignment of a character or binary value to a column resulted in the truncation of nonblank (for characters) or non-null (for binary) characters or bytes.</para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_UPDATE, and the assignment of a numeric value to a column in the result set caused the whole (as opposed to fractional) part of the number to be truncated.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_REFRESH, and returning the numeric value for one or more bound columns would have caused a loss of significant digits.</para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_UPDATE, and the assignment of a date or timestamp value to a column in the result set caused the year, month, or day field to be out of range. </para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_REFRESH, and returning the date or timestamp value for one or more bound columns would have caused the year, month, or day field to be out of range.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22008</para>
            </TD>
            <TD>
              <para>Date/time field  overflow</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, and the performance of datetime arithmetic on data being sent to a column in the result set resulted in a datetime field (the year, month, day, hour, minute, or second field) of the result being outside the permissible range of values for the field, or being invalid based on the Gregorian calendar's natural rules for datetimes.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_REFRESH, and the performance of datetime arithmetic on data being retrieved from the result set resulted in a datetime field (the year, month, day, hour, minute, or second field) of the result being outside the permissible range of values for the field, or being invalid based on the Gregorian calendar's natural rules for datetimes.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, and the assignment of an exact numeric or interval C type to an interval SQL data type caused a loss of significant digits.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE; when assigning to an interval SQL type, there was no representation of the value of the C type in the interval SQL type.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_REFRESH, and assigning from an exact numeric or interval SQL type to an interval C type caused a loss of significant digits in the leading field.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_ REFRESH; when assigning to an interval C type, there was no representation of the value of the SQL type in the interval C type. </para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_REFRESH; the C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_UPDATE; the SQL type was an exact or approximate numeric, a datetime, or an interval data type; the C type was SQL_C_CHAR; and the value in the column was not a valid literal of the bound SQL type. </para>
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
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_DELETE or SQL_UPDATE, and an integrity constraint was violated.</para>
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
              <para>(DM) A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, but <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had not been called.</para>
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called, but the cursor was positioned before the start of the result set or after the end of the result set.</para>
              <para>The argument <legacyItalic>Operation</legacyItalic> was SQL_DELETE, SQL_REFRESH, or SQL_UPDATE, and the cursor was positioned before the start of the result set or after the end of the result set.</para>
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
              <para>The transaction was rolled back due to a resource deadlock with another transaction.</para>
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
              <para>The driver was unable to lock the row as needed to perform the operation requested in the argument <legacyItalic>Operation</legacyItalic>.</para>
              <para>The driver was unable to lock the row as requested in the argument <legacyItalic>LockType</legacyItalic>.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, and the update was performed on a viewed table or a table derived from the viewed table which was created by specifying <legacyBold>WITH CHECK OPTION</legacyBold>, such that one or more rows affected by the update will no longer be present in the viewed table.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the SQLSetPos function was called.</para>
              <para> (DM) The specified <legacyItalic>StatementHandle</legacyItalic> was not in an executed state. The function was called without first calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or a catalog function.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos </legacyBold>was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) The driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver, and <legacyBold>SQLSetPos</legacyBold> was called for a <legacyItalic>StatementHandle</legacyItalic> after <legacyBold>SQLFetch</legacyBold> was called.</para>
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
              <para>(DM) The driver was an ODBC 2.<legacyItalic>x</legacyItalic> driver; the SQL_ATTR_ROW_STATUS_PTR statement attribute was set; then <legacyBold>SQLSetPos</legacyBold> was called before <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLExtendedFetch</legacyBold> was called.</para>
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
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, a data value was a null pointer, and the column length value was not 0, SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NULL_DATA, or less than or equal to SQL_LEN_DATA_AT_EXEC_OFFSET.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE; a data value was not a null pointer; the C data type was SQL_C_BINARY or SQL_C_CHAR; and the column length value was less than 0 but not equal to SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS, or SQL_NULL_DATA, or less than or equal to SQL_LEN_DATA_AT_EXEC_OFFSET.</para>
              <para>The value in a length/indicator buffer was SQL_DATA_AT_EXEC; the SQL type was either SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type; and the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y".</para>
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
              <para>(DM) The value specified for the <legacyItalic>LockType</legacyItalic> argument was invalid.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE or SQL_DELETE, and the SQL_ATTR_CONCURRENCY statement attribute was SQL_ATTR_CONCUR_READ_ONLY.</para>
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
              <para>The value specified for the argument <legacyItalic>RowNumber</legacyItalic> was greater than the number of rows in the rowset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY109</para>
            </TD>
            <TD>
              <para>Invalid cursor position</para>
            </TD>
            <TD>
              <para>The cursor associated with the <legacyItalic>StatementHandle</legacyItalic> was defined as forward-only, so the cursor could not be positioned within the rowset. See the description for the SQL_ATTR_CURSOR_TYPE attribute in <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
              <para>The <legacyItalic>Operation</legacyItalic> argument was SQL_UPDATE, SQL_DELETE, or SQL_REFRESH, and the row identified by the <legacyItalic>RowNumber</legacyItalic> argument had been deleted or had not been fetched.</para>
              <para>(DM) The <legacyItalic>RowNumber</legacyItalic> argument was 0, and the <legacyItalic>Operation</legacyItalic> argument was SQL_POSITION.</para>
              <para>
                <legacyBold>SQLSetPos</legacyBold> was called after <legacyBold>SQLBulkOperations</legacyBold> was called and before <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLFetch</legacyBold> was called.</para>
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
              <para>The driver or data source does not support the operation requested in the <legacyItalic>Operation</legacyItalic> argument or the <legacyItalic>LockType</legacyItalic> argument.</para>
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
              <para>The query timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_QUERY_TIMEOUT.</para>
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
        <para>For information on the statement states that <legacyBold>SQLSetPos</legacyBold> can be called in and what it needs to do for compatibility with ODBC 2<legacyItalic>.x</legacyItalic> applications, see <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>RowNumber Argument</title>
    <content>
      <para>The <legacyItalic>RowNumber</legacyItalic> argument specifies the number of the row in the rowset on which to perform the operation specified by the <legacyItalic>Operation</legacyItalic> argument. If <legacyItalic>RowNumber</legacyItalic> is 0, the operation applies to every row in the rowset. <legacyItalic>RowNumber</legacyItalic> must be a value from 0 to the number of rows in the rowset. </para>
      <alert class="note">
        <para>In the C language, arrays are 0-based and the <legacyItalic>RowNumber</legacyItalic> argument is 1-based. For example, to update the fifth row of the rowset, an application modifies the rowset buffers at array index 4 but specifies a <legacyItalic>RowNumber</legacyItalic> of 5.</para>
      </alert>
      <para>All operations position the cursor on the row specified by <legacyItalic>RowNumber</legacyItalic>. The following operations require a cursor position:  </para>
      <list class="bullet">
        <listItem>
          <para>Positioned update and delete statements.</para>
        </listItem>
        <listItem>
          <para>Calls to <legacyBold>SQLGetData</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>Calls to <legacyBold>SQLSetPos</legacyBold> with the SQL_DELETE, SQL_REFRESH, and SQL_UPDATE options.</para>
        </listItem>
      </list>
      <para>For example, if <legacyItalic>RowNumber</legacyItalic> is 2 for a call to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_DELETE, the cursor is positioned on the second row of the rowset and that row is deleted. The entry in the implementation row status array (pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute) for the second row is changed to SQL_ROW_DELETED.</para>
      <para>An application can specify a cursor position when it calls <legacyBold>SQLSetPos</legacyBold>. Generally, it calls <legacyBold>SQLSetPos</legacyBold> with the SQL_POSITION or SQL_REFRESH operation to position the cursor before executing a positioned update or delete statement or calling <legacyBold>SQLGetData</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Operation Argument</title>
    <content>
      <para>The <legacyItalic>Operation</legacyItalic> argument supports the following operations. To determine which options are supported by a data source, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 information type (depending on the type of the cursor).</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>Operation</legacyItalic>
              </para>
              <para>argument</para>
            </TD>
            <TD>
              <para>Operation</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_POSITION</para>
            </TD>
            <TD>
              <para>The driver positions the cursor on the row specified by <legacyItalic>RowNumber</legacyItalic>.</para>
              <para>The contents of the row status array pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute are ignored for the SQL_POSITION <legacyItalic>Operation</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_REFRESH</para>
            </TD>
            <TD>
              <para>The driver positions the cursor on the row specified by <legacyItalic>RowNumber</legacyItalic> and refreshes data in the rowset buffers for that row. For more information about how the driver returns data in the rowset buffers, see the descriptions of row-wise and column-wise binding in <legacyBold>SQLBindCol</legacyBold>.</para>
              <para>
                <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_REFRESH updates the status and content of the rows within the current fetched rowset. This includes refreshing the bookmarks. Because the data in the buffers is refreshed but not refetched, the membership in the rowset is fixed. This is different from the refresh performed by a call to <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_RELATIVE and a <legacyItalic>RowNumber</legacyItalic> equal to 0, which refetches the rowset from the result set so that it can show added data and remove deleted data if those operations are supported by the driver and the cursor.</para>
              <para>A successful refresh with <legacyBold>SQLSetPos</legacyBold> will not change a row status of SQL_ROW_DELETED. Deleted rows within the rowset will continue to be marked as deleted until the next fetch. The rows will disappear at the next fetch if the cursor supports packing (in which a subsequent <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> does not return deleted rows).</para>
              <para>Added rows do not appear when a refresh with <legacyBold>SQLSetPos</legacyBold> is performed. This behavior is different from <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchType</legacyItalic> of SQL_FETCH_RELATIVE and a <legacyItalic>RowNumber</legacyItalic> equal to 0, which also refreshes the current rowset but will show added records or pack deleted records if these operations are supported by the cursor.</para>
              <para>A successful refresh with <legacyBold>SQLSetPos</legacyBold> will change a row status of SQL_ROW_ADDED to SQL_ROW_SUCCESS (if the row status array exists).</para>
              <para>A successful refresh with <legacyBold>SQLSetPos</legacyBold> will change a row status of SQL_ROW_UPDATED to the row's new status (if the row status array exists).</para>
              <para>If an error occurs in a <legacyBold>SQLSetPos</legacyBold> operation on a row, the row status is set to SQL_ROW_ERROR (if the row status array exists).</para>
              <para>For a cursor opened with an SQL_ATTR_CONCURRENCY statement attribute of SQL_CONCUR_ROWVER or SQL_CONCUR_VALUES, a refresh with <legacyBold>SQLSetPos</legacyBold> might update the optimistic concurrency values used by the data source to detect that the row has changed. If this occurs, the row versions or values used to ensure cursor concurrency are updated whenever the rowset buffers are refreshed from the server. This occurs for each row that is refreshed. </para>
              <para>The contents of the row status array pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute are ignored for the SQL_REFRESH <legacyItalic>Operation</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_UPDATE</para>
            </TD>
            <TD>
              <para>The driver positions the cursor on the row specified by <legacyItalic>RowNumber</legacyItalic> and updates the underlying row of data with the values in the rowset buffers (the <legacyItalic>TargetValuePtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>). It retrieves the lengths of the data from the length/indicator buffers (the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>). If the length of any column is SQL_COLUMN_IGNORE, the column is not updated. After updating the row, the driver changes the corresponding element of the row status array to SQL_ROW_UPDATED or SQL_ROW_SUCCESS_WITH_INFO (if the row status array exists).</para>
              <para>It is driver-defined what the behavior is if <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_UPDATE is called on a cursor that contains duplicate columns. The driver can return a driver-defined SQLSTATE, can update the first column that appears in the result set, or perform other driver-defined behavior.</para>
              <para>The row operation array pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute can be used to indicate that a row in the current rowset should be ignored during a bulk update. For more information, see "Status and Operation Arrays" later in this function reference.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DELETE</para>
            </TD>
            <TD>
              <para>The driver positions the cursor on the row specified by <legacyItalic>RowNumber</legacyItalic> and deletes the underlying row of data. It changes the corresponding element of the row status array to SQL_ROW_DELETED. After the row has been deleted, the following are not valid for the row: positioned update and delete statements, calls to <legacyBold>SQLGetData</legacyBold>, and calls to <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to anything except SQL_POSITION. For drivers that support packing, the row is deleted from the cursor when new data is retrieved from the data source.</para>
              <para>Whether the row remains visible depends on the cursor type. For example, deleted rows are visible to static and keyset-driven cursors but invisible to dynamic cursors. </para>
              <para>The row operation array pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute can be used to indicate that a row in the current rowset should be ignored during a bulk delete. For more information, see "Status and Operation Arrays" later in this function reference.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>LockType Argument</title>
    <content>
      <para>The <legacyItalic>LockType</legacyItalic> argument provides a way for applications to control concurrency. In most cases, data sources that support concurrency levels and transactions will support only the SQL_LOCK_NO_CHANGE value of the <legacyItalic>LockType</legacyItalic> argument. The <legacyItalic>LockType</legacyItalic> argument is generally used only for file-based support.</para>
      <para>The <legacyItalic>LockType</legacyItalic> argument specifies the lock state of the row after <legacyBold>SQLSetPos</legacyBold> has been executed. If the driver is unable to lock the row either to perform the requested operation or to satisfy the <legacyItalic>LockType</legacyItalic> argument, it returns SQL_ERROR and SQLSTATE 42000 (Syntax error or access violation).</para>
      <para>Although the <legacyItalic>LockType</legacyItalic> argument is specified for a single statement, the lock accords the same privileges to all statements on the connection. In particular, a lock that is acquired by one statement on a connection can be unlocked by a different statement on the same connection.</para>
      <para>A row locked through <legacyBold>SQLSetPos</legacyBold> remains locked until the application calls <legacyBold>SQLSetPos</legacyBold> for the row with <legacyItalic>LockType</legacyItalic> set to SQL_LOCK_UNLOCK, or until the application calls <legacyBold>SQLFreeHandle</legacyBold> for the statement or <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option. For a driver that supports transactions, a row locked through <legacyBold>SQLSetPos</legacyBold> is unlocked when the application calls <legacyBold>SQLEndTran</legacyBold> to commit or roll back a transaction on the connection (if a cursor is closed when a transaction is committed or rolled back, as indicated by the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR information types returned by <legacyBold>SQLGetInfo</legacyBold>).</para>
      <para>The <legacyItalic>LockType</legacyItalic> argument supports the following types of locks. To determine which locks are supported by a data source, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 information type (depending on the type of the cursor).</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>LockType</legacyItalic> argument</para>
            </TD>
            <TD>
              <para>Lock type</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_LOCK_NO_CHANGE</para>
            </TD>
            <TD>
              <para>The driver or data source ensures that the row is in the same locked or unlocked state as it was before <legacyBold>SQLSetPos</legacyBold> was called. This value of <legacyItalic>LockType</legacyItalic> allows data sources that do not support explicit row-level locking to use whatever locking is required by the current concurrency and transaction isolation levels.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_LOCK_EXCLUSIVE</para>
            </TD>
            <TD>
              <para>The driver or data source locks the row exclusively. A statement on a different connection or in a different application cannot be used to acquire any locks on the row.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_LOCK_UNLOCK</para>
            </TD>
            <TD>
              <para>The driver or data source unlocks the row.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>If a driver supports SQL_LOCK_EXCLUSIVE but does not support SQL_LOCK_UNLOCK, a row that is locked will remain locked until one of the function calls described in the previous paragraph occurs.</para>
      <para>If a driver supports SQL_LOCK_EXCLUSIVE but does not support SQL_LOCK_UNLOCK, a row that is locked will remain locked until the application calls <legacyBold>SQLFreeHandle</legacyBold> for the statement or <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option. If the driver supports transactions and closes the cursor upon committing or rolling back the transaction, the application calls <legacyBold>SQLEndTran</legacyBold>. </para>
      <para>For the update and delete operations in <legacyBold>SQLSetPos</legacyBold>, the application uses the <legacyItalic>LockType</legacyItalic> argument as follows:  </para>
      <list class="bullet">
        <listItem>
          <para>To guarantee that a row does not change after it is retrieved, an application calls <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_REFRESH and <legacyItalic>LockType</legacyItalic> set to SQL_LOCK_EXCLUSIVE.</para>
        </listItem>
        <listItem>
          <para>If the application sets <legacyItalic>LockType</legacyItalic> to SQL_LOCK_NO_CHANGE, the driver guarantees that an update or delete operation will succeed only if the application specified SQL_CONCUR_LOCK for the SQL_ATTR_CONCURRENCY statement attribute.</para>
        </listItem>
        <listItem>
          <para>If the application specifies SQL_CONCUR_ROWVER or SQL_CONCUR_VALUES for the SQL_ATTR_CONCURRENCY statement attribute, the driver compares row versions or values and rejects the operation if the row has changed since the application fetched the row.</para>
        </listItem>
        <listItem>
          <para>If the application specifies SQL_CONCUR_READ_ONLY for the SQL_ATTR_CONCURRENCY statement attribute, the driver rejects any update or delete operation.</para>
        </listItem>
      </list>
      <para>For more information about the SQL_ATTR_CONCURRENCY statement attribute, see <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Status and Operation Arrays</title>
    <content>
      <para>The following status and operation arrays are used when calling <legacyBold>SQLSetPos</legacyBold>:  </para>
      <list class="bullet">
        <listItem>
          <para>The row status array (as pointed to by the SQL_DESC_ARRAY_STATUS_PTR field in the IRD and the SQL_ATTR_ROW_STATUS_ARRAY statement attribute) contains status values for each row of data in the rowset. The driver sets the status values in this array after a call to <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>,<legacyBold> SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>. This array is pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute.</para>
        </listItem>
        <listItem>
          <para>The row operation array (as pointed to by the SQL_DESC_ARRAY_STATUS_PTR field in the ARD and the SQL_ATTR_ROW_OPERATION_ARRAY statement attribute) contains a value for each row in the rowset that indicates whether a call to <legacyBold>SQLSetPos</legacyBold> for a bulk operation is ignored or performed. Each element in the array is set to either SQL_ROW_PROCEED (the default) or SQL_ROW_IGNORE. This array is pointed to by the SQL_ATTR_ROW_OPERATION_PTR statement attribute.</para>
        </listItem>
      </list>
      <para>The number of elements in the status and operation arrays must equal the number of rows in the rowset (as defined by the SQL_ATTR_ROW_ARRAY_SIZE statement attribute).</para>
      <para>For information about the row status array, see <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>. For information about the row operation array, see "Ignoring a Row in a Bulk Operation," later in this section. </para>
    </content>
  </section>
  <section>
    <title>Using SQLSetPos</title>
    <content>
      <para>Before an application calls <legacyBold>SQLSetPos</legacyBold>, it must perform the following sequence of steps:  </para>
      <list class="ordered">
        <listItem>
          <para>If the application will call <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_UPDATE, call <legacyBold>SQLBindCol</legacyBold> (or <legacyBold>SQLSetDescRec</legacyBold>) for each column to specify its data type and bind buffers for the column's data and length.</para>
        </listItem>
        <listItem>
          <para>If the application will call <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_DELETE or SQL_UPDATE, call <legacyBold>SQLColAttribute</legacyBold> to make sure that the columns to be deleted or updated are updatable.</para>
        </listItem>
        <listItem>
          <para>Call <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or a catalog function to create a result set.</para>
        </listItem>
        <listItem>
          <para>Call <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> to retrieve the data.</para>
        </listItem>
      </list>
      <para>For more information about using <legacyBold>SQLSetPos</legacyBold>, see <legacyLink xlink:href="e9625b59-06a0-4883-b155-b932ba7528d9">Updating Data with SQLSetPos</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Deleting Data Using SQLSetPos</title>
    <content>
      <para>To delete data with <legacyBold>SQLSetPos</legacyBold>, an application calls <legacyBold>SQLSetPos</legacyBold> with <legacyItalic>RowNumber</legacyItalic> set to the number of the row to delete and <legacyItalic>Operation</legacyItalic> set to SQL_DELETE.</para>
      <para>After the data has been deleted, the driver changes the value in the implementation row status array for the appropriate row to SQL_ROW_DELETED (or SQL_ROW_ERROR).</para>
    </content>
  </section>
  <section>
    <title>Updating Data Using SQLSetPos</title>
    <content>
      <para>An application can pass the value for a column either in the bound data buffer or with one or more calls to <legacyBold>SQLPutData</legacyBold>. Columns whose data is passed with <legacyBold>SQLPutData</legacyBold> are known as <legacyItalic>data-at-execution</legacyItalic> <legacyItalic>columns</legacyItalic>. These are commonly used to send data for SQL_LONGVARBINARY and SQL_LONGVARCHAR columns and can be mixed with other columns.</para>
      <procedure>
        <title>To update data with SQLSetPos, an application:</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Places values in the data and length/indicator buffers bound with <legacyBold>SQLBindCol</legacyBold>: </para>
              <list class="bullet">
                <listItem>
                  <para>For normal columns, the application places the new column value in the <legacyItalic>*TargetValuePtr</legacyItalic> buffer and the length of that value in the <legacyItalic>*StrLen_or_IndPtr</legacyItalic> buffer. If the row should not be updated, the application places SQL_ROW_IGNORE in that row's element of the row operation array.</para>
                </listItem>
                <listItem>
                  <para>For data-at-execution columns, the application places an application-defined value, such as the column number, in the <legacyItalic>*TargetValuePtr</legacyItalic> buffer. The value can be used later to identify the column. </para>
                  <para>The application places the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro in the <legacyItalic>*StrLen_or_IndPtr</legacyItalic> buffer. If the SQL data type of the column is SQL_LONGVARBINARY, SQL_LONGVARCHAR, or a long data source–specific data type and the driver returns "Y" for the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold>, <legacyItalic>length</legacyItalic> is the number of bytes of data to be sent for the parameter; otherwise, it must be a non-negative value and is ignored. </para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Calls <legacyBold>SQLSetPos</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_UPDATE to update the row of data. </para>
              <list class="bullet">
                <listItem>
                  <para>If there are no data-at-execution columns, the process is complete.</para>
                </listItem>
                <listItem>
                  <para>If there are any data-at-execution columns, the function returns SQL_NEED_DATA and proceeds to step 3.</para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Calls <legacyBold>SQLParamData</legacyBold> to retrieve the address of the <legacyItalic>*TargetValuePtr</legacyItalic> buffer for the first data-at-execution column to be processed. <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA. The application retrieves the application-defined value from the <legacyItalic>*TargetValuePtr</legacyItalic> buffer. </para>
              <alert class="note">
                <para>Although data-at-execution parameters are similar to data-at-execution columns, the value returned by <legacyBold>SQLParamData</legacyBold> is different for each.</para>
              </alert>
              <alert class="note">
                <para>Data-at-execution parameters are parameters in an SQL statement for which data will be sent with <legacyBold>SQLPutData</legacyBold> when the statement is executed with <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold>. They are bound with <legacyBold>SQLBindParameter</legacyBold> or by setting descriptors with<legacyBold> SQLSetDescRec</legacyBold>. The value returned by <legacyBold>SQLParamData</legacyBold> is a 32-bit value passed to <legacyBold>SQLBindParameter</legacyBold> in the <legacyItalic>ParameterValuePtr</legacyItalic> argument.</para>
              </alert>
              <alert class="note">
                <para>Data-at-execution columns are columns in a rowset for which data will be sent with <legacyBold>SQLPutData</legacyBold> when a row is updated with <legacyBold>SQLSetPos</legacyBold>. They are bound with <legacyBold>SQLBindCol</legacyBold>. The value returned by <legacyBold>SQLParamData</legacyBold> is the address of the row in the *<legacyItalic>TargetValuePtr</legacyItalic> buffer that is being processed.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Calls <legacyBold>SQLPutData</legacyBold> one or more times to send data for the column. More than one call is needed if all the data values cannot be returned in the <legacyItalic>*TargetValuePtr</legacyItalic> buffer specified in <legacyBold>SQLPutData</legacyBold>; multiple calls to <legacyBold>SQLPutData</legacyBold> for the same column are allowed only when sending character C data to a column with a character, binary, or data source–specific data type or when sending binary C data to a column with a character, binary, or data source–specific data type.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Calls <legacyBold>SQLParamData</legacyBold> again to signal that all data has been sent for the column. </para>
              <list class="bullet">
                <listItem>
                  <para>If there are more data-at-execution columns, <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA and the address of the <legacyItalic>TargetValuePtr</legacyItalic> buffer for the next data-at-execution column to be processed. The application repeats steps 4 and 5.</para>
                </listItem>
                <listItem>
                  <para>If there are no more data-at-execution columns, the process is complete. If the statement was executed successfully, <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO; if the execution failed, it returns SQL_ERROR. At this point, <legacyBold>SQLParamData</legacyBold> can return any SQLSTATE that can be returned by <legacyBold>SQLSetPos</legacyBold>.</para>
                </listItem>
              </list>
            </content>
          </step>
        </steps>
      </procedure>
      <para>If data has been updated, the driver changes the value in the implementation row status array for the appropriate row to SQL_ROW_UPDATED.</para>
      <para>If the operation is canceled or an error occurs in <legacyBold>SQLParamData</legacyBold> or <legacyBold>SQLPutData</legacyBold>, after <legacyBold>SQLSetPos</legacyBold> returns SQL_NEED_DATA and before data is sent for all data-at-execution columns, the application can call only <legacyBold>SQLCancel</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, <legacyBold>SQLGetDiagRec</legacyBold>, <legacyBold>SQLGetFunctions</legacyBold>, <legacyBold>SQLParamData</legacyBold>, or <legacyBold>SQLPutData</legacyBold> for the statement or the connection associated with the statement. If it calls any other function for the statement or the connection associated with the statement, the function returns SQL_ERROR and SQLSTATE HY010 (Function sequence error).</para>
      <para>If the application calls <legacyBold>SQLCancel</legacyBold> while the driver still needs data for data-at-execution columns, the driver cancels the operation. The application can then call <legacyBold>SQLSetPos</legacyBold> again; canceling does not affect the cursor state or the current cursor position.</para>
      <para>When the SELECT-list of the query specification associated with the cursor contains more than one reference to the same column, whether an error is generated or the driver ignores the duplicated references and performs the requested operations is driver-defined.</para>
    </content>
  </section>
  <section>
    <title>Performing Bulk Operations</title>
    <content>
      <para>If the <legacyItalic>RowNumber</legacyItalic> argument is 0, the driver performs the operation specified in the <legacyItalic>Operation</legacyItalic> argument for every row in the rowset that has a value of SQL_ROW_PROCEED in its field in the row operation array pointed to by SQL_ATTR_ROW_OPERATION_PTR statement attribute. This is a valid value of the <legacyItalic>RowNumber</legacyItalic> argument for an <legacyItalic>Operation</legacyItalic> argument of SQL_DELETE, SQL_REFRESH, or SQL_UPDATE, but not SQL_POSITION. <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_POSITION and a <legacyItalic>RowNumber</legacyItalic> equal to 0 will return SQLSTATE HY109 (Invalid cursor position).</para>
      <para>If an error occurs that pertains to the entire rowset, such as SQLSTATE HYT00 (Timeout expired), the driver returns SQL_ERROR and the appropriate SQLSTATE. The contents of the rowset buffers are undefined, and the cursor position is unchanged.</para>
      <para>If an error occurs that pertains to a single row, the driver:  </para>
      <list class="bullet">
        <listItem>
          <para>Sets the element for the row in the row status array pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute to SQL_ROW_ERROR.</para>
        </listItem>
        <listItem>
          <para>Posts one or more additional SQLSTATEs for the error in the error queue and sets the SQL_DIAG_ROW_NUMBER field in the diagnostic data structure.</para>
        </listItem>
      </list>
      <para>After it has processed the error or warning, if the driver completes the operation for the remaining rows in the rowset, it returns SQL_SUCCESS_WITH_INFO. Thus, for each row that returned an error, the error queue contains zero or more additional SQLSTATEs. If the driver stops the operation after it has processed the error or warning, it returns SQL_ERROR.</para>
      <para>If the driver returns any warnings, such as SQLSTATE 01004 (Data truncated), it returns warnings that apply to the entire rowset or to unknown rows in the rowset before it returns the error information that applies to specific rows. It returns warnings for specific rows along with any other error information about those rows.</para>
      <para>If <legacyItalic>RowNumber</legacyItalic> is equal to 0 and <legacyItalic>Operation</legacyItalic> is SQL_UPDATE, SQL_REFRESH, or SQL_DELETE, the number of rows that <legacyBold>SQLSetPos</legacyBold> operates on is pointed to by the SQL_ATTR_ROWS_FETCHED_PTR statement attribute.</para>
      <para>If <legacyItalic>RowNumber</legacyItalic> is equal to 0 and <legacyItalic>Operation</legacyItalic> is SQL_DELETE, SQL_REFRESH, or SQL_UPDATE, the current row after the operation is the same as the current row before the operation.</para>
    </content>
  </section>
  <section>
    <title>Ignoring a Row in a Bulk Operation</title>
    <content>
      <para>The row operation array can be used to indicate that a row in the current rowset should be ignored during a bulk operation using <legacyBold>SQLSetPos</legacyBold>. To direct the driver to ignore one or more rows during a bulk operation, an application should perform the following steps:  </para>
      <list class="ordered">
        <listItem>
          <para>Call <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_ATTR_ROW_OPERATION_PTR statement attribute to point to an array of SQLUSMALLINTs. This field can also be set by calling <legacyBold>SQLSetDescField</legacyBold> to set the SQL_DESC_ARRAY_STATUS_PTR header field of the ARD, which requires that an application obtains the descriptor handle.</para>
        </listItem>
        <listItem>
          <para>Set each element of the row operation array to one of two values: </para>
          <list class="bullet">
            <listItem>
              <para>SQL_ROW_IGNORE, to indicate that the row is excluded for the bulk operation.</para>
            </listItem>
            <listItem>
              <para>SQL_ROW_PROCEED, to indicate that the row is included in the bulk operation. (This is the default value.)</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Call <legacyBold>SQLSetPos</legacyBold> to perform the bulk operation.</para>
        </listItem>
      </list>
      <para>The following rules apply to the row operation array:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_ROW_IGNORE and SQL_ROW_PROCEED affect only bulk operations using <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_DELETE or SQL_UPDATE. They do not affect calls to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_REFRESH or SQL_POSITION.</para>
        </listItem>
        <listItem>
          <para>The pointer is set to null by default.</para>
        </listItem>
        <listItem>
          <para>If the pointer is null, all rows are updated as if all elements were set to SQL_ROW_PROCEED.</para>
        </listItem>
        <listItem>
          <para>Setting an element to SQL_ROW_PROCEED does not guarantee that the operation will occur on that particular row. For example, if a certain row in the rowset has the status SQL_ROW_ERROR, the driver might not be able to update that row regardless of whether the application specified SQL_ROW_PROCEED. An application must always check the row status array to see whether the operation was successful.</para>
        </listItem>
        <listItem>
          <para>SQL_ROW_PROCEED is defined as 0 in the header file. An application can initialize the row operation array to 0 in order to process all rows.</para>
        </listItem>
        <listItem>
          <para>If element number "n" in the row operation array is set to SQL_ROW_IGNORE and <legacyBold>SQLSetPos</legacyBold> is called to perform a bulk update or delete operation, the nth row in the rowset remains unchanged after the call to <legacyBold>SQLSetPos</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>An application should automatically set a read-only column to SQL_ROW_IGNORE.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Ignoring a Column in a Bulk Operation</title>
    <content>
      <para>To avoid unnecessary processing diagnostics generated by attempted updates to one or more read-only columns, an application can set the value in the bound length/indicator buffer to SQL_COLUMN_IGNORE. For more information, see <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application allows a user to browse the ORDERS table and update order status. The cursor is keyset-driven with a rowset size of 20 and uses optimistic concurrency control comparing row versions. After each rowset is fetched, the application prints it and allows the user to select and update the status of an order. The application uses <legacyBold>SQLSetPos</legacyBold> to position the cursor on the selected row and performs a positioned update of the row. (Error handling is omitted for clarity.)</para>
      <code>#define ROWS 20
#define STATUS_LEN 6

SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];
SQLINTEGER     cbStatus[ROWS], cbOrderID;
SQLUSMALLINT   rgfRowStatus[ROWS];
SQLUINTEGER    sOrderID, crow = ROWS, irow;
SQLHSTMT       hstmtS, hstmtU;

SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);
SQLSetCursorName(hstmtS, "C1", SQL_NTS);
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);

SQLBindCol(hstmtS, 1, SQL_C_ULONG, &amp;sOrderID, 0, &amp;cbOrderID);
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &amp;cbStatus);

while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {
   if (retcode == SQL_NO_DATA_FOUND)
      break;
   for (irow = 0; irow &lt; crow; irow++) {
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);
   }
   while (TRUE) {
      printf("\nRow number to update?");
      gets_s(szReply, 3);
      irow = atoi(szReply);
      if (irow &gt; 0 &amp;&amp; irow &lt;= crow) {
         printf("\nNew status?");
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);
         SQLPrepare(hstmtU,
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,
            SQL_C_CHAR, SQL_CHAR,
            STATUS_LEN, 0, szStatus[irow], 0, NULL);
         SQLExecute(hstmtU);
      } else if (irow == 0) {
         break;
      }
   }
}</code>
      <para>For more examples, see <legacyLink xlink:href="0eafba50-02c7-46ca-a439-ef3307b935dc">Positioned Update and Delete Statements</legacyLink> and <legacyLink xlink:href="d83a8c2a-5aa8-4f19-947c-79a817167ee1">Updating Rows in the Rowset with SQLSetPos</legacyLink>.</para>
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
              <para>Performing bulk operations that do not relate to the block cursor position</para>
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