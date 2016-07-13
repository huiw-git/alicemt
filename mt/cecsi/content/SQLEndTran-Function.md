---
title: SQLEndTran Function
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
  - SQLEndTran
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLEndTran Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0 Standards Compliance: ISO 92</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLEndTran</legacyBold> requests a commit or rollback operation for all active operations on all statements associated with a connection. <legacyBold>SQLEndTran</legacyBold> can also request that a commit or rollback operation be performed for all connections associated with an environment.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLEndTran</legacyBold>(
     SQLSMALLINT   <parameterReference>HandleType</parameterReference>,
     SQLHANDLE     <parameterReference>Handle</parameterReference>,
     SQLSMALLINT   <parameterReference>CompletionType</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Handle type identifier. Contains either SQL_HANDLE_ENV (if <legacyItalic>Handle</legacyItalic> is an environment handle) or SQL_HANDLE_DBC (if <legacyItalic>Handle</legacyItalic> is a connection handle).</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The handle, of the type indicated by <legacyItalic>HandleType</legacyItalic>, indicating the scope of the transaction. See "Comments" for more information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>CompletionType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] One of the following two values:</para>
          <para>SQL_COMMIT SQL_ROLLBACK </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLEndTran</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with the appropriate <legacyItalic>HandleType</legacyItalic> and <legacyItalic>Handle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLEndTran</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>08003</para>
            </TD>
            <TD>
              <para>Connection not open</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC, and the <legacyItalic>Handle</legacyItalic> was not in a connected state.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08007</para>
            </TD>
            <TD>
              <para>Connection failure during transaction</para>
            </TD>
            <TD>
              <para>The <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC, and the connection associated with the <legacyItalic>Handle</legacyItalic> failed during the execution of the function, and it cannot be determined whether the requested <legacyBold>COMMIT</legacyBold> or <legacyBold>ROLLBACK</legacyBold> occurred before the failure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>25S01</para>
            </TD>
            <TD>
              <para>Transaction state unknown</para>
            </TD>
            <TD>
              <para>One or more of the connections in <legacyItalic>Handle</legacyItalic> failed to complete the transaction with the outcome specified, and the outcome is unknown.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>25S02</para>
            </TD>
            <TD>
              <para>Transaction is still active</para>
            </TD>
            <TD>
              <para>The driver was not able to guarantee that all work in the global transaction could be completed atomically, and the transaction is still active.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>25S03</para>
            </TD>
            <TD>
              <para>Transaction is rolled back</para>
            </TD>
            <TD>
              <para>The driver was not able to guarantee that all work in the global transaction could be completed atomically, and all work in the transaction active in <legacyItalic>Handle</legacyItalic> was rolled back.</para>
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
              <para>40002</para>
            </TD>
            <TD>
              <para>Integrity constraint violation</para>
            </TD>
            <TD>
              <para>The <legacyItalic>CompletionType</legacyItalic> was SQL_COMMIT, and the commitment of changes caused integrity constraint violation. As a result, the transaction was rolled back.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*szMessageText</legacyItalic> buffer describes the error and its cause.</para>
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
              <para>Asynchronous processing was enabled for the <parameterReference>ConnectionHandle</parameterReference>. The function was called, and before it finished executing <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link> was called on the <parameterReference>ConnectionHandle</parameterReference>. Then the function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
              <para>The function was called, and before it finished executing <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was called on the <parameterReference>ConnectionHandle</parameterReference> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function was called for a statement handle associated with the <legacyItalic>ConnectionHandle</legacyItalic> and was still executing when <legacyBold>SQLEndTran</legacyBold> was called.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for a statement handle associated with the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <parameterReference>Handle</parameterReference> with <parameterReference>HandleType</parameterReference> set to SQL_HANDLE_DBC and was still executing when this function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with <parameterReference>Handle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY012</para>
            </TD>
            <TD>
              <para>Invalid transaction operation code</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>CompletionType</legacyItalic> was neither SQL_COMMIT nor SQL_ROLLBACK.</para>
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
              <para>HY092</para>
            </TD>
            <TD>
              <para>Invalid attribute/option identifier</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>HandleType</legacyItalic> was neither SQL_HANDLE_ENV nor SQL_HANDLE_DBC.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY115</para>
            </TD>
            <TD>
              <para>SQLEndTran is not allowed for an environment that contains a connection with asynchronous function execution enabled</para>
            </TD>
            <TD>
              <para>(DM) <parameterReference>HandleType</parameterReference> cannot be set to SQL_HANDLE_ENV if asynchronous execution of connection functions is enabled for a connection in the environment.</para>
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
              <para>(DM) For more information about suspended state, refer to the Comments section of this topic.</para>
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
              <para>The driver or data source does not support the <legacyBold>ROLLBACK</legacyBold> operation.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>ConnectionHandle</legacyItalic> does not support the function.</para>
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
      <para>For an ODBC 3.<legacyItalic>x</legacyItalic> driver, if <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV and <legacyItalic>Handle</legacyItalic> is a valid environment handle, then the Driver Manager will call <legacyBold>SQLEndTran</legacyBold> in each driver associated with the environment. The <legacyItalic>Handle</legacyItalic> argument for the call to a driver will be the driver's environment handle. For an ODBC 2.<legacyItalic>x</legacyItalic> driver, if <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV and <legacyItalic>Handle</legacyItalic> is a valid environment handle, and there are multiple connections in a connected state in that environment, then the Driver Manager will call <legacyBold>SQLTransact</legacyBold> in the driver once for each connection in a connected state in that environment. The <legacyItalic>Handle</legacyItalic> argument in each call will be the connection's handle. In either case, the driver will attempt to commit or roll back transactions, depending on the value of <legacyItalic>CompletionType</legacyItalic>, on all connections that are in a connected state on that environment. Connections that are not active do not affect the transaction. </para>
      <alert class="note">
        <para>
          <legacyBold>SQLEndTran</legacyBold> cannot be used to commit or roll back transactions on a shared environment. SQLSTATE HY092 (Invalid attribute/option identifier) will be returned if <legacyBold>SQLEndTran</legacyBold> is called with <legacyItalic>Handle</legacyItalic> set to either the handle of a shared environment or the handle of a connection on a shared environment.</para>
      </alert>
      <para>The Driver Manager will return SQL_SUCCESS only if it receives SQL_SUCCESS for each connection. If the Driver Manager receives SQL_ERROR on one or more connections, it returns SQL_ERROR to the application, and the diagnostic information is placed in the diagnostic data structure of the environment. To determine which connection or connections failed during the commit or rollback operation, the application can call <legacyBold>SQLGetDiagRec</legacyBold> for each connection.</para>
      <alert class="note">
        <para>The Driver Manager does not simulate a global transaction across all connections and therefore does not use two-phase commit protocols.</para>
      </alert>
      <para>If <legacyItalic>CompletionType</legacyItalic> is SQL_COMMIT, <legacyBold>SQLEndTran</legacyBold> issues a commit request for all active operations on any statement associated with an affected connection. If <legacyItalic>CompletionType</legacyItalic> is SQL_ROLLBACK, <legacyBold>SQLEndTran</legacyBold> issues a rollback request for all active operations on any statement associated with an affected connection. If no transactions are active, <legacyBold>SQLEndTran</legacyBold> returns SQL_SUCCESS with no effect on any data sources. For more information, see <legacyLink xlink:href="800f2c1a-6f79-4ed1-830b-aa1a62ff5165">Committing and Rolling Back Transactions</legacyLink>.</para>
      <para>If the driver is in manual-commit mode (by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_AUTOCOMMIT attribute set to SQL_AUTOCOMMIT_OFF), a new transaction is implicitly started when an SQL statement that can be contained within a transaction is executed against the current data source. For more information, see <legacyLink xlink:href="963fe470-f7cb-4dbe-a779-05f98d7ff17d">Commit Mode</legacyLink>.</para>
      <para>To determine how transaction operations affect cursors, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CURSOR_ROLLBACK_BEHAVIOR and SQL_CURSOR_COMMIT_BEHAVIOR options. For more information, see the following paragraphs and also see <legacyLink xlink:href="523e22a2-7b53-4c25-97c1-ef0284aec76e">Effect of Transactions on Cursors and Prepared Statements</legacyLink>.</para>
      <para>If the SQL_CURSOR_ROLLBACK_BEHAVIOR or SQL_CURSOR_COMMIT_BEHAVIOR value equals SQL_CB_DELETE, <legacyBold>SQLEndTran</legacyBold> closes and deletes all open cursors on all statements associated with the connection and discards all pending results. <legacyBold>SQLEndTran</legacyBold> leaves any statement present in an allocated (unprepared) state; the application can reuse them for subsequent SQL requests or can call <legacyBold>SQLFreeStmt</legacyBold> or <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT to deallocate them.</para>
      <para>If the SQL_CURSOR_ROLLBACK_BEHAVIOR or SQL_CURSOR_COMMIT_BEHAVIOR value equals SQL_CB_CLOSE, <legacyBold>SQLEndTran</legacyBold> closes all open cursors on all statements associated with the connection. <legacyBold>SQLEndTran</legacyBold> leaves any statement present in a prepared state; the application can call <legacyBold>SQLExecute</legacyBold> for a statement associated with the connection without first calling <legacyBold>SQLPrepare</legacyBold>.</para>
      <para>If the SQL_CURSOR_ROLLBACK_BEHAVIOR or SQL_CURSOR_COMMIT_BEHAVIOR value equals SQL_CB_PRESERVE, <legacyBold>SQLEndTran</legacyBold> does not affect open cursors associated with the connection. Cursors remain at the row they pointed to prior to the call to <legacyBold>SQLEndTran</legacyBold>.</para>
      <para>For drivers and data sources that support transactions, calling <legacyBold>SQLEndTran</legacyBold> with either SQL_COMMIT or SQL_ROLLBACK when no transaction is active returns SQL_SUCCESS (indicating that there is no work to be committed or rolled back) and has no effect on the data source.</para>
      <para>When a driver is in autocommit mode, the Driver Manager does not call <legacyBold>SQLEndTran</legacyBold> in the driver. <legacyBold>SQLEndTran</legacyBold> always returns SQL_SUCCESS regardless of whether it is called with a <legacyItalic>CompletionType</legacyItalic> of SQL_COMMIT or SQL_ROLLBACK.</para>
      <para>Drivers or data sources that do not support transactions (<legacyBold>SQLGetInfo</legacyBold> <legacyItalic>option</legacyItalic> SQL_TXN_CAPABLE is SQL_TC_NONE) are effectively always in autocommit mode and therefore always return SQL_SUCCESS for <legacyBold>SQLEndTran</legacyBold> whether or not they are called with a <legacyItalic>CompletionType</legacyItalic> of SQL_COMMIT or SQL_ROLLBACK. Such drivers and data sources do not actually roll back transactions when requested to do so.</para>
    </content>
  </section>
  <section>
    <title>Suspended State</title>
    <content>
      <para>In Driver Managers that were released before Windows 7, a transaction was active if <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> returned SQL_ERROR from the driver. However, it was possible that the transaction had been successfully committed on the server, but the driver on the client had not been notified (for example, because a network error occurred). This would leave the connection in a bad state. Starting with Windows 7, when <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> returns SQL_ERROR, the connection might be in a suspended state. In a suspended state, it is possible to call read-only functions. Eventually, the application should call <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> on a suspended connection to release resources.</para>
      <para>If all of the following conditions are true, the connection will be put into a suspended state:</para>
      <list class="bullet">
        <listItem>
          <para>The driver returns SQL_ERROR from <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference>.</para>
        </listItem>
        <listItem>
          <para>The driver is ODBC version 3.8, or later.</para>
        </listItem>
        <listItem>
          <para>The application version is 3.8 or later; or the recompiled ODBC 2.x or 3.x application successfully cancels the <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> function through <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>.</para>
        </listItem>
        <listItem>
          <para>The driver did not return one of the following messages, which confirm that the transaction did not complete:</para>
          <list class="bullet">
            <listItem>
              <para>25S03: Transaction is rolled back</para>
            </listItem>
            <listItem>
              <para>40001: Serialization failure</para>
            </listItem>
            <listItem>
              <para>40002: Integrity constraint</para>
            </listItem>
            <listItem>
              <para>HYC00: Optional feature not implemented</para>
            </listItem>
          </list>
        </listItem>
      </list>
      <para>If <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> was called on an environment handle and one of its connections met the above conditions, all connections connecting to the same driver will be put into the suspended state.</para>
      <para>After an application calls <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> on a suspended connection, the connection can be used to reconnect to another data source or the same data source.</para>
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
              <para>Canceling a function running asynchronously on a connection handle.</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a driver or data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Freeing a handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Freeing a statement handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
<link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>