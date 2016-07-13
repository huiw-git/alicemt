---
title: SQLFreeStmt Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLFreeStmt
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFreeStmt Function
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
          <legacyBold>SQLFreeStmt</legacyBold> stops processing associated with a specific statement, closes any open cursors associated with the statement, discards pending results, or, optionally, frees all resources associated with the statement handle.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLFreeStmt</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLUSMALLINT   <parameterReference>Option</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle</para>
        </definition>
        <definedTerm>
          <legacyItalic>Option</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] One of the following options:</para>
          <para>SQL_ CLOSE: Closes the cursor associated with <legacyItalic>StatementHandle</legacyItalic> (if one was defined) and discards all pending results. The application can reopen this cursor later by executing a <legacyBold>SELECT</legacyBold> statement again with the same or different parameter values. If no cursor is open, this option has no effect for the application. <legacyBold>SQLCloseCursor</legacyBold> can also be called to close a cursor. For more information, see <legacyLink xlink:href="4f19bf5e-6d8c-40ae-a975-cfd62a0790ec">Closing the Cursor</legacyLink>.</para>
          <para>SQL_DROP: This option is deprecated. A call to <legacyBold>SQLFreeStmt</legacyBold> with an <legacyItalic>Option</legacyItalic> of SQL_DROP is mapped in the Driver Manager to <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink>.   </para>
          <para>SQL_UNBIND: Sets the SQL_DESC_COUNT field of the ARD to 0, releasing all column buffers bound by <legacyBold>SQLBindCol</legacyBold> for the given <legacyItalic>StatementHandle</legacyItalic>. This does not unbind the bookmark column; to do that, the SQL_DESC_DATA_PTR field of the ARD for the bookmark column is set to NULL. Notice that if this operation is performed on an explicitly allocated descriptor that is shared by more than one statement, the operation will affect the bindings of all statements that share the descriptor. For more information, see <legacyLink xlink:href="052870e3-3f3f-4f07-91da-b649348225f4">Overview of Retrieving Results (Basic)</legacyLink>.</para>
          <para>SQL_RESET_PARAMS: Sets the SQL_DESC_COUNT field of the APD to 0, releasing all parameter buffers set by <legacyBold>SQLBindParameter</legacyBold> for the given <legacyItalic>StatementHandle</legacyItalic>. If this operation is performed on an explicitly allocated descriptor that is shared by more than one statement, this operation will affect the bindings of all the statements that share the descriptor. For more information, see <legacyLink xlink:href="7538a82b-b08b-4c8f-9809-e4ccea16db11">Binding Parameters</legacyLink>.</para>
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
      <para>When <legacyBold>SQLFreeStmt</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLFreeStmt</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when <unmanagedCodeEntityReference>SQLFreeStmt</unmanagedCodeEntityReference> was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called with <parameterReference>Option</parameterReference> set to SQL_RESET_PARAMS before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
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
              <para>HY092</para>
            </TD>
            <TD>
              <para>Option type out of range</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>Option</legacyItalic> was not:</para>
              <para>SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS</para>
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
      <para>Calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option is equivalent to calling <legacyBold>SQLCloseCursor</legacyBold>, except that <legacyBold>SQLFreeStmt</legacyBold> with SQL_CLOSE does not affect the application if no cursor is open on the statement. If no cursor is open, a call to <legacyBold>SQLCloseCursor</legacyBold> returns SQLSTATE 24000 (Invalid cursor state).</para>
      <para>An application should not use a statement handle after it has been freed; the Driver Manager does not check the validity of a handle in a function call.</para>
    </content>
  </section>
  <codeExample>
    <description>
      <content>
        <para>It is a good programming practice to free handles. However, for simplicity, the following sample does not include code that frees allocated handles. For an example of how to free handles, see <link xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</link>.</para>
      </content>
    </description>
    <code>// SQLFreeStmt.cpp
// compile with: user32.lib odbc32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;

int main() {
   // declare and initialize the environment, connection, statement handles
   SQLHENV henv = NULL;   // Environment   
   SQLHDBC hdbc = NULL;   // Connection handle
   SQLHSTMT hstmt = NULL;   // Statement handle

   SQLRETURN retCode;
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle
   SQLCHAR connStrbuffer[1024];
   SQLSMALLINT connStrBufferLen;
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &amp;connStrBufferLen, SQL_DRIVER_PROMPT);
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);
}</code>
  </codeExample>
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
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink>
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
              <para>Closing a cursor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="05b0a054-e28d-4e16-b5b0-07418486b372">SQLCloseCursor Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Freeing a handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</legacyLink>
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
</relatedTopics>
</developerReferenceWithSyntaxDocument>