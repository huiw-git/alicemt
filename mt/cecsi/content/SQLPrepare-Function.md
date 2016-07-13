---
title: SQLPrepare Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLPrepare
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLPrepare Function
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
          <legacyBold>SQLPrepare</legacyBold> prepares an SQL string for execution.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLPrepare</legacyBold>(
     SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *     <parameterReference>StatementText</parameterReference>,
     SQLINTEGER    <parameterReference>TextLength</parameterReference>);</legacySyntax>
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
          <legacyItalic>StatementText</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] SQL text string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TextLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>StatementText</legacyItalic> in characters.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLPrepare</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLPrepare </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>Option value changed</para>
            </TD>
            <TD>
              <para>A specified statement attribute was invalid because of implementation working conditions, so a similar value was temporarily substituted. (<legacyBold>SQLGetStmtAttr</legacyBold> can be called to determine what the temporarily substituted value is.) The substitute value is valid for the <legacyItalic>StatementHandle</legacyItalic> until the cursor is closed. The statement attributes that can be changed are: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR</para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>21S01</para>
            </TD>
            <TD>
              <para>Insert value list does not match column list</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>INSERT</legacyBold> statement, and the number of values to be inserted did not match the degree of the derived table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>21S02</para>
            </TD>
            <TD>
              <para>Degree of derived table does not match column list</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE VIEW</legacyBold> statement, and the number of names specified is not the same degree as the derived table defined by the query specification.</para>
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
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a literal or parameter, and the value was incompatible with the data type of the associated table column.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22019</para>
            </TD>
            <TD>
              <para>Invalid escape character</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>StatementText</legacyItalic> contained a <legacyBold>LIKE</legacyBold> predicate with an <legacyBold>ESCAPE</legacyBold> in the <legacyBold>WHERE</legacyBold> clause, and the length of the escape character following <legacyBold>ESCAPE</legacyBold> was not equal to 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22025</para>
            </TD>
            <TD>
              <para>Invalid escape sequence</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>StatementText</legacyItalic> contained "<legacyBold>LIKE</legacyBold> <legacyItalic>pattern value</legacyItalic> <legacyBold>ESCAPE</legacyBold> <legacyItalic>escape character</legacyItalic>" in the <legacyBold>WHERE</legacyBold> clause, and the character following the escape character in the pattern value was neither "%" nor "_".</para>
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
              <para>(DM) A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called.</para>
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, but <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had not been called.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>34000</para>
            </TD>
            <TD>
              <para>Invalid cursor name</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a positioned <legacyBold>DELETE</legacyBold> or a positioned <legacyBold>UPDATE</legacyBold>, and the cursor referenced by the statement being prepared was not open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3D000</para>
            </TD>
            <TD>
              <para>Invalid catalog name</para>
            </TD>
            <TD>
              <para>The catalog name specified in <legacyItalic>StatementText</legacyItalic> was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3F000</para>
            </TD>
            <TD>
              <para>Invalid schema name</para>
            </TD>
            <TD>
              <para>The schema name specified in <legacyItalic>StatementText</legacyItalic> was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42000</para>
            </TD>
            <TD>
              <para>Syntax error or access violation</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that was not preparable or contained a syntax error.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a statement for which the user did not have the required privileges.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S01</para>
            </TD>
            <TD>
              <para>Base table or view already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> or <legacyBold>CREATE VIEW</legacyBold> statement, and the table name or view name specified already exists.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S02</para>
            </TD>
            <TD>
              <para>Base table or view not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DROP TABLE</legacyBold> or a <legacyBold>DROP VIEW</legacyBold> statement, and the specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>ALTER TABLE</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE VIEW</legacyBold> statement, and a table name or view name defined by the query specification did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>GRANT</legacyBold> or <legacyBold>REVOKE</legacyBold> statement, and the specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>SELECT</legacyBold> statement, and a specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DELETE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>UPDATE</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> statement, and a table specified in a constraint (referencing a table other than the one being created) did not exist.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S11</para>
            </TD>
            <TD>
              <para>Index already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and the specified index name already existed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S12</para>
            </TD>
            <TD>
              <para>Index not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DROP INDEX</legacyBold> statement, and the specified index name did not exist.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S21</para>
            </TD>
            <TD>
              <para>Column already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>ALTER TABLE</legacyBold> statement, and the column specified in the <legacyBold>ADD</legacyBold> clause is not unique or identifies an existing column in the base table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S22</para>
            </TD>
            <TD>
              <para>Column not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and one or more of the column names specified in the column list did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>GRANT</legacyBold> or <legacyBold>REVOKE</legacyBold> statement, and a specified column name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>SELECT</legacyBold>, <legacyBold>DELETE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>UPDATE</legacyBold> statement, and a specified column name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> statement, and a column specified in a constraint (referencing a table other than the one being created) did not exist.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution,<legacyBold> SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>, and then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
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
              <para>(DM) <legacyItalic>StatementText</legacyItalic> was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLPrepare</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
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
              <para>HY090</para>
            </TD>
            <TD>
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>TextLength</legacyItalic> was less than or equal to 0 but not equal to SQL_NTS. </para>
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
              <para>The concurrency setting was invalid for the type of cursor defined.</para>
              <para>The SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_VARIABLE, and the SQL_ATTR_CURSOR_TYPE statement attribute was set to a cursor type for which the driver does not support bookmarks.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT00</para>
            </TD>
            <TD>
              <para>Timeout expired</para>
            </TD>
            <TD>
              <para>The timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtAttr</legacyBold>, SQL_ATTR_QUERY_TIMEOUT.</para>
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
      <para>The application calls <legacyBold>SQLPrepare</legacyBold> to send an SQL statement to the data source for preparation. For more information about prepared execution, see <legacyLink xlink:href="f08c8a98-31ee-48b2-9dbf-6f31c2166dbb">Prepared Execution</legacyLink>. The application can include one or more parameter markers in the SQL statement. To include a parameter marker, the application embeds a question mark (?) into the SQL string at the appropriate position. For information about parameters, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>.</para>
      <alert class="note">
        <para>If an application uses <legacyBold>SQLPrepare</legacyBold> to prepare and <legacyBold>SQLExecute</legacyBold> to submit a <legacyBold>COMMIT</legacyBold> or <legacyBold>ROLLBACK</legacyBold> statement, it will not be interoperable between DBMS products. To commit or roll back a transaction, call <legacyBold>SQLEndTran</legacyBold>.</para>
      </alert>
      <para>The driver can modify the statement to use the form of SQL used by the data source and then submit it to the data source for preparation. In particular, the driver modifies the escape sequences used to define SQL syntax for certain features. (For a description of SQL statement grammar, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink> and <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>.) For the driver, a statement handle is similar to a statement identifier in embedded SQL code. If the data source supports statement identifiers, the driver can send a statement identifier and parameter values to the data source.</para>
      <para>After a statement is prepared, the application uses the statement handle to refer to the statement in later function calls. The prepared statement associated with the statement handle can be re-executed by calling <legacyBold>SQLExecute</legacyBold> until the application frees the statement with a call to <legacyBold>SQLFreeStmt</legacyBold> with the SQL_DROP option or until the statement handle is used in a call to <legacyBold>SQLPrepare</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or one of the catalog functions (<legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLTables</legacyBold>, and so on). Once the application prepares a statement, it can request information about the format of the result set. For some implementations, calling <legacyBold>SQLDescribeCol</legacyBold> or <legacyBold>SQLDescribeParam</legacyBold> after <legacyBold>SQLPrepare</legacyBold> might not be as efficient as calling the function after <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>.</para>
      <para>Some drivers cannot return syntax errors or access violations when the application calls <legacyBold>SQLPrepare</legacyBold>. A driver can handle syntax errors and access violations, only syntax errors, or neither syntax errors nor access violations. Therefore, an application must be able to handle these conditions when calling subsequent related functions such as <legacyBold>SQLNumResultCols</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLColAttribute</legacyBold>, and <legacyBold>SQLExecute</legacyBold>.</para>
      <para>Depending on the capabilities of the driver and data source, parameter information (such as data types) might be checked when the statement is prepared (if all parameters have been bound) or when it is executed (if all parameters have not been bound). For maximum interoperability, an application should unbind all parameters that applied to an old SQL statement before preparing a new SQL statement on the same statement. This prevents errors that are due to old parameter information being applied to the new statement.</para>
      <alert class="important">
        <para>Committing a transaction, either by explicitly calling <legacyBold>SQLEndTran</legacyBold> or by working in autocommit mode, can cause the data source to delete the access plans for all statements on a connection. For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR information types in <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> and <legacyLink xlink:href="523e22a2-7b53-4c25-97c1-ef0284aec76e">Effect of Transactions on Cursors and Prepared Statements</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>, <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>, and <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>.</para>
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
              <para>Allocating a statement handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Binding a buffer to a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
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
              <para>Executing a commit or rollback operation</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran Function</legacyLink>
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
              <para>Returning the number of rows affected by a statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="61e00a8a-9b3b-45b9-b397-7fe818822416">SQLRowCount Function</legacyLink>
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