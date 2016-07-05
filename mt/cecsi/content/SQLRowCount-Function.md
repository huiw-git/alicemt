---
title: SQLRowCount Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLRowCount
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
translation.priority.ht: 
  - en-gb
---
# SQLRowCount Function
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
          <legacyBold>SQLRowCount</legacyBold> returns the number of rows affected by an <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>DELETE</legacyBold> statement; an SQL_ADD, SQL_UPDATE_BY_BOOKMARK, or SQL_DELETE_BY_BOOKMARK operation in <legacyBold>SQLBulkOperations</legacyBold>; or an SQL_UPDATE or SQL_DELETE operation in <legacyBold>SQLSetPos</legacyBold>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLRowCount</legacyBold>(
      SQLHSTMT   <parameterReference>StatementHandle</parameterReference>,
      SQLLEN *   <parameterReference>RowCountPtr</parameterReference>);</legacySyntax>
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
          <legacyItalic>RowCountPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Points to a buffer in which to return a row count. For <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, and <legacyBold>DELETE</legacyBold> statements, for the SQL_ADD, SQL_UPDATE_BY_BOOKMARK, and SQL_DELETE_BY_BOOKMARK operations in <legacyBold>SQLBulkOperations</legacyBold>, and for the SQL_UPDATE or SQL_DELETE operations in <legacyBold>SQLSetPos</legacyBold>, the value returned in *<legacyItalic>RowCountPtr</legacyItalic> is either the number of rows affected by the request or –1 if the number of affected rows is not available. </para>
          <para>When <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLSetPos, or SQLMoreResults</legacyBold> is called, the SQL_DIAG_ROW_COUNT field of the diagnostic data structure is set to the row count, and the row count is cached in an implementation-dependent way. <legacyBold>SQLRowCount</legacyBold> returns the cached row count value. The cached row count value is valid until the statement handle is set back to the prepared or allocated state, the statement is reexecuted, or <legacyBold>SQLCloseCursor</legacyBold> is called. Note that if a function has been called since the SQL_DIAG_ROW_COUNT field was set, the value returned by <legacyBold>SQLRowCount </legacyBold>might be different from the value in the SQL_DIAG_ROW_COUNT field because the SQL_DIAG_ROW_COUNT field is reset to 0 by any function call.   </para>
          <para>For other statements and functions, the driver may define the value returned in *<legacyItalic>RowCountPtr</legacyItalic>. For example, some data sources may be able to return the number of rows returned by a <legacyBold>SELECT</legacyBold> statement or a catalog function before fetching the rows. </para>
          <alert class="note">
            <para>Many data sources cannot return the number of rows in a result set before fetching them; for maximum interoperability, applications should not rely on this behavior. </para>
          </alert>
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
      <para>When <legacyBold>SQLRowCount </legacyBold>returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLRowCount</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLRowCount</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) The function was called prior to calling <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> for the <legacyItalic>StatementHandle</legacyItalic>.</para>
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
      <para>If the last SQL statement executed on the statement handle was not an <legacyBold>UPDATE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>DELETE</legacyBold> statement or if the <legacyItalic>Operation</legacyItalic> argument in the previous call to <legacyBold>SQLBulkOperations</legacyBold> was not SQL_ADD, SQL_UPDATE_BY_BOOKMARK, or SQL_DELETE_BY_BOOKMARK, or if the <legacyItalic>Operation</legacyItalic> argument in the previous call to <legacyBold>SQLSetPos</legacyBold> was not SQL_UPDATE or SQL_DELETE, the value of *<legacyItalic>RowCountPtr </legacyItalic>is driver-defined. For more information, see <legacyLink xlink:href="1e56297d-a786-415e-b66d-b42d1b2a8d45">Determining the Number of Affected Rows</legacyLink>.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>