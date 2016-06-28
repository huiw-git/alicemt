---
title: SQLProcedures Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLProcedures
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: d0d9ef10-2fd4-44a5-9334-649f186f4ba0
translation.priority.ht: 
  - en-gb
---
# SQLProcedures Function
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
          <legacyBold>SQLProcedures</legacyBold> returns the list of procedure names stored in a specific data source. <legacyItalic>Procedure</legacyItalic> is a generic term used to describe an <legacyItalic>executable object</legacyItalic>, or a named entity that can be invoked using input and output parameters. For more information on procedures, see the <legacyLink xlink:href="92172f52-6bd2-4b17-9ef0-baf1a97f7510">Procedures</legacyLink>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLProcedures</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *      <parameterReference>CatalogName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength1</parameterReference>,
     SQLCHAR *      <parameterReference>SchemaName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength2</parameterReference>,
     SQLCHAR *      <parameterReference>ProcName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength3</parameterReference>);</legacySyntax>
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
          <legacyItalic>CatalogName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Procedure catalog. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have catalogs. <legacyItalic>CatalogName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>CatalogName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>CatalogName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>CatalogName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>SchemaName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] String search pattern for procedure schema names. If a driver supports schemas for some procedures but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those procedures that do not have schemas. </para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>SchemaName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>SchemaName</legacyItalic> is a pattern value argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>SchemaName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ProcName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] String search pattern for procedure names. </para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>ProcName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>ProcName</legacyItalic> is a pattern value argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength3</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>ProcName</legacyItalic>.</para>
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
      <para>When <legacyBold>SQLProcedures</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLProcedures</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called. This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA, and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, but <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had not been called.</para>
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
              <para>The associated connection failed during the execution of this function, and the state of the transaction cannot be determined.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
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
              <para>The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, the <legacyItalic>CatalogName</legacyItalic> argument was a null pointer, and the SQL_CATALOG_NAME <legacyItalic>InfoType</legacyItalic> returns that catalog names are supported.</para>
              <para>(DM) The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, and the <legacyItalic>SchemaName </legacyItalic>or <legacyItalic>ProcName</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was was still executing when this function was called.</para>
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
              <para>(DM) The value of one of the name length arguments was less than 0 but not equal to SQL_NTS.</para>
              <para>The value of one of the name length arguments exceeded the maximum length value for the corresponding name. </para>
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
              <para>A procedure catalog was specified, and the driver or data source does not support catalogs.</para>
              <para>A procedure schema was specified, and the driver or data source does not support schemas.</para>
              <para>A string search pattern was specified for the procedure schema or procedure name, and the data source does not support search patterns for one or more of those arguments.</para>
              <para>The combination of the current settings of the SQL_ATTR_CONCURRENCY and SQL_ATTR_CURSOR_TYPE statement attributes was not supported by the driver or data source.</para>
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
              <para>The query timeout period expired before the data source returned the requested result set. The timeout period is set through <legacyBold>SQLSetStmtAttr</legacyBold>, SQL_ATTR_QUERY_TIMEOUT.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>StatementHandle</legacyItalic> does not support this function.</para>
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
        <legacyBold>SQLProcedures</legacyBold> lists all procedures in the requested range. A user may or may not have permission to execute any of these procedures. To check accessibility, an application can call <legacyBold>SQLGetInfo</legacyBold> and check the SQL_ACCESSIBLE_PROCEDURES information value. Otherwise, the application must be able to handle a situation where the user selects a procedure that it cannot execute. For information about how this information might be used, see <legacyLink xlink:href="92172f52-6bd2-4b17-9ef0-baf1a97f7510">Procedures</legacyLink>.</para>
      <alert class="note">
        <para>For more information about the general use, arguments, and returned data of ODBC catalog functions, see <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
      </alert>
      <para>
        <legacyBold>SQLProcedures</legacyBold> returns the results as a standard result set, ordered by PROCEDURE_CAT, PROCEDURE_SCHEMA, and PROCEDURE_NAME.</para>
      <alert class="note">
        <para>
          <legacyBold>SQLProcedures</legacyBold> might not return all procedures. Applications can use any valid procedure, regardless of whether it is returned by <legacyBold>SQLProcedures</legacyBold>.</para>
      </alert>
      <para>The following columns have been renamed for ODBC 3<legacyItalic>.x</legacyItalic>. The column name changes do not affect backward compatibility because applications bind by column number.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC 2.0 column</para>
            </TD>
            <TD>
              <para>ODBC 3<legacyItalic>.x</legacyItalic> column</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>PROCEDURE_QUALIFIER</para>
            </TD>
            <TD>
              <para>PROCEDURE_CAT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROCEDURE _OWNER</para>
            </TD>
            <TD>
              <para>PROCEDURE _SCHEM</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>To determine the actual lengths of the PROCEDURE_CAT, PROCEDURE_SCHEM, and PROCEDURE_NAME columns, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, and SQL_MAX_PROCEDURE_NAME_LEN options.</para>
      <para>The following table lists the columns in the result set. Additional columns beyond column 8 (PROCEDURE_TYPE) can be defined by the driver. An application should gain access to driver-specific columns by counting down from the end of the result set rather than specifying an explicit ordinal position. For more information, see <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Column name</para>
            </TD>
            <TD>
              <para>Column number</para>
            </TD>
            <TD>
              <para>Data type</para>
            </TD>
            <TD>
              <para>Comments</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>PROCEDURE_CAT (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Procedure catalog identifier; NULL if not applicable to the data source. If a driver supports catalogs for some procedures but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those procedures that do not have catalogs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROCEDURE_SCHEM (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Procedure schema identifier; NULL if not applicable to the data source. If a driver supports schemas for some procedures but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those procedures that do not have schemas.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROCEDURE_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Procedure identifier.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUM_INPUT_PARAMS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>N/A</para>
            </TD>
            <TD>
              <para>Reserved for future use. Applications should not rely on the data returned in these result columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUM_OUTPUT_PARAMS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>N/A</para>
            </TD>
            <TD>
              <para>Reserved for future use. Applications should not rely on the data returned in these result columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUM_RESULT_SETS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>N/A</para>
            </TD>
            <TD>
              <para>Reserved for future use. Applications should not rely on the data returned in these result columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REMARKS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>A description of the procedure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROCEDURE_TYPE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Defines the procedure type:</para>
              <para>SQL_PT_UNKNOWN: It cannot be determined whether the procedure returns a value.</para>
              <para>SQL_PT_PROCEDURE: The returned object is a procedure; that is, it does not have a return value.</para>
              <para>SQL_PT_FUNCTION: The returned object is a function; that is, it has a return value.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The <legacyItalic>SchemaName</legacyItalic> and <legacyItalic>ProcName</legacyItalic> arguments accept search patterns. For more information about valid search patterns, see <legacyLink xlink:href="1d3f0ea6-87af-4836-807f-955e7df2b5df">Pattern Value Arguments</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <legacyLink xlink:href="145130cc-40e7-4722-8417-dff131084752">Procedure Calls</legacyLink>.</para>
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
              <para>Returning the parameters and result set columns of a procedure</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4ca37b28-a6df-465b-8988-d422d37fc025">SQLProcedureColumns Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Syntax for invoking stored procedures</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="09063f43-f5f0-4cf0-baa9-12fec8898997">Executing Statements</legacyLink>
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