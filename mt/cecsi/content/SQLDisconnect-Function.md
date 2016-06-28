---
title: SQLDisconnect Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLDisconnect
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
translation.priority.ht: 
  - en-gb
---
# SQLDisconnect Function
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
          <legacyBold>SQLDisconnect</legacyBold> closes the connection associated with a specific connection handle.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDisconnect</legacyBold>(
     SQLHDBC     <parameterReference>ConnectionHandle</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>ConnectionHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Connection handle.</para>
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
      <para>When <legacyBold>SQLDisconnect</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLDisconnect</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>01002</para>
            </TD>
            <TD>
              <para>Disconnect error</para>
            </TD>
            <TD>
              <para>An error occurred during the disconnect. However, the disconnect succeeded. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The connection specified in the argument <legacyItalic>ConnectionHandle</legacyItalic> was not open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>25000</para>
            </TD>
            <TD>
              <para>Invalid transaction state</para>
            </TD>
            <TD>
              <para>There was a transaction in process on the connection specified by the argument <legacyItalic>ConnectionHandle</legacyItalic>. The transaction remains active.</para>
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
              <para>Asynchronous processing was enabled for the <parameterReference>ConnectionHandle</parameterReference>. The function was called, and before it finshed executing <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link> was called on the <parameterReference>ConnectionHandle</parameterReference>. Then the function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
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
              <para> (DM) An asynchronously executing function was called for a <legacyItalic>StatementHandle</legacyItalic> associated with the <legacyItalic>ConnectionHandle</legacyItalic> and was still executing when <legacyBold>SQLDisconnect</legacyBold> was called.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for a <legacyItalic>StatementHandle</legacyItalic> associated with the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
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
              <para>The connection timeout period expired before the data source responded to the request, and the connection is still active. The connection timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_CONNECTION_TIMEOUT.</para>
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
      <para>If an application calls <legacyBold>SQLDisconnect</legacyBold> after <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_NEED_DATA and before it returns a different return code, the driver cancels the connection browsing process and returns the connection to an unconnected state.</para>
      <para>If an application calls <legacyBold>SQLDisconnect</legacyBold> while there is an incomplete transaction associated with the connection handle, the driver returns SQLSTATE 25000 (Invalid transaction state), indicating that the transaction is unchanged and the connection is open. An incomplete transaction is one that has not been committed or rolled back with <legacyBold>SQLEndTran</legacyBold>.</para>
      <para>If an application calls <legacyBold>SQLDisconnect</legacyBold> before it has freed all statements associated with the connection, the driver, after it successfully disconnects from the data source, frees those statements and all descriptors that have been explicitly allocated on the connection. However, if one or more of the statements associated with the connection are still executing asynchronously, <legacyBold>SQLDisconnect</legacyBold> returns SQL_ERROR with a SQLSTATE value of HY010 (Function sequence error). Also, <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> will free all associated statements and all descriptors that have been explicitly allocated on the connection, if the connection is in a suspended state or if <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> was successfully canceled by <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>.</para>
      <para>For information about how an application uses <legacyBold>SQLDisconnect</legacyBold>, see <legacyLink xlink:href="83dbf0bf-b400-41fb-8537-9b016050dc3c">Disconnecting from a Data Source or Driver</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Disconnecting from a Pooled Connection</title>
    <content>
      <para>If connection pooling is enabled for a shared environment and an application calls <legacyBold>SQLDisconnect</legacyBold> on a connection in that environment, the connection is returned to the connection pool and is still available to other components using the same shared environment.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>, <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect Function</legacyLink>, and <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.</para>
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
              <para>Allocating a handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source using a connection string or dialog box</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a commit or rollback operation</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Freeing a connection handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="0d22eaeb-3c75-47fb-af9a-6f7397e61b9c">SQLFreeConnect Function</legacyLink>
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