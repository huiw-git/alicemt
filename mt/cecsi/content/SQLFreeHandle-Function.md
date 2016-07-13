---
title: SQLFreeHandle Function
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
  - SQLFreeHandle
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFreeHandle Function
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
          <legacyBold>SQLFreeHandle</legacyBold> frees resources associated with a specific environment, connection, statement, or descriptor handle.</para>
        <alert class="note">
          <para>This function is a generic function for freeing handles. It replaces the ODBC 2.0 functions <legacyBold>SQLFreeConnect</legacyBold> (for freeing a connection handle) and <legacyBold>SQLFreeEnv</legacyBold> (for freeing an environment handle). <legacyBold>SQLFreeConnect</legacyBold> and <legacyBold>SQLFreeEnv</legacyBold> are both deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. <legacyBold>SQLFreeHandle</legacyBold> also replaces the ODBC 2.0 function <legacyBold>SQLFreeStmt</legacyBold> (with the SQL_DROP <legacyItalic>Option</legacyItalic>) for freeing a statement handle. For more information, see "Comments." For more information about what the Driver Manager maps this function to when an ODBC 3<legacyItalic>.x</legacyItalic> application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN<legacyBold> SQLFreeHandle</legacyBold>(
     SQLSMALLINT   <parameterReference>HandleType</parameterReference>,
     SQLHANDLE     <parameterReference>Handle</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type of handle to be freed by <legacyBold>SQLFreeHandle</legacyBold>. Must be one of the following values:</para>
          <list class="bullet">
            <listItem>
              <para>SQL_HANDLE_DBC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DBC_INFO_TOKEN</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_DESC</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_ENV</para>
            </listItem>
            <listItem>
              <para>SQL_HANDLE_STMT</para>
            </listItem>
          </list>
          <para>SQL_HANDLE_DBC_INFO_TOKEN handle is used only by the Driver Manager and driver. Applications should not use this handle type. For more information about SQL_HANDLE_DBC_INFO_TOKEN, see <link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link>.</para>
          <para>If <legacyItalic>HandleType</legacyItalic> is not one of these values, <legacyBold>SQLFreeHandle</legacyBold> returns SQL_INVALID_HANDLE.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The handle to be freed.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
      <para>If <legacyBold>SQLFreeHandle</legacyBold> returns SQL_ERROR, the handle is still valid.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLFreeHandle</legacyBold> returns SQL_ERROR, an associated SQLSTATE value may be obtained from the diagnostic data structure for the handle that <legacyBold>SQLFreeHandle</legacyBold> tried to free but could not. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLFreeHandle</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_ENV, and at least one connection was in an allocated or connected state. <legacyBold>SQLDisconnect</legacyBold> and <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC must be called for each connection before calling <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DBC, and the function was called before calling <legacyBold>SQLDisconnect</legacyBold> for the connection.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DBC. An asynchronously executing function was called with <legacyItalic>Handle</legacyItalic> and the function was still executing when this function was called.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT. <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called with the statement handle and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT. An asynchronously executing function was called on the statement handle or on the associated connection handle and the function was still executing when this function was called.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DESC. An asynchronously executing function was called on the associated connection handle; and the function was still executing when this function was called.</para>
              <para>(DM) All subsidiary handles and other resources were not released before <legacyBold>SQLFreeHandle</legacyBold> was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>Handle</parameterReference> and <parameterReference>HandleType</parameterReference> was set to SQL_HANDLE_STMT or SQL_HANDLE_DESC returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT or SQL_HANDLE_DESC, and the function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY017</para>
            </TD>
            <TD>
              <para>Invalid use of an automatically allocated descriptor handle.</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>Handle</legacyItalic> argument was set to the handle for an automatically allocated descriptor.</para>
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
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_DESC, and the driver was an ODBC 2<legacyItalic>.x</legacyItalic> driver.</para>
              <para>(DM) The <legacyItalic>HandleType</legacyItalic> argument was SQL_HANDLE_STMT, and the driver was not a valid ODBC driver.</para>
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
        <legacyBold>SQLFreeHandle</legacyBold> is used to free handles for environments, connections, statements, and descriptors, as described in the following sections. For general information about handles, see <legacyLink xlink:href="f663101e-a4cc-402b-b9d7-84d5e975be71">Handles</legacyLink>.</para>
      <para>An application should not use a handle after it has been freed; the Driver Manager does not check the validity of a handle in a function call.</para>
    </content>
  </section>
  <section>
    <title>Freeing an Environment Handle</title>
    <content>
      <para>Before it calls <legacyBold>SQLFreeHandle </legacyBold>with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV, an application must call <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC for all connections allocated under the environment. Otherwise, the call to <legacyBold>SQLFreeHandle</legacyBold> returns SQL_ERROR and the environment and any active connection remains valid. For more information, see <legacyLink xlink:href="917f1b0c-272b-4e37-a1f5-87cd24b9fa21">Environment Handles</legacyLink> and <legacyLink xlink:href="77b5d1d6-7eb7-428d-bf75-a5c5a325d25c">Allocating the Environment Handle</legacyLink>.</para>
      <para>If the environment is a shared environment, the application that calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV no longer has access to the environment after the call, but the environment's resources are not necessarily freed. The call to <legacyBold>SQLFreeHandle</legacyBold> decrements the reference count of the environment. The reference count is maintained by the Driver Manager. If it does not reach zero, the shared environment is not freed, because it is still being used by another component. If the reference count reaches zero, the resources of the shared environment are freed.</para>
    </content>
  </section>
  <section>
    <title>Freeing a Connection Handle</title>
    <content>
      <para>Before it calls <legacyBold>SQLFreeHandle </legacyBold>with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC, an application must call <legacyBold>SQLDisconnect</legacyBold> for the connection if there is a connection on this handle<legacyItalic>.</legacyItalic> Otherwise, the call to <legacyBold>SQLFreeHandle</legacyBold> returns SQL_ERROR and the connection remains valid.</para>
      <para>For more information, see <legacyLink xlink:href="12222653-f04d-46d6-bdee-61348f5d550f">Connection Handles</legacyLink> and <legacyLink xlink:href="83dbf0bf-b400-41fb-8537-9b016050dc3c">Disconnecting from a Data Source or Driver</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Freeing a Statement Handle</title>
    <content>
      <para>A call to <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT frees all resources that were allocated by a call to <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT. When an application calls <legacyBold>SQLFreeHandle</legacyBold> to free a statement that has pending results, the pending results are deleted. When an application frees a statement handle, the driver frees the four automatically allocated descriptors associated with that handle. For more information, see <legacyLink xlink:href="65d6d78b-a8c8-489a-9dad-f8d127a44882">Statement Handles</legacyLink> and <legacyLink xlink:href="ee18e2f1-2690-4cc1-9e5c-e20244e5d480">Freeing a Statement Handle</legacyLink>.</para>
      <para>Notice that <legacyBold>SQLDisconnect</legacyBold> automatically drops any statements and descriptors open on the connection.</para>
    </content>
  </section>
  <section>
    <title>Freeing a Descriptor Handle</title>
    <content>
      <para>A call to <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC frees the descriptor handle in <legacyItalic>Handle</legacyItalic>. The call to <legacyBold>SQLFreeHandle</legacyBold> does not release any memory allocated by the application that may be referenced by a pointer field (including SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR) of any descriptor record of <legacyItalic>Handle</legacyItalic>. The memory allocated by the driver for fields that are not pointer fields is freed when the handle is freed. When a user-allocated descriptor handle is freed, all statements that the freed handle had been associated with revert to their respective automatically allocated descriptor handles.</para>
      <alert class="note">
        <para>ODBC 2<legacyItalic>.x</legacyItalic> drivers do not support freeing descriptor handles, just as they do not support allocating descriptor handles.</para>
      </alert>
      <para>Notice that <legacyBold>SQLDisconnect</legacyBold> automatically drops any statements and descriptors open on the connection. When an application frees a statement handle, the driver frees all the automatically generated descriptors associated with that handle.</para>
      <para>For more information about descriptors, see <legacyLink xlink:href="ef2cbb93-cd00-40f8-b1d2-5f5723a991aa">Descriptors</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>For additional code samples, see <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect</legacyLink> and <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>.</para>
    </content>
    <sections>
      <section>
        <title>Code</title>
        <content>
          <code>// SQLFreeHandle.cpp
// compile with: user32.lib odbc32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#include &lt;stdio.h&gt;

int main() {
   SQLRETURN retCode;
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle
   SQLCHAR connStrbuffer[1024];
   SQLSMALLINT connStrBufferLen;

   // Initialize the environment, connection, statement handles.
   SQLHENV henv = NULL;   // Environment   
   SQLHDBC hdbc = NULL;   // Connection handle
   SQLHSTMT hstmt = NULL;   // Statement handle
   
   // Allocate the environment.
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);

   // Set environment attributes.
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);

   // Allocate the connection.
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);

   // Set the login timeout.
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);

   // Let the user select the data source and connect to the database.
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &amp;connStrBufferLen, SQL_DRIVER_PROMPT);

   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   // Free handles, and disconnect.   
   if (hstmt) { 
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);
      hstmt = NULL; 
   }
   if (hdbc) { 
      SQLDisconnect(hdbc);
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
      hdbc = NULL; 
   }
   if (henv) { 
      SQLFreeHandle(SQL_HANDLE_ENV, henv);
      henv = NULL; 
   }
}</code>
        </content>
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
              <para>Allocating a handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCance Functionl</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a cursor name</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName Function</legacyLink>
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
<link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link></relatedTopics>
</developerReferenceWithSyntaxDocument>