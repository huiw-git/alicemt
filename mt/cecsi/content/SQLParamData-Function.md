---
title: SQLParamData Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLParamData
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
translation.priority.ht: 
  - en-gb
---
# SQLParamData Function
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
          <legacyBold>SQLParamData</legacyBold> is used together with <legacyBold>SQLPutData</legacyBold> to supply parameter data at statement execution time, and with <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve streamed output parameter data.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLParamData</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLPOINTER *   <parameterReference>ValuePtrPtr</parameterReference>);</legacySyntax>
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
          <legacyItalic>ValuePtrPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the address of the <legacyItalic>ParameterValuePtr</legacyItalic> buffer specified in <legacyBold>SQLBindParameter</legacyBold> (for parameter data) or the address of the <legacyItalic>TargetValuePtr</legacyItalic> buffer specified in <legacyBold>SQLBindCol</legacyBold> (for column data), as contained in the SQL_DESC_DATA_PTR descriptor record field.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_PARAM_DATA_AVAILABLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLParamData</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLParamData </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>07006</para>
            </TD>
            <TD>
              <para>Restricted data type attribute violation</para>
            </TD>
            <TD>
              <para>The data value identified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> for the bound parameter could not be converted to the data type identified by the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>The data value returned for a parameter bound as SQL_PARAM_INPUT_OUTPUT or SQL_PARAM_OUTPUT could not be converted to the data type identified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>(If the data values for one or more rows could not be converted, but one or more rows were successfully returned, this function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>22026</para>
            </TD>
            <TD>
              <para>String data, length mismatch</para>
            </TD>
            <TD>
              <para>The SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y", and less data was sent for a long parameter (the data type was SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type) than was specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>The SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y", and less data was sent for a long column (the data type was SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type) than was specified in the length buffer corresponding to a column in a row of data that was added or updated with <legacyBold>SQLBulkOperations</legacyBold> or updated with <legacyBold>SQLSetPos</legacyBold>.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>; the function was then called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
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
              <para> (DM) The previous function call was not a call to <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> where the return code was SQL_NEED_DATA, or the previous function call was a call to <legacyBold>SQLPutData</legacyBold>.</para>
              <para>The previous function call was a call to <legacyBold>SQLParamData</legacyBold>.</para>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called. </para>
              <para>
                <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. <legacyBold>SQLCancel</legacyBold> was called before data was sent for all data-at-execution parameters or columns.</para>
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
              <para>(DM) The driver that corresponds to the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
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
      <para>If <legacyBold>SQLParamData</legacyBold> is called while sending data for a parameter in an SQL statement, it can return any SQLSTATE that can be returned by the function called to execute the statement (<legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>). If it is called while sending data for a column being updated or added with <legacyBold>SQLBulkOperations</legacyBold> or being updated with <legacyBold>SQLSetPos</legacyBold>, it can return any SQLSTATE that can be returned by <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLParamData</legacyBold> can be called to supply data-at-execution data for two uses: parameter data that will be used in a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>, or column data that will be used when a row is updated or added by a call to <legacyBold>SQLBulkOperations</legacyBold> or updated by a call to <legacyBold>SQLSetPos</legacyBold>. At execution time, <legacyBold>SQLParamData</legacyBold> returns to the application an indicator of which data the driver requires.</para>
      <para>When an application calls <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>, the driver returns SQL_NEED_DATA if it needs data-at-execution data. An application then calls <legacyBold>SQLParamData</legacyBold> to determine which data to send. If the driver requires parameter data, the driver returns in the <legacyItalic>*ValuePtrPtr</legacyItalic> output buffer the value that the application put in the rowset buffer. The application can use this value to determine which parameter data the driver is requesting. If the driver requires column data, the driver returns in the <legacyItalic>*ValuePtrPtr</legacyItalic> buffer the address that the column was originally bound to, as follows: </para>
      <para>
        <legacyItalic>Bound Address</legacyItalic> + <legacyItalic>Binding Offset</legacyItalic> + ((<legacyItalic>Row Number</legacyItalic> – 1) x <legacyItalic>Element Size</legacyItalic>)</para>
      <para>where the variables are defined as indicated in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyItalic>Bound Address</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The address specified with the <legacyItalic>TargetValuePtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Binding Offset</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The value stored at the address specified with the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Row Number</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The 1-based number of the row in the rowset. For single-row fetches, which are the default, this is 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Element Size</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>The value of the SQL_ATTR_ROW_BIND_TYPE statement attribute for both data and length/indicator buffers.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>It also returns SQL_NEED_DATA, which is an indicator to the application that it should call <legacyBold>SQLPutData</legacyBold> to send the data.</para>
      <para>The application calls <legacyBold>SQLPutData</legacyBold> as many times as necessary to send the data-at-execution data for the column or parameter. After all the data has been sent for the column or parameter, the application calls <legacyBold>SQLParamData</legacyBold> again. If <legacyBold>SQLParamData</legacyBold> again returns SQL_NEED_DATA, data must be sent for another parameter or column. Therefore, the application again calls <legacyBold>SQLPutData</legacyBold>. If all data-at-execution data has been sent for all parameters or columns, then <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the value in <legacyItalic>*ValuePtrPtr</legacyItalic> is undefined, and the SQL statement can be executed or the <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> call can be processed.</para>
      <para>If <legacyBold>SQLParamData</legacyBold> supplies parameter data for a searched update or delete statement that does not affect any rows at the data source, the call to <legacyBold>SQLParamData</legacyBold> returns SQL_NO_DATA.</para>
      <para>For more information about how data-at-execution parameter data is passed at statement execution time, see "Passing Parameter Values" in <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink> and <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>. For more information about how data-at-execution column data is updated or added, see the section "Using SQLSetPos" in <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>, "Performing Bulk Updates Using Bookmarks" in <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>, and <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>.</para>
      <para>
        <legacyBold>SQLParamData</legacyBold> can be called to retrieve streamed output parameters. When <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference> returns SQL_PARAM_DATA_AVAILABLE, call <legacyBold>SQLParamData</legacyBold> to determine which parameter has a value available. For more information about SQL_PARAM_DATA_AVAILABLE and streamed output parameters, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>.</para>
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
              <para>Binding a buffer to a parameter</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a parameter in a statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1f5b63c4-2f3e-44da-b155-876405302281">SQLDescribeParam Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing an SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Sending parameter data at execution time</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink> </para>
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