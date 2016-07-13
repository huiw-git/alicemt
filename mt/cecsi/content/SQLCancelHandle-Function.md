---
title: SQLCancelHandle Function
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16049b5b-22a7-4640-9897-c25dd0f19d21
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLCancelHandle Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.8 </para>
        <para>Standards Compliance: None</para>
        <para>It is expected that most ODBC 3.8 (and later) drivers will implement this function. If a driver does not, a call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> with a connection handle in the <parameterReference>Handle</parameterReference> parameter will return SQL_ERROR with a SQLSTATE of IM001 and message 'Driver does not support this function’' A call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> with a statement handle as the <parameterReference>Handle</parameterReference> parameter will be mapped to a call to <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> by the Driver Manager and can be processed if the driver implements <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>. An application can use <unmanagedCodeEntityReference>SQLGetFunctions</unmanagedCodeEntityReference> to determine if a driver supports <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>.</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> cancels the processing on a connection or statement. The Driver Manager maps a call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to a call to <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> when <parameterReference>HandleType</parameterReference> is SQL_HANDLE_STMT.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLCancelHandle</legacyBold>(
      SQLSMALLINT  <parameterReference>HandleType,</parameterReference>
      SQLHANDLE    <parameterReference>Handle</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type of the handle on which to cacel processing. Valid values are SQL_HANDLE_DBC or SQL_HANDLE_STMT.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The handle on which to cancel processing.</para>
          <para>If <parameterReference>Handle</parameterReference> is not a valid handle of the type specified by <parameterReference>HandleType</parameterReference>, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> returns SQL_INVALID_HANDLE.</para>
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
      <para>When <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <unmanagedCodeEntityReference>SQLGetDiagRec</unmanagedCodeEntityReference> with a <parameterReference>HandleType</parameterReference> of SQL_HANDLE_STMT and a statement handle <parameterReference>Handle</parameterReference> or a <parameterReference>HandleType</parameterReference> of SQL_HANDLE_DBC and a connection handle <parameterReference>Handle</parameterReference>.</para>
      <para>The following table lists the SQLSTATE values commonly returned by <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLSTATE </para>
            </TD>
            <TD>
              <para>Error </para>
            </TD>
            <TD>
              <para>Description </para>
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
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>An asynchronously executing, statement-related function was called for one of the statement handles associated with the <parameterReference>Handle</parameterReference>, and <parameterReference>HandleType</parameterReference> was set to SQL_HANDLE_DBC. The asynchronous function was still executing when <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was called.</para>
              <para>(DM) The <parameterReference>HandleType</parameterReference> argument was SQL_HANDLE_STMT; an asynchronously executing function was called on the associated connection handle; and the function was still executing when this function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>Handle</parameterReference> and <parameterReference>HandleType</parameterReference> was set to SQL_HANDLE_DBC, and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>
                <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference> was called for <parameterReference>ConnectionHandle</parameterReference>, and returned SQL_NEED_DATA. This function was called before the browsing process completed.</para>
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
              <para>
                <parameterReference>HandleType</parameterReference> was set to SQL_HANDLE_ENV or SQL_HANDLE_DESC.</para>
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
              <para>The connection timeout period expired before the data source responded to the request. The connection timeout period is set through <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference>, SQL_ATTR_CONNECTION_TIMEOUT.</para>
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
              <para>(DM) The driver associated with the <parameterReference>Handle</parameterReference> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>If <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> is called with <parameterReference>HandleType</parameterReference> set to SQL_HANDLE_STMT, it can return any SQLSTATE that can be returned by the function <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference>.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>This function is similar to <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> but may take either a connection or statement handle as a parameter rather than only a statement handle. The Driver Manager maps a call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to a call to <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> when <parameterReference>HandleType</parameterReference> is SQL_HANDLE_STMT. This allows applications to use <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to cancel statement operations even if the driver does not implement <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>.</para>
      <para>For more information about cancelling a statement operation, see <link xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</link>.</para>
      <para>If there are no operations in progress on <parameterReference>Handle</parameterReference> the call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> has no effect. </para>
      <para>
        <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on a connection handle can cancel the following types of processing:</para>
      <list class="bullet">
        <listItem>
          <para>A function running asynchronously on the connection.</para>
        </listItem>
        <listItem>
          <para>A function running on the connection handle on another thread.</para>
        </listItem>
      </list>
      <para>When <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> is called to cancel a function running asynchronously in a connection, diagnostic records posted by <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> are appended to those returned by the operation being canceled; <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> does not return diagnostic records, however, when canceling a function running on a connection on another thread.</para>
      <para>Using <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to cancel <unmanagedCodeEntityReference>SQLEndTran</unmanagedCodeEntityReference> may put the connection in suspended state. For more information on suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
      <alert class="note">
        <para>For information about how to use <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> in an application that will be deployed on a Windows operating system older than Windows 7, see <link xlink:href="0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6">Compatibility Matrix</link>.</para>
      </alert>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Canceling Connection-Related Asynchronous Processing</title>
            <content>
              <para>If a function returns SQL_STILL_EXECUTING, an application can call <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to cancel the operation. If the cancel request is successful, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> returns SQL_SUCCESS. This does not mean that the original function was canceled; it indicates that the cancel request was processed. The driver and data source determine when or if the operation is canceled. The application must continue to call the original function until the return code is not SQL_STILL_EXECUTING. If the original function was canceled, the return code is SQL_ERROR and SQLSTATE HY008 (Operation canceled). If the original function completed its normal processing (was not cancelled), the return code is SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, or SQL_ERROR and a SQLSTATE other than HY008 (Operation canceled), if the original function failed.</para>
            </content>
          </section>
          <section>
            <title>Canceling Functions Executing on Another Thread</title>
            <content>
              <para>In a multithread application, the application can cancel an operation that is running on another thread. To cancel the operation, the application calls <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> with the handle used by the function, but on a different thread. The driver and operating system determine how the operation is canceled. The <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> return code indicates whether the driver processed the request, returning either SQL_SUCCESS or SQL_ERROR (no diagnostic information is returned). If processing on the original function is canceled, the original function returns SQL_ERROR and SQLSTATE HY008 (Operation cancelled).</para>
              <para>If a function is being executed when <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> is called on another thread to cancel the function, it is possible for the function to succeed and return SQL_SUCCESS before the cancel can take effect. A call to <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> has no effect if the operation completed before <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was able to cancel the operation.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
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
              <para>Canceling a function running asynchronously on a statement handle, canceling a function on a statement that needs data, or canceling a function running on a statement on another thread.</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</link>
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
<link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>