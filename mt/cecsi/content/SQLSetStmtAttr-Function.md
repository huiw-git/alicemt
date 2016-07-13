---
title: SQLSetStmtAttr Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetStmtAttr
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 7abc5260-733a-48d4-9974-2d1a6a9ea5f6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtAttr Function
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
          <legacyBold>SQLSetStmtAttr</legacyBold> sets attributes related to a statement.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3<legacyItalic>.x</legacyItalic> application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetStmtAttr</legacyBold>(
     SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
     SQLINTEGER    <parameterReference>Attribute</parameterReference>,
     SQLPOINTER    <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER    <parameterReference>StringLength</parameterReference>);</legacySyntax>
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
          <legacyItalic>Attribute</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Option to set, listed in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Value to be associated with <legacyItalic>Attribute</legacyItalic>. Depending on the value of <legacyItalic>Attribute</legacyItalic>, <legacyItalic>ValuePtr</legacyItalic> will be one of the following:</para>
          <list class="bullet">
            <listItem>
              <para>An ODBC descriptor handle.</para>
            </listItem>
            <listItem>
              <para>A SQLUINTEGER value.</para>
            </listItem>
            <listItem>
              <para>A SQLULEN value.</para>
            </listItem>
            <listItem>
              <para>A pointer to one of the following:</para>
              <list class="bullet">
                <listItem>
                  <para>A null-terminated character string.</para>
                </listItem>
                <listItem>
                  <para>A binary buffer.</para>
                </listItem>
                <listItem>
                  <para>A value or array of type SQLLEN, SQLULEN, or SQLUSMALLINT.</para>
                </listItem>
                <listItem>
                  <para>A driver-defined value.</para>
                </listItem>
              </list>
            </listItem>
          </list>
          <para>If the <legacyItalic>Attribute</legacyItalic> argument is a driver-specific value, <legacyItalic>ValuePtr</legacyItalic> may be a signed integer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>StringLength</legacyItalic> is ignored.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is a driver-defined attribute, the application indicates the nature of the attribute to the Driver Manager by setting the <legacyItalic>StringLength</legacyItalic> argument. <legacyItalic>StringLength</legacyItalic> can have the following values: </para>
        </definition>
      </definitionTable>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a character string, then <legacyItalic>StringLength</legacyItalic> is the length of the string or SQL_NTS.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a binary buffer, then the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>StringLength</legacyItalic>. This places a negative value in <legacyItalic>StringLength</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a value other than a character string or a binary string, then <legacyItalic>StringLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>ValuePtr</legacyItalic> contains a fixed-length value, then <legacyItalic>StringLength</legacyItalic> is either SQL_IS_INTEGER or SQL_IS_UINTEGER, as appropriate.</para>
        </listItem>
      </list>
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
      <para>When <legacyBold>SQLSetStmtAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetStmtAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The driver did not support the value specified in <legacyItalic>ValuePtr</legacyItalic>, or the value specified in <legacyItalic>ValuePtr</legacyItalic> was invalid because of implementation working conditions, so the driver substituted a similar value. (<legacyBold>SQLGetStmtAttr</legacyBold> can be called to determine the temporarily substituted value.) The substitute value is valid for the <legacyItalic>StatementHandle</legacyItalic> until the cursor is closed, at which point the statement attribute reverts to its previous value. The statement attributes that can be changed are: </para>
              <para>SQL_ ATTR_CONCURRENCY SQL_ ATTR_CURSOR_TYPE SQL_ ATTR_KEYSET_SIZE SQL_ ATTR_MAX_LENGTH SQL_ ATTR_MAX_ROWS SQL_ ATTR_QUERY_TIMEOUT  SQL_ATTR_ROW_ARRAY_SIZE SQL_ ATTR_SIMULATE_CURSOR </para>
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
              <para>24000</para>
            </TD>
            <TD>
              <para>Invalid cursor state</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Attribute</legacyItalic> was SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, or SQL_ATTR_USE_BOOKMARKS, and the cursor was open.</para>
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
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid use of null pointer</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Attribute</legacyItalic> argument identified a statement attribute that required a string attribute, and the <legacyItalic>ValuePtr </legacyItalic>argument was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLSetStmtAttr</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY011</para>
            </TD>
            <TD>
              <para>Attribute cannot be set now</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Attribute</legacyItalic> was SQL_ATTR_CONCURRENCY, SQL_ ATTR_CURSOR_TYPE, SQL_ ATTR_SIMULATE_CURSOR, or SQL_ ATTR_USE_BOOKMARKS, and the statement was prepared.</para>
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
              <para>HY017</para>
            </TD>
            <TD>
              <para>Invalid use of an automatically allocated descriptor handle</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_IMP_ROW_DESC or SQL_ATTR_IMP_PARAM_DESC.</para>
              <para>(DM) The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC, and the value in <legacyItalic>ValuePtr</legacyItalic> was an implicitly allocated descriptor handle other than the handle originally allocated for the ARD or APD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY024</para>
            </TD>
            <TD>
              <para>Invalid attribute value</para>
            </TD>
            <TD>
              <para>Given the specified <legacyItalic>Attribute</legacyItalic> value, an invalid value was specified in <legacyItalic>ValuePtr</legacyItalic>. (The Driver Manager returns this SQLSTATE only for connection and statement attributes that accept a discrete set of values, such as SQL_ATTR_ACCESS_MODE or SQL_ ATTR_ASYNC_ENABLE. For all other connection and statement attributes, the driver must verify the value specified in <legacyItalic>ValuePtr</legacyItalic>.)</para>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC, and <legacyItalic>ValuePtr</legacyItalic> was an explicitly allocated descriptor handle that is not on the same connection as the <legacyItalic>StatementHandle</legacyItalic> argument.</para>
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
              <para>(DM) <legacyItalic>*ValuePtr</legacyItalic> is a character string, and the <legacyItalic>StringLength</legacyItalic> argument was less than 0 but was not SQL_NTS.</para>
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
              <para>(DM) The value specified for the argument <legacyItalic>Attribute</legacyItalic> was not valid for the version of ODBC supported by the driver.</para>
              <para>(DM) The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a read-only attribute.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC statement attribute for the version of ODBC supported by the driver but was not supported by the driver.</para>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ASYNC_ENABLE, and a call to <legacyBold>SQLGetInfo</legacyBold> with an <legacyItalic>InfoType</legacyItalic> of SQL_ASYNC_MODE returns SQL_AM_CONNECTION.</para>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ENABLE_AUTO_IPD, and the value of the connection attribute SQL_ATTR_AUTO_IPD was SQL_FALSE.</para>
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
              <para>S1118</para>
            </TD>
            <TD>
              <para>Driver does not support asynchronous notification</para>
            </TD>
            <TD>
              <para>If calling <languageKeyword>SQLSetStmtAttr</languageKeyword> to set SQL_ATTR_ASYNC_STMT_EVENT; asynchronous notification is not supported by the driver.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>Statement attributes for a statement remain in effect until they are changed by another call to <legacyBold>SQLSetStmtAttr</legacyBold> or until the statement is dropped by calling <legacyBold>SQLFreeHandle</legacyBold>. Calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE, SQL_UNBIND, or SQL_RESET_PARAMS option does not reset statement attributes.</para>
      <para>Some statement attributes support substitution of a similar value if the data source does not support the value specified in <legacyItalic>ValuePtr</legacyItalic>. In such cases, the driver returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value changed). For example, if <legacyItalic>Attribute</legacyItalic> is SQL_ATTR_CONCURRENCY and <legacyItalic>ValuePtr</legacyItalic> is SQL_CONCUR_ROWVER, and if the data source does not support this, the driver substitutes SQL_CONCUR_VALUES and returns SQL_SUCCESS_WITH_INFO. To determine the substituted value, an application calls <legacyBold>SQLGetStmtAttr</legacyBold>.</para>
      <para>The format of information set with <legacyItalic>ValuePtr</legacyItalic> depends on the specified <legacyItalic>Attribute</legacyItalic>. <legacyBold>SQLSetStmtAttr</legacyBold> accepts attribute information in one of two different formats: a character string or an integer value. The format of each is noted in the attribute's description. This format applies to the information returned for each attribute in <legacyBold>SQLGetStmtAttr</legacyBold>. Character strings pointed to by the <legacyItalic>ValuePtr</legacyItalic> argument of <legacyBold>SQLSetStmtAttr</legacyBold> have a length of <legacyItalic>StringLength</legacyItalic>.</para>
      <alert class="note">
        <para>The ability to set statement attributes at the connection level by calling <legacyBold>SQLSetConnectAttr</legacyBold> has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3<legacyItalic>.x</legacyItalic> applications should never set statement attributes at the connection level. ODBC 3<legacyItalic>.x</legacyItalic> statement attributes cannot be set at the connection level, with the exception of the SQL_ATTR_METADATA_ID and SQL_ATTR_ASYNC_ENABLE attributes, which are both connection attributes and statement attributes, and can be set at either the connection level or the statement level.</para>
      </alert>
      <alert class="note">
        <para>ODBC 3<legacyItalic>.x</legacyItalic> drivers need only support this functionality if they should work with ODBC 2<legacyItalic>.x</legacyItalic> applications that set ODBC 2<legacyItalic>.x</legacyItalic> statement options at the connection level. For more information, see "Setting Statement Options on the Connection Level" under <legacyLink xlink:href="a1b325cf-0c42-41c1-b141-b5a4fee7e708">SQLSetConnectOption Mapping</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Statement Attributes That Set Descriptor Fields</title>
    <content>
      <para>Many statement attributes correspond to a header field of a descriptor. Setting these attributes actually results in the setting of the descriptor fields. Setting fields by a call to <legacyBold>SQLSetStmtAttr</legacyBold> rather than to <legacyBold>SQLSetDescField</legacyBold> has the advantage that a descriptor handle does not have to be obtained for the function call.</para>
      <alert class="caution">
        <para>Calling <legacyBold>SQLSetStmtAttr</legacyBold> for one statement can affect other statements. This occurs when the APD or ARD associated with the statement is explicitly allocated and is also associated with other statements. Because <legacyBold>SQLSetStmtAttr</legacyBold> modifies the APD or ARD, the modifications apply to all statements with which this descriptor is associated. If this is not the required behavior, the application should dissociate this descriptor from the other statements (by calling <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_ATTR_APP_ROW_DESC or SQL_ATTR_APP_PARAM_DESC field to a different descriptor handle) before calling <legacyBold>SQLSetStmtAttr</legacyBold> again.</para>
      </alert>
      <para>When a descriptor field is set as a result of the corresponding statement attribute being set, the field is set only for the applicable descriptors that are currently associated with the statement identified by the <legacyItalic>StatementHandle</legacyItalic> argument, and the attribute setting does not affect any descriptors that may be associated with that statement in the future. When a descriptor field that is also a statement attribute is set by a call to <legacyBold>SQLSetDescField</legacyBold>, the corresponding statement attribute is set. If an explicitly allocated descriptor is dissociated from a statement, a statement attribute that corresponds to a header field will revert to the value of the field in the implicitly allocated descriptor.</para>
      <para>When a statement is allocated (see <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle</legacyLink>), four descriptor handles are automatically allocated and associated with the statement. Explicitly allocated descriptor handles can be associated with the statement by calling <legacyBold>SQLAllocHandle</legacyBold> with an <legacyItalic>fHandleType</legacyItalic> of SQL_HANDLE_DESC to allocate a descriptor handle and then calling <legacyBold>SQLSetStmtAttr</legacyBold> to associate the descriptor handle with the statement. </para>
      <para>The statement attributes in the following table correspond to descriptor header fields.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Statement attribute</para>
            </TD>
            <TD>
              <para>Header field</para>
            </TD>
            <TD>
              <para>Desc.</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>APD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQL_DESC_BIND_TYPE</para>
            </TD>
            <TD>
              <para>APD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_STATUS_PTR</para>
            </TD>
            <TD>
              <para>APD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_STATUS_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_STATUS_PTR</para>
            </TD>
            <TD>
              <para>IPD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAMS_PROCESSED_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
            </TD>
            <TD>
              <para>IPD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAMSET_SIZE</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_SIZE</para>
            </TD>
            <TD>
              <para>APD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_SIZE</para>
            </TD>
            <TD>
              <para>ARD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>ARD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQL_DESC_BIND_TYPE</para>
            </TD>
            <TD>
              <para>ARD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_OPERATION_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_STATUS_PTR</para>
            </TD>
            <TD>
              <para>ARD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_STATUS_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ARRAY_STATUS_PTR</para>
            </TD>
            <TD>
              <para>IRD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
            </TD>
            <TD>
              <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
            </TD>
            <TD>
              <para>IRD</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Statement Attributes</title>
    <content>
      <para>The currently defined attributes and the version of ODBC in which they were introduced are shown in the following table; it is expected that more attributes will be defined by drivers to take advantage of different data sources. A range of attributes is reserved by ODBC; driver developers must reserve values for their own driver-specific use from Open Group. For more information, see <legacyLink xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</legacyLink>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Attribute</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>ValuePtr</legacyItalic> contents</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_APP_PARAM_DESC (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>The handle to the APD for subsequent calls to <legacyBold>SQLExecute</legacyBold> and <legacyBold>SQLExecDirect</legacyBold> on the statement handle. The initial value of this attribute is the descriptor implicitly allocated when the statement was initially allocated. If the value of this attribute is set to SQL_NULL_DESC or the handle originally allocated for the descriptor, an explicitly allocated APD handle that was previously associated with the statement handle is dissociated from it and the statement handle reverts to the implicitly allocated APD handle. </para>
              <para>This attribute cannot be set to a descriptor handle that was implicitly allocated for another statement or to another descriptor handle that was implicitly set on the same statement; implicitly allocated descriptor handles cannot be associated with more than one statement or descriptor handle.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_APP_ROW_DESC (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>The handle to the ARD for subsequent fetches on the statement handle. The initial value of this attribute is the descriptor implicitly allocated when the statement was initially allocated. If the value of this attribute is set to SQL_NULL_DESC or the handle originally allocated for the descriptor, an explicitly allocated ARD handle that was previously associated with the statement handle is dissociated from it and the statement handle reverts to the implicitly allocated ARD handle. </para>
              <para>This attribute cannot be set to a descriptor handle that was implicitly allocated for another statement or to another descriptor handle that was implicitly set on the same statement; implicitly allocated descriptor handles cannot be associated with more than one statement or descriptor handle.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_ENABLE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A SQLULEN value that specifies whether a function called with the specified statement is executed asynchronously:</para>
              <para>SQL_ASYNC_ENABLE_OFF = Disable statement level asynchronous execution support (the default).</para>
              <para>SQL_ASYNC_ENABLE_ON = Enable statement level asynchronous execution support.</para>
              <para>For more information, see <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>.</para>
              <para>For drivers with statement level asynchronous execution support, the statement attribute SQL_ATTR_ASYNC_ENABLE is read only. Its value is the same as the value of the connection level attribute with the same name at the time the statement handle was allocated. </para>
              <para>Calling <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ASYNC_ENABLE when the SQL_ASYNC_MODE <legacyItalic>InfoType</legacyItalic> returns SQL_AM_CONNECTION returns SQLSTATE HYC00 (Optional feature not implemented). For more information, see <link xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</link> for more information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_STMT_EVENT (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value that is an event handle.</para>
              <para>Notification of completion of asynchronous functions is enabled by calling <languageKeyword>SQLSetStmtAttr</languageKeyword> to set the <languageKeyword>SQL_ATTR_ASYNC_STMT_EVENT</languageKeyword> attribute and specify the event handle.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_STMT_PCALLBACK (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER to the asynchronous callback function.</para>
              <para>Only the Driver Manager can call a driver’s <languageKeyword>SQLSetStmtAttr</languageKeyword> function with this attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_STMT_PCONTEXT (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER to the context structure</para>
              <para>Only the Driver Manager can call a driver’s <languageKeyword>SQLSetStmtAttr</languageKeyword> function with this attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CONCURRENCY (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the cursor concurrency:</para>
              <para>SQL_CONCUR_READ_ONLY = Cursor is read-only. No updates are allowed.</para>
              <para>SQL_CONCUR_LOCK = Cursor uses the lowest level of locking sufficient to ensure that the row can be updated.</para>
              <para>SQL_CONCUR_ROWVER = Cursor uses optimistic concurrency control, comparing row versions such as SQLBase ROWID or Sybase TIMESTAMP.</para>
              <para>SQL_CONCUR_VALUES = Cursor uses optimistic concurrency control, comparing values.</para>
              <para>The default value for SQL_ATTR_CONCURRENCY is SQL_CONCUR_READ_ONLY.</para>
              <para>This attribute cannot be specified for an open cursor. For more information, see <legacyLink xlink:href="46762ae5-17dd-4777-968e-58156f470fe1">Concurrency Types</legacyLink>.</para>
              <para>If the SQL_ATTR_CURSOR_TYPE <legacyItalic>Attribute</legacyItalic> is changed to a type that does not support the current value of SQL_ATTR_CONCURRENCY, the value of SQL_ATTR_CONCURRENCY will be changed at execution time, and a warning issued when <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLPrepare</legacyBold> is called.</para>
              <para>If the driver supports the <legacyBold>SELECT FOR UPDATE</legacyBold> statement and such a statement is executed while the value of SQL_ATTR_CONCURRENCY is set to SQL_CONCUR_READ_ONLY, an error will be returned. If the value of SQL_ATTR_CONCURRENCY is changed to a value that the driver supports for some value of SQL_ATTR_CURSOR_TYPE but not for the current value of SQL_ATTR_CURSOR_TYPE, the value of SQL_ATTR_CURSOR_TYPE will be changed at execution time and SQLSTATE 01S02 (Option value changed) is issued when <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLPrepare</legacyBold> is called.</para>
              <para>If the specified concurrency is not supported by the data source, the driver substitutes a different concurrency and returns SQLSTATE 01S02 (Option value changed). For SQL_CONCUR_VALUES, the driver substitutes SQL_CONCUR_ROWVER, and vice versa. For SQL_CONCUR_LOCK, the driver substitutes, in order, SQL_CONCUR_ROWVER or SQL_CONCUR_VALUES. The validity of the substituted value is not checked until execution time.</para>
              <para>For more information about the relationship between SQL_ATTR_CONCURRENCY and the other cursor attributes, see <legacyLink xlink:href="6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b">Cursor Characteristics and Cursor Type</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURSOR_SCROLLABLE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the level of support that the application requires. Setting this attribute affects subsequent calls to <legacyBold>SQLExecDirect</legacyBold> and <legacyBold>SQLExecute</legacyBold>.</para>
              <para>SQL_NONSCROLLABLE = Scrollable cursors are not required on the statement handle. If the application calls <legacyBold>SQLFetchScroll</legacyBold> on this handle, the only valid value of <legacyItalic>FetchOrientation</legacyItalic> is SQL_FETCH_NEXT. This is the default.</para>
              <para>SQL_SCROLLABLE = Scrollable cursors are required on the statement handle. When calling <legacyBold>SQLFetchScroll</legacyBold>, the application may specify any valid value of <legacyItalic>FetchOrientation</legacyItalic>, achieving cursor positioning in modes other than the sequential mode. </para>
              <para>For more information about scrollable cursors, see <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>. For more information about the relationship between SQL_ATTR_CURSOR_SCROLLABLE and the other cursor attributes, see <legacyLink xlink:href="6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b">Cursor Characteristics and Cursor Type</legacyLink></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURSOR_SENSITIVITY (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies whether cursors on the statement handle make visible the changes made to a result set by another cursor. Setting this attribute affects subsequent calls to <legacyBold>SQLExecDirect</legacyBold> and <legacyBold>SQLExecute</legacyBold>. An application can read back the value of this attribute to obtain its initial state or its state as most recently set by the application.</para>
              <para>SQL_UNSPECIFIED = It is unspecified what the cursor type is and whether cursors on the statement handle make visible the changes made to a result set by another cursor. Cursors on the statement handle may make visible none, some, or all such changes. This is the default.</para>
              <para>SQL_INSENSITIVE = All cursors on the statement handle show the result set without reflecting any changes made to it by any other cursor. Insensitive cursors are read-only. This corresponds to a static cursor, which has a concurrency that is read-only.</para>
              <para>SQL_SENSITIVE = All cursors on the statement handle make visible all changes made to a result set by another cursor. </para>
              <para>For more information about the relationship between SQL_ATTR_CURSOR_SENSITIVITY and the other cursor attributes, see <legacyLink xlink:href="6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b">Cursor Characteristics and Cursor Type</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURSOR_TYPE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the cursor type:</para>
              <para>SQL_CURSOR_FORWARD_ONLY = The cursor only scrolls forward.</para>
              <para>SQL_CURSOR_STATIC = The data in the result set is static.</para>
              <para>SQL_CURSOR_KEYSET_DRIVEN = The driver saves and uses the keys for the number of rows specified in the SQL_ATTR_KEYSET_SIZE statement attribute.</para>
              <para>SQL_CURSOR_DYNAMIC = The driver saves and uses only the keys for the rows in the rowset.</para>
              <para>The default value is SQL_CURSOR_FORWARD_ONLY. This attribute cannot be specified after the SQL statement has been prepared.</para>
              <para>If the specified cursor type is not supported by the data source, the driver substitutes a different cursor type and returns SQLSTATE 01S02 (Option value changed). For a mixed or dynamic cursor, the driver substitutes, in order, a keyset-driven or static cursor. For a keyset-driven cursor, the driver substitutes a static cursor. </para>
              <para>For more information about scrollable cursor types, see <legacyLink xlink:href="dbd32576-0453-4e90-ae45-1a81cee8259d">Scrollable Cursor Types</legacyLink>. For more information about the relationship between SQL_ATTR_CURSOR_TYPE and the other cursor attributes, see <legacyLink xlink:href="6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b">Cursor Characteristics and Cursor Type</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ENABLE_AUTO_IPD (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies whether automatic population of the IPD is performed:</para>
              <para>SQL_TRUE = Turns on automatic population of the IPD after a call to <legacyBold>SQLPrepare</legacyBold>. SQL_FALSE = Turns off automatic population of the IPD after a call to <legacyBold>SQLPrepare</legacyBold>. (An application can still obtain IPD field information by calling <legacyBold>SQLDescribeParam</legacyBold>, if supported.) The default value of the statement attribute SQL_ATTR_ENABLE_AUTO_IPD is SQL_FALSE. For more information, see <legacyLink xlink:href="1184a7d8-d557-4140-843b-6633ae6deacc">Automatic Population of the IPD</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_FETCH_BOOKMARK_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A SQLLEN * that points to a binary bookmark value. When <legacyBold>SQLFetchScroll</legacyBold> is called with <legacyItalic>fFetchOrientation</legacyItalic> equal to SQL_FETCH_BOOKMARK, the driver picks up the bookmark value from this field. This field defaults to a null pointer. For more information, see <legacyLink xlink:href="4862f098-41a4-4bd2-894e-f71bb97f9bc0">Scrolling by Bookmark</legacyLink>.</para>
              <para>The value pointed to by this field is not used for delete by bookmark, update by bookmark, or fetch by bookmark operations in <legacyBold>SQLBulkOperations</legacyBold>, which use bookmarks cached in rowset buffers.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_IMP_PARAM_DESC (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>The handle to the IPD. The value of this attribute is the descriptor allocated when the statement was initially allocated. The application cannot set this attribute. </para>
              <para>This attribute can be retrieved by a call to <legacyBold>SQLGetStmtAttr</legacyBold> but not set by a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_IMP_ROW_DESC (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>The handle to the IRD. The value of this attribute is the descriptor allocated when the statement was initially allocated. The application cannot set this attribute. </para>
              <para>This attribute can be retrieved by a call to <legacyBold>SQLGetStmtAttr</legacyBold> but not set by a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_KEYSET_SIZE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN that specifies the number of rows in the keyset for a keyset-driven cursor. If the keyset size is 0 (the default), the cursor is fully keyset-driven. If the keyset size is greater than 0, the cursor is mixed (keyset-driven within the keyset and dynamic outside of the keyset). The default keyset size is 0. For more information about keyset-driven cursors, see <legacyLink xlink:href="01769f43-1d9c-4685-84fa-15a6465335e9">Keyset-Driven Cursors</legacyLink>.</para>
              <para>If the specified size exceeds the maximum keyset size, the driver substitutes that size and returns SQLSTATE 01S02 (Option value changed).</para>
              <para>
                <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> returns an error if the keyset size is greater than 0 and less than the rowset size.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_MAX_LENGTH (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the maximum amount of data that the driver returns from a character or binary column. If <legacyItalic>ValuePtr</legacyItalic> is less than the length of the available data, <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLGetData</legacyBold> truncates the data and returns SQL_SUCCESS. If <legacyItalic>ValuePtr</legacyItalic> is 0 (the default), the driver attempts to return all available data.</para>
              <para>If the specified length is less than the minimum amount of data that the data source can return or greater than the maximum amount of data that the data source can return, the driver substitutes that value and returns SQLSTATE 01S02 (Option value changed).</para>
              <para>The value of this attribute can be set on an open cursor; however, the setting might not take effect immediately, in which case the driver will return SQLSTATE 01S02 (Option value changed) and reset the attribute to its original value.</para>
              <para>This attribute is intended to reduce network traffic and should be supported only when the data source (as opposed to the driver) in a multiple-tier driver can implement it. This mechanism should not be used by applications to truncate data; to truncate data received, an application should specify the maximum buffer length in the <legacyItalic>BufferLength </legacyItalic>argument in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_MAX_ROWS (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value corresponding to the maximum number of rows to return to the application for a <legacyBold>SELECT</legacyBold> statement. If *<legacyItalic>ValuePtr</legacyItalic> equals 0 (the default), the driver returns all rows.</para>
              <para>This attribute is intended to reduce network traffic. Conceptually, it is applied when the result set is created and limits the result set to the first <legacyItalic>ValuePtr</legacyItalic> rows. If the number of rows in the result set is greater than <legacyItalic>ValuePtr</legacyItalic>, the result set is truncated. </para>
              <para>SQL_ATTR_MAX_ROWS applies to all result sets on the <legacyItalic>Statement</legacyItalic>, including those returned by catalog functions. SQL_ATTR_MAX_ROWS establishes a maximum for the value of the cursor row count.</para>
              <para>A driver should not emulate SQL_ATTR_MAX_ROWS behavior for <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> (if result set size limitations cannot be implemented at the data source) if it cannot guarantee that SQL_ATTR_MAX_ROWS will be implemented properly.</para>
              <para>It is driver-defined whether SQL_ATTR_MAX_ROWS applies to statements other than SELECT statements (such as catalog functions). </para>
              <para>The value of this attribute can be set on an open cursor; however, the setting might not take effect immediately, in which case the driver will return SQLSTATE 01S02 (Option value changed) and reset the attribute to its original value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_METADATA_ID (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that determines how the string arguments of catalog functions are treated.</para>
              <para>If SQL_TRUE, the string argument of catalog functions are treated as identifiers. The case is not significant. For nondelimited strings, the driver removes any trailing spaces and the string is folded to uppercase. For delimited strings, the driver removes any leading or trailing spaces and takes whatever is between the delimiters literally. If one of these arguments is set to a null pointer, the function returns SQL_ERROR and SQLSTATE HY009 (Invalid use of null pointer). </para>
              <para>If SQL_FALSE, the string arguments of catalog functions are not treated as identifiers. The case is significant. They can either contain a string search pattern or not, depending on the argument.</para>
              <para>The default value is SQL_FALSE.</para>
              <para>The <legacyItalic>TableType</legacyItalic> argument of <legacyBold>SQLTables</legacyBold>, which takes a list of values, is not affected by this attribute.</para>
              <para>SQL_ATTR_METADATA_ID can also be set on the connection level. (It and SQL_ATTR_ASYNC_ENABLE are the only statement attributes that are also connection attributes.)</para>
              <para>For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_NOSCAN (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that indicates whether the driver should scan SQL strings for escape sequences:</para>
              <para>SQL_NOSCAN_OFF = The driver scans SQL strings for escape sequences (the default).</para>
              <para>SQL_NOSCAN_ON = The driver does not scan SQL strings for escape sequences. Instead, the driver sends the statement directly to the data source.</para>
              <para>For more information, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN * value that points to an offset added to pointers to change binding of dynamic parameters. If this field is non-null, the driver dereferences the pointer, adds the dereferenced value to each of the deferred fields in the descriptor record (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR), and uses the new pointer values when binding. It is set to null by default.</para>
              <para>The bind offset is always added directly to the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields. If the offset is changed to a different value, the new value is still added directly to the value in the descriptor field. The new offset is not added to the field value plus any earlier offsets.</para>
              <para>For more information, see <legacyLink xlink:href="309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c">Parameter Binding Offsets</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_BIND_OFFSET_PTR field in the APD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_TYPE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that indicates the binding orientation to be used for dynamic parameters. </para>
              <para>This field is set to SQL_PARAM_BIND_BY_COLUMN (the default) to select column-wise binding. </para>
              <para>To select row-wise binding, this field is set to the length of the structure or an instance of a buffer that will be bound to a set of dynamic parameters. This length must include space for all of the bound parameters and any padding of the structure or buffer to ensure that when the address of a bound parameter is incremented with the specified length, the result will point to the beginning of the same parameter in the next set of parameters. When using the <legacyItalic>sizeof</legacyItalic> operator in ANSI C, this behavior is guaranteed.</para>
              <para>For more information, see <legacyLink xlink:href="037afe23-052d-4f3a-8aa7-45302b199ad0">Binding Arrays of Parameters</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ BIND_TYPE field in the APD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_OPERATION_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUSMALLINT * value that points to an array of SQLUSMALLINT values used to ignore a parameter during execution of an SQL statement. Each value is set to either SQL_PARAM_PROCEED (for the parameter to be executed) or SQL_PARAM_IGNORE (for the parameter to be ignored). </para>
              <para>A set of parameters can be ignored during processing by setting the status value in the array pointed to by SQL_DESC_ARRAY_STATUS_PTR in the APD to SQL_PARAM_IGNORE. A set of parameters is processed if its status value is set to SQL_PARAM_PROCEED or if no elements in the array are set.</para>
              <para>This statement attribute can be set to a null pointer, in which case the driver does not return parameter status values. This attribute can be set at any time, but the new value is not used until the next time <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> is called.</para>
              <para>This attribute is ignored when there is no bound parameter.</para>
              <para>For more information, see <legacyLink xlink:href="5a28be88-e171-4f5b-bf4d-543c4383c869">Using Arrays of Parameters</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_STATUS_PTR field in the APD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_STATUS_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUSMALLINT * value that points to an array of SQLUSMALLINT values containing status information for each row of parameter values after a call to <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. This field is required only if PARAMSET_SIZE is greater than 1. </para>
              <para>The status values can contain the following values:</para>
              <para>SQL_PARAM_SUCCESS: The SQL statement was successfully executed for this set of parameters.</para>
              <para>SQL_PARAM_SUCCESS_WITH_INFO: The SQL statement was successfully executed for this set of parameters; however, warning information is available in the diagnostics data structure.</para>
              <para>SQL_PARAM_ERROR: There was an error in processing this set of parameters. Additional error information is available in the diagnostics data structure.</para>
              <para>SQL_PARAM_UNUSED: This parameter set was unused, possibly due to the fact that some previous parameter set caused an error that aborted further processing, or because SQL_PARAM_IGNORE was set for that set of parameters in the array specified by the SQL_ATTR_PARAM_OPERATION_PTR.</para>
              <para>SQL_PARAM_DIAG_UNAVAILABLE: The driver treats arrays of parameters as a monolithic unit and so does not generate this level of error information. </para>
              <para>This statement attribute can be set to a null pointer, in which case the driver does not return parameter status values. This attribute can be set at any time, but the new value is not used until the next time <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> is called. Note that setting this attribute can affect the output parameter behavior implemented by the driver.</para>
              <para>For more information, see <legacyLink xlink:href="5a28be88-e171-4f5b-bf4d-543c4383c869">Using Arrays of Parameters</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_STATUS_PTR field in the IPD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAMS_PROCESSED_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN * record field that points to a buffer in which to return the number of sets of parameters that have been processed, including error sets. No number will be returned if this is a null pointer.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ROWS_PROCESSED_PTR field in the IPD header.</para>
              <para>If the call to <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> that fills in the buffer pointed to by this attribute does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined.</para>
              <para>For more information, see <legacyLink xlink:href="5a28be88-e171-4f5b-bf4d-543c4383c869">Using Arrays of Parameters</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAMSET_SIZE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the number of values for each parameter. If SQL_ATTR_PARAMSET_SIZE is greater than 1, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR of the APD point to arrays. The cardinality of each array is equal to the value of this field. </para>
              <para>This attribute is ignored when there is no bound parameter.</para>
              <para>For more information, see <legacyLink xlink:href="5a28be88-e171-4f5b-bf4d-543c4383c869">Using Arrays of Parameters</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_SIZE field in the APD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_QUERY_TIMEOUT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value corresponding to the number of seconds to wait for an SQL statement to execute before returning to the application. If <legacyItalic>ValuePtr</legacyItalic> is equal to 0 (default), there is no timeout.</para>
              <para>If the specified timeout exceeds the maximum timeout in the data source or is smaller than the minimum timeout, <legacyBold>SQLSetStmtAttr</legacyBold> substitutes that value and returns SQLSTATE 01S02 (Option value changed).</para>
              <para>Note that the application need not call <legacyBold>SQLCloseCursor</legacyBold> to reuse the statement if a <legacyBold>SELECT</legacyBold> statement timed out.</para>
              <para>The query timeout set in this statement attribute is valid in both synchronous and asynchronous modes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_RETRIEVE_DATA (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value:</para>
              <para>SQL_RD_ON = <legacyBold>SQLFetchScroll</legacyBold> and, in ODBC 3<legacyItalic>.x</legacyItalic>, <legacyBold>SQLFetch</legacyBold> retrieve data after it positions the cursor to the specified location. This is the default.</para>
              <para>SQL_RD_OFF = <legacyBold>SQLFetchScroll</legacyBold> and, in ODBC 3<legacyItalic>.x</legacyItalic>, <legacyBold>SQLFetch</legacyBold> do not retrieve data after it positions the cursor.</para>
              <para>By setting SQL_RETRIEVE_DATA to SQL_RD_OFF, an application can verify that a row exists or retrieve a bookmark for the row without incurring the overhead of retrieving rows. For more information, see <legacyLink xlink:href="c43764cb-5841-4b89-9dc0-984a7488b3c1">Scrolling and Fetching Rows</legacyLink>.</para>
              <para>The value of this attribute can be set on an open cursor; however, the setting might not take effect immediately, in which case the driver will return SQLSTATE 01S02 (Option value changed) and reset the attribute to its original value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_ARRAY_SIZE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies the number of rows returned by each call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. It is also the number of rows in a bookmark array used in a bulk bookmark operation in <legacyBold>SQLBulkOperations</legacyBold>. The default value is 1.</para>
              <para>If the specified rowset size exceeds the maximum rowset size supported by the data source, the driver substitutes that value and returns SQLSTATE 01S02 (Option value changed).</para>
              <para>For more information, see <legacyLink xlink:href="60366ae8-175c-456a-ae5e-bdd860786911">Rowset Size</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_SIZE field in the ARD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_BIND_OFFSET_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN * value that points to an offset added to pointers to change binding of column data. If this field is non-null, the driver dereferences the pointer, adds the dereferenced value to each of the deferred fields in the descriptor record (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR), and uses the new pointer values when binding. It is set to null by default.</para>
              <para>Setting this statement attribute sets the SQL_DESC_BIND_OFFSET_PTR field in the ARD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_BIND_TYPE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that sets the binding orientation to be used when <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> is called on the associated statement. Column-wise binding is selected by setting the value to SQL_BIND_BY_COLUMN. Row-wise binding is selected by setting the value to the length of a structure or an instance of a buffer into which result columns will be bound.</para>
              <para>If a length is specified, it must include space for all of the bound columns and any padding of the structure or buffer to ensure that when the address of a bound column is incremented with the specified length, the result will point to the beginning of the same column in the next row. When using the <legacyBold>sizeof</legacyBold> operator with structures or unions in ANSI C, this behavior is guaranteed.</para>
              <para>Column-wise binding is the default binding orientation for <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold>.</para>
              <para>For more information, see <legacyLink xlink:href="231beede-cdfa-4e28-8b10-2760b983250f">Binding Columns for Use with Block Cursors</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_BIND_TYPE field in the ARD header.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_NUMBER (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that is the number of the current row in the entire result set. If the number of the current row cannot be determined or there is no current row, the driver returns 0.</para>
              <para>This attribute can be retrieved by a call to <legacyBold>SQLGetStmtAttr</legacyBold> but not set by a call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_OPERATION_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUSMALLINT * value that points to an array of SQLUSMALLINT values used to ignore a row during a bulk operation using <legacyBold>SQLSetPos</legacyBold>. Each value is set to either SQL_ROW_PROCEED (for the row to be included in the bulk operation) or SQL_ROW_IGNORE (for the row to be excluded from the bulk operation). (Rows cannot be ignored by using this array during calls to <legacyBold>SQLBulkOperations</legacyBold>.)</para>
              <para>This statement attribute can be set to a null pointer, in which case the driver does not return row status values. This attribute can be set at any time, but the new value is not used until the next time <legacyBold>SQLSetPos</legacyBold> is called.</para>
              <para>For more information, see <legacyLink xlink:href="d83a8c2a-5aa8-4f19-947c-79a817167ee1">Updating Rows in the Rowset with SQLSetPos</legacyLink> and <legacyLink xlink:href="3117a47d-e179-4f76-89d0-656582f1c9bb">Deleting Rows in the Rowset with SQLSetPos</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_STATUS_PTR field in the ARD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROW_STATUS_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUSMALLINT * value that points to an array of SQLUSMALLINT values containing row status values after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. The array has as many elements as there are rows in the rowset. </para>
              <para>This statement attribute can be set to a null pointer, in which case the driver does not return row status values. This attribute can be set at any time, but the new value is not used until the next time <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> is called.</para>
              <para>For more information, see <legacyLink xlink:href="a069b979-5108-4905-932f-8ae8e7905ff2">Number of Rows Fetched and Status</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ARRAY_STATUS_PTR field in the IRD header.</para>
              <para>This attribute is mapped by an ODBC 2<legacyItalic>.x</legacyItalic> driver to the <legacyItalic>rgbRowStatus</legacyItalic> array in a call to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ROWS_FETCHED_PTR (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN * value that points to a buffer in which to return the number of rows fetched after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>; the number of rows affected by a bulk operation performed by a call to <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_REFRESH; or the number of rows affected by a bulk operation performed by <legacyBold>SQLBulkOperations</legacyBold>. This number includes error rows.</para>
              <para>For more information, see <legacyLink xlink:href="a069b979-5108-4905-932f-8ae8e7905ff2">Number of Rows Fetched and Status</legacyLink>.</para>
              <para>Setting this statement attribute sets the SQL_DESC_ROWS_PROCESSED_PTR field in the IRD header. </para>
              <para>If the call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> that fills in the buffer pointed to by this attribute does not return SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the contents of the buffer are undefined.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_SIMULATE_CURSOR (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies whether drivers that simulate positioned update and delete statements guarantee that such statements affect only one single row.</para>
              <para>To simulate positioned update and delete statements, most drivers construct a searched <legacyBold>UPDATE</legacyBold> or <legacyBold>DELETE</legacyBold> statement containing a <legacyBold>WHERE</legacyBold> clause that specifies the value of each column in the current row. Unless these columns make up a unique key, such a statement can affect more than one row.</para>
              <para>To guarantee that such statements affect only one row, the driver determines the columns in a unique key and adds these columns to the result set. If an application guarantees that the columns in the result set make up a unique key, the driver is not required to do so. This may reduce execution time.</para>
              <para>SQL_SC_NON_UNIQUE = The driver does not guarantee that simulated positioned update or delete statements will affect only one row; it is the application's responsibility to do so. If a statement affects more than one row, <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> returns SQLSTATE 01001 (Cursor operation conflict).</para>
              <para>SQL_SC_TRY_UNIQUE = The driver attempts to guarantee that simulated positioned update or delete statements affect only one row. The driver always executes such statements, even if they might affect more than one row, such as when there is no unique key. If a statement affects more than one row, <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> returns SQLSTATE 01001 (Cursor operation conflict).</para>
              <para>SQL_SC_UNIQUE = The driver guarantees that simulated positioned update or delete statements affect only one row. If the driver cannot guarantee this for a given statement, <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLPrepare</legacyBold> returns an error.</para>
              <para>If the data source provides native SQL support for positioned update and delete statements and the driver does not simulate cursors, SQL_SUCCESS is returned when SQL_SC_UNIQUE is requested for SQL_SIMULATE_CURSOR. SQL_SUCCESS_WITH_INFO is returned if SQL_SC_TRY_UNIQUE or SQL_SC_NON_UNIQUE is requested. If the data source provides the SQL_SC_TRY_UNIQUE level of support and the driver does not, SQL_SUCCESS is returned for SQL_SC_TRY_UNIQUE and SQL_SUCCESS_WITH_INFO is returned for SQL_SC_NON_UNIQUE.</para>
              <para>If the specified cursor simulation type is not supported by the data source, the driver substitutes a different simulation type and returns SQLSTATE 01S02 (Option value changed). For SQL_SC_UNIQUE, the driver substitutes, in order, SQL_SC_TRY_UNIQUE or SQL_SC_NON_UNIQUE. For SQL_SC_TRY_UNIQUE, the driver substitutes SQL_SC_NON_UNIQUE.</para>
              <para>The default is SQL_SC_UNIQUE.</para>
              <para>For more information, see <legacyLink xlink:href="b24ed59f-f25b-4646-a135-5f3596abc1a4">Simulating Positioned Update and Delete Statements</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_USE_BOOKMARKS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN value that specifies whether an application will use bookmarks with a cursor:</para>
              <para>SQL_UB_OFF = Off (the default)</para>
              <para>SQL_UB_VARIABLE = An application will use bookmarks with a cursor, and the driver will provide variable-length bookmarks if they are supported. SQL_UB_FIXED is deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3<legacyItalic>.x</legacyItalic> applications should always use variable-length bookmarks, even when working with ODBC 2<legacyItalic>.x</legacyItalic> drivers (which supported only 4-byte, fixed-length bookmarks). This is because a fixed-length bookmark is just a special case of a variable-length bookmark. When working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, the Driver Manager maps SQL_UB_VARIABLE to SQL_UB_FIXED.</para>
              <para>To use bookmarks with a cursor, the application must specify this attribute with the SQL_UB_VARIABLE value before opening the cursor.</para>
              <para>For more information, see <legacyLink xlink:href="a34c8f09-b786-4835-a44b-b7294c970aff">Retrieving Bookmarks</legacyLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   These functions can be called asynchronously only if the descriptor is an implementation descriptor, not an application descriptor.</para>
      <para>See <legacyLink xlink:href="86d37637-3a25-455d-9c82-a0d7bff8d70d">Column-Wise Binding</legacyLink> and <legacyLink xlink:href="4f622cf4-0603-47a1-a48b-944c4ef46364">Row-Wise Binding</legacyLink>.</para>
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
              <para>Returning the setting of a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the setting of a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a single field of the descriptor</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
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