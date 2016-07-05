---
title: SQLCancel Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLCancel
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: ac0b5972-627f-4440-8c5a-0e8da728726d
translation.priority.ht: 
  - en-gb
---
# SQLCancel Function
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
          <legacyBold>SQLCancel</legacyBold> cancels the processing on a statement.</para>
        <para>To cancel processing on a connection or statement, use <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLCancel</legacyBold>(
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
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLCancel</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLCancel </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec</legacyLink> in the argument <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
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
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence  error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) Cancel operation failed because an asynchronous operation is in progress on a connection handle that is associated with <legacyItalic>StatementHandle</legacyItalic>.</para>
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
              <para>HY018</para>
            </TD>
            <TD>
              <para>Server declined cancel request</para>
            </TD>
            <TD>
              <para>The server declined the cancel request.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLCancel</legacyBold> can cancel the following types of processing on a statement:</para>
      <list class="bullet">
        <listItem>
          <para>A function running asynchronously on the statement.</para>
        </listItem>
        <listItem>
          <para>A function on a statement that needs data.</para>
        </listItem>
        <listItem>
          <para>A function running on the statement on another thread.</para>
        </listItem>
      </list>
      <para>In ODBC 2.<legacyItalic>x</legacyItalic>, if an application calls <legacyBold>SQLCancel</legacyBold> when no processing is being done on the statement, <legacyBold>SQLCancel</legacyBold> has the same effect as <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option; this behavior is defined only for completeness and applications should call <legacyBold>SQLFreeStmt</legacyBold> or <legacyBold>SQLCloseCursor</legacyBold> to close cursors. </para>
      <para>When <legacyBold>SQLCancel</legacyBold> is called to cancel a function running asynchronously in a statement or a function on a statement that needs data, diagnostic records posted by the function being canceled are cleared, and <legacyBold>SQLCancel</legacyBold> posts its own diagnostic records; when <legacyBold>SQLCancel</legacyBold> is called to cancel a function running on a statement on another thread, however, it does not clear the diagnostic records of the being canceled function and does not post its own diagnostic records.</para>
    </content>
  </section>
  <section>
    <title>Canceling Asynchronous Processing</title>
    <content>
      <para>After an application calls a function asynchronously, it calls the function repeatedly to determine whether it has finished processing. If the function is still processing, it returns SQL_STILL_EXECUTING. If the function has finished processing, it returns a different code.</para>
      <para>After any call to the function that returns SQL_STILL_EXECUTING, an application can call <legacyBold>SQLCancel</legacyBold> to cancel the function. If the cancel request is successful, the driver returns SQL_SUCCESS. This message does not indicate that the function was actually canceled; it indicates that the cancel request was processed. When or if the function is actually canceled is driver-dependent and data source–dependent. The application must continue to call the original function until the return code is not SQL_STILL_EXECUTING. If the function was successfully canceled, the return code is SQL_ERROR and SQLSTATE HY008 (Operation canceled). If the function completed its normal processing, the return code is SQL_SUCCESS or SQL_SUCCESS_WITH_INFO if the function succeeded or SQL_ERROR and a SQLSTATE other than HY008 (Operation canceled) if the function failed.</para>
      <alert class="note">
        <para>In ODBC 3.5, a call to <legacyBold>SQLCancel</legacyBold> when no processing is being done on the statement is not treated as <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option, but has is no effect at all. To close a cursor, an application should call <legacyBold>SQLCloseCursor</legacyBold>, not <legacyBold>SQLCancel</legacyBold>.</para>
      </alert>
      <para>For more information about asynchronous processing, see <legacyLink xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Canceling Functions that Need Data</title>
    <content>
      <para>After <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns SQL_NEED_DATA and before data has been sent for all data-at-execution parameters, an application can call <legacyBold>SQLCancel</legacyBold> to cancel the statement execution. After the statement has been canceled, the application can call <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> again. For more information, see <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>.</para>
      <para>After <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> returns SQL_NEED_DATA and before data has been sent for all data-at-execution columns, an application can call <legacyBold>SQLCancel</legacyBold> to cancel the operation. After the operation has been canceled, the application can call <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> again; canceling does not affect the cursor state or the current cursor position. For more information, see <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink> or <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Canceling Functions Executing on Another Thread</title>
    <content>
      <para>In a multithread application, the application can cancel a function that is running on another thread. To cancel the function, the application calls <legacyBold>SQLCancel</legacyBold> with the same statement handle as that used by the target function, but on a different thread. How the function is canceled depends on the driver and the operating system. As in canceling a function running asynchronously, the return code of the <legacyBold>SQLCancel</legacyBold> indicates only whether the driver processed the request successfully. Only SQL_SUCCESS or SQL_ERROR can be returned; no diagnostic information is returned. If the original function is canceled, it returns SQL_ERROR and SQLSTATE HY008 (Operation canceled).</para>
      <para>If an SQL statement is being executed when <legacyBold>SQLCancel</legacyBold> is called on another thread to cancel the statement execution, it is possible for the execution to succeed and return SQL_SUCCESS while the cancel is also successful. In this case, the Driver Manager assumes that the cursor opened by the statement execution is closed by the cancel, so the application will not be able to use the cursor.</para>
      <para>For more information about threading, see <legacyLink xlink:href="cdfebdf5-12ff-4e28-8055-41f49b77f664">Multithreading</legacyLink>.</para>
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
                <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Performing bulk insert or update operations</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cancels a function running asynchronously on a connection handle, in addition to the functionality of <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>.</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>
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
              <para>Freeing a statement handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Obtaining a field of a diagnostic record or a field of the diagnostic header</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Obtaining multiple fields of a diagnostic data structure</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the next parameter to send data for</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Sending parameter data at execution time</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Positioning the cursor in a rowset, refreshing data in the rowset, or updating or deleting data in the result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>
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