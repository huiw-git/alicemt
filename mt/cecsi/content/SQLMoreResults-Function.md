---
title: SQLMoreResults Function
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
  - SQLMoreResults
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLMoreResults Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLMoreResults</legacyBold> determines whether more results are available on a statement containing <legacyBold>SELECT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>DELETE</legacyBold> statements and, if so, initializes processing for those results.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLMoreResults</legacyBold>(
     SQLHSTMT     <parameterReference>StatementHandle</parameterReference>);</legacySyntax>
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
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE, OR SQL_PARAM_DATA_AVAILABLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLMoreResults</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLMoreResults </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>01S02</para>
            </TD>
            <TD>
              <para>Option value has changed</para>
            </TD>
            <TD>
              <para>The value of a statement attribute changed as the batch was being processed. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The associated connection failed during the execution of this function and the state of the transaction cannot be determined.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> function was called and, before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> function was called and, before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> function was called.</para>
              <para> (DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
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
        <legacyBold>SELECT</legacyBold> statements return result sets. <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, and <legacyBold>DELETE</legacyBold> statements return a count of affected rows. If any of these statements are batched, submitted with arrays of parameters (numbered in increasing parameter order, in the order that they appear in the batch), or in procedures, they can return multiple result sets or row counts. For information about batches of statements and arrays of parameters, see <legacyLink xlink:href="766488cc-450c-434c-9c88-467f6c57e17c">Batches of SQL Statements</legacyLink> and <legacyLink xlink:href="9b572c5b-1dfe-40af-bebd-051548ab6d90">Arrays of Parameter Values</legacyLink>.</para>
      <para>After executing the batch, the application is positioned on the first result set. The application can call <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLGetData</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLSetPos</legacyBold>, and all the metadata functions, on the first or any subsequent result sets, just as it would if there were just a single result set. Once it is done with the first result set, the application calls <legacyBold>SQLMoreResults</legacyBold> to move to the next result set. If another result set or count is available, <legacyBold>SQLMoreResults</legacyBold> returns SQL_SUCCESS and initializes the result set or count for additional processing. If any row count–generating statements appear in between result set–generating statements, they can be stepped over by calling <legacyBold>SQLMoreResults</legacyBold>.After calling <legacyBold>SQLMoreResults</legacyBold> for <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>DELETE</legacyBold> statements, an application can call <legacyBold>SQLRowCount</legacyBold>. </para>
      <para>If there was a current result set with unfetched rows, <legacyBold>SQLMoreResults</legacyBold> discards that result set and makes the next result set or count available. If all results have been processed, <legacyBold>SQLMoreResults</legacyBold> returns SQL_NO_DATA. For some drivers, output parameters and return values are not available until all result sets and row counts have been processed. For such drivers, output parameters and return values become available when <legacyBold>SQLMoreResults</legacyBold> returns SQL_NO_DATA.</para>
      <para>Any bindings that were established for the previous result set still remain valid. If the column structures are different for this result set, then calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> may result in an error or truncation. To prevent this, the application has to call <legacyBold>SQLBindCol</legacyBold> to explicitly rebind as appropriate (or do so by setting descriptor fields). Alternatively, the application can call <legacyBold>SQLFreeStmt </legacyBold>with an <legacyItalic>Option</legacyItalic> of SQL_UNBIND to unbind all the column buffers.</para>
      <para>The values of statement attributes, such as cursor type, cursor concurrency, keyset size, or maximum length, may change as the application navigates through the batch by calls to <legacyBold>SQLMoreResults</legacyBold>. If this happens, <legacyBold>SQLMoreResults</legacyBold> will return SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value has changed).</para>
      <para>Calling <legacyBold>SQLCloseCursor</legacyBold>, or <legacyBold>SQLFreeStmt</legacyBold> with an <legacyItalic>Option</legacyItalic> of SQL_CLOSE, discards all the result sets and row counts that were available as a result of the execution of the batch. The statement handle returns to either the allocated or prepared state. Calling <legacyBold>SQLCancel</legacyBold> to cancel an asynchronously executing function when a batch has been executed and the statement handle is in the executed, cursor-positioned, or asynchronous state results in all the results sets and row counts generated by the batch being discarded if the cancel call was successful. The statement then returns to the prepared or allocated state. </para>
      <para>If a batch of statements or a procedure mixes other SQL statements with <legacyBold>SELECT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, and <legacyBold>DELETE</legacyBold> statements, these other statements do not affect <legacyBold>SQLMoreResults</legacyBold>.</para>
      <para>For more information, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
      <para>If a searched update, insert, or delete statement in a batch of statements does not affect any rows at the data source, <legacyBold>SQLMoreResults</legacyBold> returns SQL_SUCCESS. This is different from the case of a searched update, insert, or delete statement that is executed through <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold>, which returns SQL_NO_DATA if it does not affect any rows at the data source. If an application calls <legacyBold>SQLRowCount</legacyBold> to retrieve the row count after a call to <legacyBold>SQLMoreResults</legacyBold> has not affected any rows, <legacyBold>SQLRowCount</legacyBold> will return SQL_NO_DATA.</para>
      <para>For additional information about the valid sequencing of result-processing functions, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
      <para>For more information about SQL_PARAM_DATA_AVAILABLE and streamed output parameters, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
    </content>
  </section>
  <section>
    <title>Availability of Row Counts</title>
    <content>
      <para>When a batch contains multiple consecutive row count–generating statements, it is possible that these row counts are rolled up into just one row count. For example, if a batch has five insert statements, then certain data sources are capable of returning five individual row counts. Certain other data sources return only one row count that represents the sum of the five individual row counts.</para>
      <para>When a batch contains a combination of result set–generating and row count–generating statements, row counts may or may not be available at all. The behavior of the driver with respect to the availability of row counts is enumerated in the SQL_BATCH_ROW_COUNT information type available through a call to <legacyBold>SQLGetInfo</legacyBold>. For example, suppose that the batch contains a <legacyBold>SELECT</legacyBold>, followed by two <legacyBold>INSERT</legacyBold>s and another <legacyBold>SELECT</legacyBold>. Then the following cases are possible:  </para>
      <list class="bullet">
        <listItem>
          <para>The row counts corresponding to the two <legacyBold>INSERT</legacyBold> statements are not available at all. The first call to <legacyBold>SQLMoreResults</legacyBold> will position you on the result set of the second <legacyBold>SELECT</legacyBold> statement.</para>
        </listItem>
        <listItem>
          <para>The row counts corresponding to the two <legacyBold>INSERT</legacyBold> statements are available individually. (A call to <legacyBold>SQLGetInfo</legacyBold> does not return the SQL_BRC_ROLLED_UP bit for the SQL_BATCH_ROW_COUNT information type.) The first call to <legacyBold>SQLMoreResults</legacyBold> will position you on the row count of the first <legacyBold>INSERT</legacyBold>, and the second call will position you on the row count of the second <legacyBold>INSERT</legacyBold>. The third call to <legacyBold>SQLMoreResults</legacyBold> will position you on the result set of the second <legacyBold>SELECT</legacyBold> statement.</para>
        </listItem>
        <listItem>
          <para>The row counts corresponding to the two <legacyBold>INSERTs</legacyBold> are rolled up into one single row count that is available. (A call to <legacyBold>SQLGetInfo</legacyBold> returns the SQL_BRC_ROLLED_UP bit for the SQL_BATCH_ROW_COUNT information type.) The first call to <legacyBold>SQLMoreResults</legacyBold> will position you on the rolled-up row count, and the second call to <legacyBold>SQLMoreResults</legacyBold> will position you on the result set of the second <legacyBold>SELECT</legacyBold>.</para>
        </listItem>
      </list>
      <para>Certain drivers make row counts available only for explicit batches and not for stored procedures.</para>
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
              <para>Fetching a single row or a block of data in a forward-only direction</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>
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