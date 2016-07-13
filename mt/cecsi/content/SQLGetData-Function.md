---
title: SQLGetData Function
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
  - SQLGetData
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetData Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ISO 92 </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLGetData</legacyBold> retrieves data for a single column in the result set or for a single parameter after <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> returns SQL_PARAM_DATA_AVAILABLE. It can be called multiple times to retrieve variable-length data in parts.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetData</legacyBold>(
      SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
      SQLUSMALLINT   <parameterReference>Col_or_Param_Num</parameterReference>,
      SQLSMALLINT    <parameterReference>TargetType</parameterReference>,
      SQLPOINTER     <parameterReference>TargetValuePtr</parameterReference>,
      SQLLEN         <parameterReference>BufferLength</parameterReference>,
      SQLLEN *       <parameterReference>StrLen_or_IndPtr</parameterReference>);</legacySyntax>
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
          <parameterReference>Col_or_Param_Num</parameterReference>
        </definedTerm>
        <definition>
          <para>[Input] For retrieving column data, it is the number of the column for which to return data. Result set columns are numbered in increasing column order starting at 1. The bookmark column is column number 0; this can be specified only if bookmarks are enabled.</para>
          <para>For retrieving parameter data, it is the ordinal of the parameter, which starts at 1.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TargetType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type identifier of the C data type of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer. For a list of valid C data types and type identifiers, see the <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> section in Appendix D: Data Types.</para>
          <para>If <legacyItalic>TargetType</legacyItalic> is SQL_ARD_TYPE, the driver uses the type identifier specified in the SQL_DESC_CONCISE_TYPE field of the ARD. If <legacyItalic>TargetType</legacyItalic> is SQL_APD_TYPE, <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> will use the same C data type that was specified in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference>. Otherwise, the C data type specified in <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> overrides the C data type specified in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference>. If it is SQL_C_DEFAULT, the driver selects the default C data type based on the SQL data type of the source.</para>
          <para>You can also specify an extended C data type. For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TargetValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the buffer in which to return the data.</para>
          <para>
            <legacyItalic>TargetValuePtr</legacyItalic> cannot be NULL.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer in bytes.</para>
          <para>The driver uses <legacyItalic>BufferLength</legacyItalic> to avoid writing past the end of the *<legacyItalic>TargetValuePtr</legacyItalic> buffer when returning variable-length data, such as character or binary data. Note that the driver counts the null-termination character when returning character data to *<legacyItalic>TargetValuePtr</legacyItalic>. *<legacyItalic>TargetValuePtr</legacyItalic> must therefore contain space for the null-termination character, or the driver will truncate the data.</para>
          <para>When the driver returns fixed-length data, such as an integer or a date structure, the driver ignores <legacyItalic>BufferLength</legacyItalic> and assumes the buffer is large enough to hold the data. It is therefore important for the application to allocate a large enough buffer for fixed-length data or the driver will write past the end of the buffer.</para>
          <para>
            <legacyBold>SQLGetData</legacyBold> returns SQLSTATE HY090 (Invalid string or buffer length) when <legacyItalic>BufferLength</legacyItalic> is less than 0 but not when <legacyItalic>BufferLength</legacyItalic> is 0.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StrLen_or_IndPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the buffer in which to return the length or indicator value. If this is a null pointer, no length or indicator value is returned. This returns an error when the data being fetched is NULL.</para>
          <para>
            <legacyBold>SQLGetData</legacyBold> can return the following values in the length/indicator buffer: </para>
          <list class="bullet">
            <listItem>
              <para>The length of the data available to return</para>
            </listItem>
            <listItem>
              <para>SQL_NO_TOTAL</para>
            </listItem>
            <listItem>
              <para>SQL_NULL_DATA </para>
            </listItem>
          </list>
          <para>For more information, see <legacyLink xlink:href="849792f1-cb1e-4bc2-b568-c0aff0b66199">Using Length/Indicator Values</legacyLink> and "Comments" in this topic.</para>
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
      <para>When <legacyBold>SQLGetData</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetData</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>Not all of the data for the specified column, <legacyItalic>Col_or_Param_Num</legacyItalic>, could be retrieved in a single call to the function. SQL_NO_TOTAL or the length of the data remaining in the specified column prior to the current call to <legacyBold>SQLGetData</legacyBold> is returned in *<legacyItalic>StrLen_or_IndPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
              <para>For more information on using multiple calls to <legacyBold>SQLGetData</legacyBold> for a single column, see "Comments."</para>
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
              <para>The data returned for one or more columns was truncated. For numeric data types, the fractional part of the number was truncated. For time, timestamp, and interval data types containing a time component, the fractional portion of the time was truncated. </para>
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
              <para>The data value of a column in the result set cannot be converted to the C data type specified by the argument <legacyItalic>TargetType</legacyItalic>.</para>
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
              <para>The value specified for the argument <legacyItalic>Col_or_Param_Num</legacyItalic> was 0, and the SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_OFF.</para>
              <para>The value specified for the argument <legacyItalic>Col_or_Param_Num</legacyItalic> was greater than the number of columns in the result set. </para>
              <para>The <parameterReference>Col_or_Param_Num</parameterReference> value was not equal to the ordinal of the parameter that is available.</para>
              <para>(DM) The specified column was bound. This description does not apply to drivers that return the SQL_GD_BOUND bitmask for the SQL_GETDATA_EXTENSIONS option in <legacyBold>SQLGetInfo</legacyBold>.</para>
              <para>(DM) The number of the specified column was less than or equal to the number of the highest bound column. This description does not apply to drivers that return the SQL_GD_ANY_COLUMN bitmask for the SQL_GETDATA_EXTENSIONS option in <legacyBold>SQLGetInfo</legacyBold>.</para>
              <para>(DM) The application has already called <legacyBold>SQLGetData</legacyBold> for the current row; the number of the column specified in the current call was less than the number of the column specified in the preceding call; and the driver does not return the SQL_GD_ANY_ORDER bitmask for the SQL_GETDATA_EXTENSIONS option in <legacyBold>SQLGetInfo</legacyBold>.</para>
              <para>(DM) The <legacyItalic>TargetType</legacyItalic> argument was SQL_ARD_TYPE, and the <legacyItalic>Col_or_Param_Num</legacyItalic> descriptor record in the ARD failed the consistency check. </para>
              <para>(DM) The <legacyItalic>TargetType</legacyItalic> argument was SQL_ARD_TYPE, and the value in the SQL_DESC_COUNT field of the ARD was less than the <legacyItalic>Col_or_Param_Num</legacyItalic> argument.</para>
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
              <para>
                <legacyItalic>StrLen_or_IndPtr</legacyItalic> was a null pointer and NULL data was retrieved.</para>
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
              <para>Returning the numeric value (as numeric or string) for the column would have caused the whole (as opposed to fractional) part of the number to be truncated.</para>
              <para>For more information, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.</para>
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
              <para>The character column in the result set was bound to a C date, time, or timestamp structure, and the value in the column was an invalid date, time, or timestamp, respectively. For more information, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.</para>
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
              <para>A value from an arithmetic expression that resulted in division by zero was returned.</para>
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
              <para>When returning data to an interval C type, there was no representation of the value of the SQL type in the interval C type.</para>
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
              <para>A character column in the result set was returned to a character C buffer, and the column contained a character for which there was no representation in the character set of the buffer.</para>
              <para>The C type was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type.</para>
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
              <para>(DM) The function was called without first calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> to position the cursor on the row of data required. </para>
              <para>(DM) The <legacyItalic>StatementHandle</legacyItalic> was in an executed state, but no result set was associated with the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic> and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called, but the cursor was positioned before the start of the result set or after the end of the result set.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>MessageText</legacyItalic> buffer describes the error and its cause.</para>
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
              <para>HY003</para>
            </TD>
            <TD>
              <para>Program type out of range</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>TargetType</legacyItalic> was not a valid data type, SQL_C_DEFAULT, SQL_ARD_TYPE (in case of retrieving column data), or SQL_APD_TYPE (in case of retrieving parameter data).</para>
              <para>(DM) The argument <legacyItalic>Col_or_Param_Num</legacyItalic> was 0, and the argument <legacyItalic>TargetType</legacyItalic> was not SQL_C_BOOKMARK for a fixed-length bookmark or SQL_C_VARBOOKMARK for a variable-length bookmark.</para>
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
              <para>The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application, and then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid use of null pointer</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>TargetValuePtr</legacyItalic> was a null pointer.</para>
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
              <para> (DM) The specified <legacyItalic>StatementHandle</legacyItalic> was not in an executed state. The function was called without first calling <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold> or a catalog function.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> function was called.</para>
              <para> (DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) The <legacyItalic>StatementHandle</legacyItalic> was in an executed state, but no result set was associated with the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>A call to <unmanagedCodeEntityReference>SQLExeceute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> returned SQL_PARAM_DATA_AVAILABLE, but <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> was called, instead of <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference>.</para>
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
              <para>(DM) The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
              <para>The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 4, the <legacyItalic>Col_or_Param_Num</legacyItalic> argument was set to 0, and the driver was an ODBC 2<legacyItalic>.x</legacyItalic> driver.</para>
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
              <para>The cursor was positioned (by <legacyBold>SQLSetPos</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLBulkOperations</legacyBold>) on a row that had been deleted or could not be fetched.</para>
              <para>The cursor was a forward-only cursor, and the rowset size was greater than one.</para>
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
              <para>The driver or data source does not support use of <legacyBold>SQLGetData</legacyBold> with multiple rows in <legacyBold>SQLFetchScroll</legacyBold>. This description does not apply to drivers that return the SQL_GD_BLOCK bitmask for the SQL_GETDATA_EXTENSIONS option in <legacyBold>SQLGetInfo</legacyBold>.</para>
              <para>The driver or data source does not support the conversion specified by the combination of the <legacyItalic>TargetType</legacyItalic> argument and the SQL data type of the corresponding column. This error applies only when the SQL data type of the column was mapped to a driver-specific SQL data type.</para>
              <para>The driver supports only ODBC 2<legacyItalic>.x</legacyItalic>, and the argument <legacyItalic>TargetType</legacyItalic> was one of the following: </para>
              <para>SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT</para>
              <para>and any of the interval C data types listed in <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink> in Appendix D: Data Types.</para>
              <para>The driver only supports ODBC versions prior to 3.50, and the argument <legacyItalic>TargetType</legacyItalic> was SQL_C_GUID.</para>
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
              <para>(DM) The driver corresponding to the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
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
        <legacyBold>SQLGetData</legacyBold> returns the data in a specified column. <legacyBold>SQLGetData</legacyBold> can be called only after one or more rows have been fetched from the result set by <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLExtendedFetch</legacyBold>. If variable-length data is too large to be returned in a single call to <legacyBold>SQLGetData</legacyBold> (due to a limitation in the application), <legacyBold>SQLGetData</legacyBold> can retrieve it in parts. It is possible to bind some columns in a row and call <legacyBold>SQLGetData</legacyBold> for others, although this is subject to some restrictions. For more information, see <legacyLink xlink:href="6ccb44bc-8695-4bad-91af-363ef22bdb85">Getting Long Data</legacyLink>.</para>
      <para>For information about using <legacyBold>SQLGetData</legacyBold> with streamed output parameters, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
    </content>
  </section>
  <section>
    <title>Using SQLGetData</title>
    <content>
      <para>If the driver does not support extensions to <legacyBold>SQLGetData</legacyBold>, the function can return data only for unbound columns with a number greater than that of the last bound column. Furthermore, within a row of data, the value of the <legacyItalic>Col_or_Param_Num</legacyItalic> argument in each call to <legacyBold>SQLGetData</legacyBold> must be greater than or equal to the value of <legacyItalic>Col_or_Param_Num</legacyItalic> in the previous call; that is, data must be retrieved in increasing column number order. Finally, if no extensions are supported, <legacyBold>SQLGetData</legacyBold> cannot be called if the rowset size is greater than 1.</para>
      <para>Drivers can relax any of these restrictions. To determine what restrictions a driver relaxes, an application calls <legacyBold>SQLGetInfo</legacyBold> with any of the following SQL_GETDATA_EXTENSIONS options:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_GD_OUTPUT_PARAMS = <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> can be called to return output parameter values. For more information, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
        </listItem>
        <listItem>
          <para>SQL_GD_ANY_COLUMN. If this option is returned, <legacyBold>SQLGetData</legacyBold> can be called for any unbound column, including those before the last bound column.</para>
        </listItem>
        <listItem>
          <para>SQL_GD_ANY_ORDER. If this option is returned, <legacyBold>SQLGetData</legacyBold> can be called for unbound columns in any order.</para>
        </listItem>
        <listItem>
          <para>SQL_GD_BLOCK. If this option is returned by <legacyBold>SQLGetInfo</legacyBold> for the SQL_GETDATA_EXTENSIONS InfoType, the driver supports calls to <legacyBold>SQLGetData</legacyBold> when the rowset size is greater than 1 and the application can call <legacyBold>SQLSetPos</legacyBold> with the SQL_POSITION option to position the cursor on the correct row before calling <legacyBold>SQLGetData.</legacyBold></para>
        </listItem>
        <listItem>
          <para>SQL_GD_BOUND. If this option is returned, <legacyBold>SQLGetData</legacyBold> can be called for bound columns as well as unbound columns.</para>
        </listItem>
      </list>
      <para>There are two exceptions to these restrictions and a driver's ability to relax them. First, <legacyBold>SQLGetData</legacyBold> should never be called for a forward-only cursor when the rowset size is greater than 1. Second, if a driver supports bookmarks, it must always support the ability to call <legacyBold>SQLGetData</legacyBold> for column 0, even if it does not allow applications to call <legacyBold>SQLGetData</legacyBold> for other columns before the last bound column. (When an application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, <legacyBold>SQLGetData</legacyBold> will successfully return a bookmark when called with <legacyItalic>Col_or_Param_Num</legacyItalic> equal to 0 after a call to <legacyBold>SQLFetch</legacyBold>, because <legacyBold>SQLFetch</legacyBold> is mapped by the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager to <legacyBold>SQLExtendedFetch</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_NEXT, and <legacyBold>SQLGetData</legacyBold> with a <legacyItalic>Col_or_Param_Num</legacyItalic> of 0 is mapped by the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager to <legacyBold>SQLGetStmtOption</legacyBold> with an <legacyItalic>fOption</legacyItalic> of SQL_GET_BOOKMARK.)</para>
      <para>
        <legacyBold>SQLGetData</legacyBold> cannot be used to retrieve the bookmark for a row just inserted by calling <legacyBold>SQLBulkOperations</legacyBold> with the SQL_ADD option, because the cursor is not positioned on the row. An application can retrieve the bookmark for such a row by binding column 0 before calling <legacyBold>SQLBulkOperations</legacyBold> with SQL_ADD, in which case <legacyBold>SQLBulkOperations</legacyBold> returns the bookmark in the bound buffer. <legacyBold>SQLFetchScroll</legacyBold> can then be called with SQL_FETCH_BOOKMARK to reposition the cursor on that row.</para>
      <para>If the <legacyItalic>TargetType</legacyItalic> argument is an interval data type, the default interval leading precision (2) and the default interval seconds precision (6), as set in the SQL_DESC_DATETIME_INTERVAL_PRECISION and SQL_DESC_PRECISION fields of the ARD, respectively, are used for the data. If the <legacyItalic>TargetType</legacyItalic> argument is an SQL_C_NUMERIC data type, the default precision (driver-defined) and default scale (0), as set in the SQL_DESC_PRECISION and SQL_DESC_SCALE fields of the ARD, are used for the data. If any default precision or scale is not appropriate, the application should explicitly set the appropriate descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>. It can set the SQL_DESC_CONCISE_TYPE field to SQL_C_NUMERIC and call <legacyBold>SQLGetData</legacyBold> with a <legacyItalic>TargetType</legacyItalic> argument of SQL_ARD_TYPE, which will cause the precision and scale values in the descriptor fields to be used.</para>
      <alert class="note">
        <para>In ODBC 2<legacyItalic>.x</legacyItalic>, applications set <legacyItalic>TargetType</legacyItalic> to SQL_C_DATE, SQL_C_TIME, or SQL_C_TIMESTAMP to indicate that *<legacyItalic>TargetValuePtr</legacyItalic> is a date, time, or timestamp structure. In ODBC 3<legacyItalic>.x</legacyItalic>, applications set <legacyItalic>TargetType</legacyItalic> to SQL_C_TYPE_DATE, SQL_C_TYPE_TIME, or SQL_C_TYPE_TIMESTAMP. The Driver Manager makes appropriate mappings if necessary, based on the application and driver version.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Retrieving Variable-Length Data in Parts</title>
    <content>
      <para>
        <legacyBold>SQLGetData</legacyBold> can be used to retrieve data from a column that contains variable-length data in parts — that is, when the identifier of the SQL data type of the column is SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_WCHAR, SQL_WVARCHAR, SQL_WLONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY, or a driver-specific identifier for a variable-length type.</para>
      <para>To retrieve data from a column in parts, the application calls <legacyBold>SQLGetData</legacyBold> multiple times in succession for the same column. On each call, <legacyBold>SQLGetData</legacyBold> returns the next part of the data. It is up to the application to reassemble the parts, taking care to remove the null-termination character from intermediate parts of character data. If there is more data to return or not enough buffer was allocated for the terminating character, <legacyBold>SQLGetData</legacyBold> returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01004 (Data truncated). When it returns the last part of the data, <legacyBold>SQLGetData</legacyBold> returns SQL_SUCCESS. Neither SQL_NO_TOTAL nor zero can be returned on the last valid call to retrieve data from a column, because the application would then have no way of knowing how much of the data in the application buffer is valid. If <legacyBold>SQLGetData</legacyBold> is called after this, it returns SQL_NO_DATA. For more information, see the next section, "Retrieving Data with SQLGetData."</para>
      <para>Variable-length bookmarks can be returned in parts by <legacyBold>SQLGetData</legacyBold>. As with other data, a call to <legacyBold>SQLGetData</legacyBold> to return variable-length bookmarks in parts will return SQLSTATE 01004 (String data, right truncated) and SQL_SUCCESS_WITH_INFO when there is more data to be returned. This is different than the case when a variable-length bookmark is truncated by a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, which returns SQL_ERROR and SQLSTATE 22001 (String data, right truncated).</para>
      <para>
        <legacyBold>SQLGetData</legacyBold> cannot be used to return fixed-length data in parts. If <legacyBold>SQLGetData</legacyBold> is called more than one time in a row for a column containing fixed-length data, it returns SQL_NO_DATA for all calls after the first.</para>
    </content>
  </section>
  <section>
    <title>Retrieving Streamed Output Parameters</title>
    <content>
      <para>If a driver supports streamed output parameters, an application can call <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> with a small buffer many times to retrieve a large parameter value. For more information about streamed output parameter, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
    </content>
  </section>
  <section>
    <title>Retrieving Data with SQLGetData</title>
    <content>
      <para>To return data for the specified column, <legacyBold>SQLGetData</legacyBold> performs the following sequence of steps:</para>
      <list class="ordered">
        <listItem>
          <para>Returns SQL_NO_DATA if it has already returned all of the data for the column.</para>
        </listItem>
        <listItem>
          <para>Sets *<legacyItalic>StrLen_or_IndPtr</legacyItalic> to SQL_NULL_DATA if the data is NULL. If the data is NULL and <legacyItalic>StrLen_or_IndPtr</legacyItalic> was a null pointer, <legacyBold>SQLGetData</legacyBold> returns SQLSTATE 22002 (Indicator variable required but not supplied).</para>
          <para>If the data for the column is not NULL, <legacyBold>SQLGetData</legacyBold> proceeds to step 3.</para>
        </listItem>
        <listItem>
          <para>If the SQL_ATTR_MAX_LENGTH statement attribute is set to a nonzero value, if the column contains character or binary data, and if <legacyBold>SQLGetData</legacyBold> has not previously been called for the column, the data is truncated to SQL_ATTR_MAX_LENGTH bytes.</para>
          <alert class="note">
            <para>The SQL_ATTR_MAX_LENGTH statement attribute is intended to reduce network traffic. It is generally implemented by the data source, which truncates the data before returning it across the network. Drivers and data sources are not required to support it. Therefore, to guarantee that data is truncated to a particular size, an application should allocate a buffer of that size and specify the size in the <legacyItalic>BufferLength</legacyItalic> argument.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Converts the data to the type specified in <legacyItalic>TargetType</legacyItalic>. The data is given the default precision and scale for that data type. If <legacyItalic>TargetType</legacyItalic> is SQL_ARD_TYPE, the data type in the SQL_DESC_CONCISE_TYPE field of the ARD is used. If <legacyItalic>TargetType</legacyItalic> is SQL_ARD_TYPE, the data is given the precision and scale in the SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, and SQL_DESC_SCALE fields of the ARD, depending on the data type in the SQL_DESC_CONCISE_TYPE field. If any default precision or scale is not appropriate, the application should explicitly set the appropriate descriptor field by a call to <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>If the data was converted to a variable-length data type, such as character or binary, <legacyBold>SQLGetData</legacyBold> checks whether the length of the data exceeds <legacyItalic>BufferLength</legacyItalic>. If the length of character data (including the null-termination character) exceeds <legacyItalic>BufferLength</legacyItalic>, <legacyBold>SQLGetData</legacyBold> truncates the data to <legacyItalic>BufferLength</legacyItalic> less the length of a null-termination character. It then null-terminates the data. If the length of binary data exceeds the length of the data buffer, <legacyBold>SQLGetData</legacyBold> truncates it to <legacyItalic>BufferLength</legacyItalic> bytes. </para>
          <para>If the data buffer supplied is too small to hold the null-termination character, <legacyBold>SQLGetData</legacyBold> returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01004.  </para>
          <para>
            <legacyBold>SQLGetData</legacyBold> never truncates data converted to fixed-length data types; it always assumes that the length of *<legacyItalic>TargetValuePtr</legacyItalic> is the size of the data type. </para>
        </listItem>
        <listItem>
          <para>Places the converted (and possibly truncated) data in *<legacyItalic>TargetValuePtr</legacyItalic>. Note that <legacyBold>SQLGetData</legacyBold> cannot return data out of line.</para>
        </listItem>
        <listItem>
          <para>Places the length of the data in *<legacyItalic>StrLen_or_IndPtr</legacyItalic>. If <legacyItalic>StrLen_or_IndPtr</legacyItalic> was a null pointer, <legacyBold>SQLGetData</legacyBold> does not return the length.</para>
          <list class="bullet">
            <listItem>
              <para>For character or binary data, this is the length of the data after conversion and before truncation due to <legacyItalic>BufferLength</legacyItalic>. If the driver cannot determine the length of the data after conversion, as is sometimes the case with long data, it returns SQL_SUCCESS_WITH_INFO and sets the length to SQL_NO_TOTAL. (The last call to <legacyBold>SQLGetData</legacyBold> must always return the length of the data, not zero or SQL_NO_TOTAL.) If data was truncated due to the SQL_ATTR_MAX_LENGTH statement attribute, the value of this attribute — as opposed to the actual length — is placed in *<legacyItalic>StrLen_or_IndPtr</legacyItalic>. This is because this attribute is designed to truncate data on the server before conversion, so the driver has no way of figuring out what the actual length is. When <legacyBold>SQLGetData</legacyBold> is called multiple times in succession for the same column, this is the length of the data available at the start of the current call; that is, the length decreases with each subsequent call.</para>
            </listItem>
            <listItem>
              <para>For all other data types, this is the length of the data after conversion; that is, it is the size of the type to which the data was converted.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>If the data is truncated without loss of significance during conversion (for example, the real number 1.234 is truncated when converted to the integer 1) or because <legacyItalic>BufferLength</legacyItalic> is too small (for example, the string "abcdef" is placed in a 4-byte buffer), <legacyBold>SQLGetData</legacyBold> returns SQLSTATE 01004 (Data truncated) and SQL_SUCCESS_WITH_INFO. If data is truncated without loss of significance due to the SQL_ATTR_MAX_LENGTH statement attribute, <legacyBold>SQLGetData</legacyBold> returns SQL_SUCCESS and does not return SQLSTATE 01004 (Data truncated).</para>
        </listItem>
      </list>
      <para>The contents of the bound data buffer (if <legacyBold>SQLGetData</legacyBold> is called on a bound column) and the length/indicator buffer are undefined if <legacyBold>SQLGetData</legacyBold> does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO.</para>
      <para>Successive calls to <legacyBold>SQLGetData</legacyBold> will retrieve data from the last column requested; prior offsets become invalid. For example, when the following sequence is performed:</para>
      <code>SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)</code>
      <para>the second call to SQLGetData(icol=n) retrieves data from the start of the n column. Any offset in the data due to earlier calls to <legacyBold>SQLGetData</legacyBold> for the column is no longer valid.</para>
    </content>
  </section>
  <section>
    <title>Descriptors and SQLGetData</title>
    <content>
      <para>
        <legacyBold>SQLGetData</legacyBold> does not interact directly with any descriptor fields.</para>
      <para>If <legacyItalic>TargetType</legacyItalic> is SQL_ARD_TYPE, the data type in the SQL_DESC_CONCISE_TYPE field of the ARD is used. If <legacyItalic>TargetType</legacyItalic> is either SQL_ARD_TYPE or SQL_C_DEFAULT, the data is given the precision and scale in the SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_PRECISION, and SQL_DESC_SCALE fields of the ARD, depending on the data type in the SQL_DESC_CONCISE_TYPE field.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application executes a <legacyBold>SELECT</legacyBold> statement to return a result set of the customer IDs, names, and phone numbers sorted by name, ID, and phone number. For each row of data, it calls <legacyBold>SQLFetch</legacyBold> to position the cursor to the next row. It calls <legacyBold>SQLGetData</legacyBold> to retrieve the fetched data; the buffers for the data and the returned number of bytes are specified in the call to <legacyBold>SQLGetData</legacyBold>. Finally, it prints each employee's name, ID, and phone number.</para>
      <code>#define NAME_LEN 50
#define PHONE_LEN 50

SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;
SQLRETURN    retcode;
SQLHSTMT     hstmt;

retcode = SQLExecDirect(hstmt,
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",
   SQL_NTS);

if (retcode == SQL_SUCCESS) {
   while (TRUE) {
      retcode = SQLFetch(hstmt);
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {
         show_error();
      }
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){

         /* Get data for columns 1, 2, and 3 */

         SQLGetData(hstmt, 1, SQL_C_ULONG, &amp;sCustID, 0, &amp;cbCustID);
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &amp;cbName);
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,
            &amp;cbPhone);

         /* Print the row of data */

         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName, 
            PHONE_LEN-1, szPhone);
      } else {
         break;
      }
   }
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
              <para>Assigning storage for a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Performing bulk operations that do not relate to the block cursor position</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a block of data or scrolling through a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a single row of data or a block of data in a forward-only direction</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Sending parameter data at execution time</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Positioning the cursor, refreshing data in the rowset, or updating or deleting data in the rowset</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>
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
<link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>