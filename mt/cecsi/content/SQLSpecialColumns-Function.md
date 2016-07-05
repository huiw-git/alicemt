---
title: SQLSpecialColumns Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSpecialColumns
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: bb2d9f21-bda0-4e50-a8be-f710db660034
translation.priority.ht: 
  - en-gb
---
# SQLSpecialColumns Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: Open Group</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLSpecialColumns</legacyBold> retrieves the following information about columns within a specified table:</para>
        <list class="bullet">
          <listItem>
            <para>The optimal set of columns that uniquely identifies a row in the table.</para>
          </listItem>
          <listItem>
            <para>Columns that are automatically updated when any value in the row is updated by a transaction.</para>
          </listItem>
        </list>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSpecialColumns</legacyBold>(
     SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
     SQLSMALLINT   <parameterReference>IdentifierType</parameterReference>,
     SQLCHAR *     <parameterReference>CatalogName</parameterReference>,
     SQLSMALLINT   <parameterReference>NameLength1</parameterReference>,
     SQLCHAR *     <parameterReference>SchemaName</parameterReference>,
     SQLSMALLINT   <parameterReference>NameLength2</parameterReference>,
     SQLCHAR *     <parameterReference>TableName</parameterReference>,
     SQLSMALLINT   <parameterReference>NameLength3</parameterReference>,
     SQLSMALLINT   <parameterReference>Scope</parameterReference>,
     SQLSMALLINT   <parameterReference>Nullable</parameterReference>);</legacySyntax>
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
          <legacyItalic>IdentifierType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of column to return. Must be one of the following values:</para>
          <para>SQL_BEST_ROWID: Returns the optimal column or set of columns that, by retrieving values from the column or columns, allows any row in the specified table to be uniquely identified. A column can be either a pseudo-column specifically designed for this purpose (as in Oracle ROWID or Ingres TID) or the column or columns of any unique index for the table.   </para>
          <para>SQL_ROWVER: Returns the column or columns in the specified table, if any, that are automatically updated by the data source when any value in the row is updated by any transaction (as in SQLBase ROWID or Sybase TIMESTAMP). </para>
        </definition>
        <definedTerm>
          <legacyItalic>CatalogName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Catalog name for the table. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have catalogs.<legacyItalic> CatalogName</legacyItalic> cannot contain a string search pattern.</para>
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
          <para>[Input] Schema name for the table. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have schemas.<legacyItalic> SchemaName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>SchemaName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>SchemaName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>SchemaName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TableName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Table name. This argument cannot be a null pointer.<legacyItalic> TableName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>TableName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>TableName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength3</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>TableName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Scope</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Minimum required scope of the rowid. The returned rowid may be of greater scope. Must be one of the following:</para>
          <para>SQL_SCOPE_CURROW: The rowid is guaranteed to be valid only while positioned on that row. A later reselect using rowid may not return a row if the row was updated or deleted by another transaction.   </para>
          <para>SQL_SCOPE_TRANSACTION: The rowid is guaranteed to be valid for the duration of the current transaction.   </para>
          <para>SQL_SCOPE_SESSION: The rowid is guaranteed to be valid for the duration of the session (across transaction boundaries). </para>
        </definition>
        <definedTerm>
          <legacyItalic>Nullable</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Determines whether to return special columns that can have a NULL value. Must be one of the following:</para>
          <para>SQL_NO_NULLS: Exclude special columns that can have NULL values. Some drivers cannot support SQL_NO_NULLS, and these drivers will return an empty result set if SQL_NO_NULLS was specified. Applications should be prepared for this case and request SQL_NO_NULLS only if it is absolutely required.   </para>
          <para>SQL_NULLABLE: Return special columns even if they can have NULL values. </para>
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
      <para>When <legacyBold>SQLSpecialColumns</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSpecialColumns</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic>, and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called. This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
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
              <para>The <legacyItalic>TableName</legacyItalic> argument was a null pointer. </para>
              <para>The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, the <legacyItalic>CatalogName</legacyItalic> argument was a null pointer, and the SQL_CATALOG_NAME <legacyItalic>InfoType</legacyItalic> returns that catalog names are supported.</para>
              <para>(DM) The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, and the <legacyItalic>SchemaName</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This function was still executing when <unmanagedCodeEntityReference>SQLSpecialColumns</unmanagedCodeEntityReference> was called.</para>
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
              <para>(DM) The value of one of the length arguments was less than 0 but not equal to SQL_NTS.</para>
              <para>The value of one of the length arguments exceeded the maximum length value for the corresponding name. The maximum length of each name can be obtained by calling <legacyBold>SQLGetInfo</legacyBold> with the <legacyItalic>InfoType</legacyItalic> values: SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, or SQL_MAX_TABLE_NAME_LEN.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY097</para>
            </TD>
            <TD>
              <para>Column type out of range</para>
            </TD>
            <TD>
              <para>(DM) An invalid <legacyItalic>IdentifierType</legacyItalic> value was specified.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY098</para>
            </TD>
            <TD>
              <para>Scope type out of range</para>
            </TD>
            <TD>
              <para>(DM) An invalid <legacyItalic>Scope</legacyItalic> value was specified.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY099</para>
            </TD>
            <TD>
              <para>Nullable type out of range</para>
            </TD>
            <TD>
              <para>(DM) An invalid <legacyItalic>Nullable</legacyItalic> value was specified.</para>
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
              <para>A catalog was specified, and the driver or data source does not support catalogs.</para>
              <para>A schema was specified, and the driver or data source does not support schemas.</para>
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
      <para>When the <legacyItalic>IdentifierType</legacyItalic> argument is SQL_BEST_ROWID, <legacyBold>SQLSpecialColumns</legacyBold> returns the column or columns that uniquely identify each row in the table. These columns can always be used in a <legacyItalic>select-list</legacyItalic> or <legacyBold>WHERE</legacyBold> clause. <legacyBold>SQLColumns</legacyBold>, which is used to return a variety of information on the columns of a table, does not necessarily return the columns that uniquely identify each row, or columns that are automatically updated when any value in the row is updated by a transaction. For example, <legacyBold>SQLColumns</legacyBold> might not return the Oracle pseudo-column ROWID. This is why <legacyBold>SQLSpecialColumns</legacyBold> is used to return these columns. For more information, see <legacyLink xlink:href="d5915d0c-eec3-4382-850e-bd863763c99a">Uses of Catalog Data</legacyLink>.</para>
      <alert class="note">
        <para>For more information about the general use, arguments, and returned data of ODBC catalog functions, see <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
      </alert>
      <para>If there are no columns that uniquely identify each row in the table, <legacyBold>SQLSpecialColumns</legacyBold> returns a rowset with no rows; a subsequent call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> on the statement returns SQL_NO_DATA.</para>
      <para>If the <legacyItalic>IdentifierType</legacyItalic>, <legacyItalic>Scope</legacyItalic>, or <legacyItalic>Nullable</legacyItalic> arguments specify characteristics that are not supported by the data source, <legacyBold>SQLSpecialColumns</legacyBold> returns an empty result set.</para>
      <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, the <legacyItalic>CatalogName</legacyItalic>, <legacyItalic>SchemaName</legacyItalic>, and <legacyItalic>TableName</legacyItalic> arguments are treated as identifiers, so they cannot be set to a null pointer in certain situations. (For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>.)</para>
      <para>
        <legacyBold>SQLSpecialColumns</legacyBold> returns the results as a standard result set, ordered by SCOPE.</para>
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
              <para>PRECISION</para>
            </TD>
            <TD>
              <para>COLUMN_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LENGTH</para>
            </TD>
            <TD>
              <para>BUFFER_LENGTH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SCALE</para>
            </TD>
            <TD>
              <para>DECIMAL_DIGITS</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>To determine the actual length of the COLUMN_NAME column, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_COLUMN_NAME_LEN option.</para>
      <para>The following table lists the columns in the result set. Additional columns beyond column 8 (PSEUDO_COLUMN) can be defined by the driver. An application should gain access to driver-specific columns by counting down from the end of the result set rather than specifying an explicit ordinal position. For more information, see <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>.</para>
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
              <para>SCOPE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Actual scope of the rowid. Contains one of the following values:</para>
              <para>SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION</para>
              <para>NULL is returned when <legacyItalic>IdentifierType</legacyItalic> is SQL_ROWVER. For a description of each value, see the description of <legacyItalic>Scope</legacyItalic> in "Syntax," earlier in this section.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Column name. The driver returns an empty string for a column that does not have a name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DATA_TYPE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>SQL data type. This can be an ODBC SQL data type or a driver-specific SQL data type. For a list of valid ODBC SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink>. For information about driver-specific SQL data types, see the driver's documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TYPE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Data source–dependent data type name; for example, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", or "CHAR ( ) FOR BIT DATA".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_SIZE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>The size of the column on the data source. For more information concerning column size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BUFFER_LENGTH (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>The length in bytes of data transferred on an <legacyBold>SQLGetData</legacyBold> or <legacyBold>SQLFetch</legacyBold> operation if SQL_C_DEFAULT is specified. For numeric data, this size may be different than the size of the data stored on the data source. This value is the same as the COLUMN_SIZE column for character or binary data. For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DECIMAL_DIGITS (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>The decimal digits of the column on the data source. NULL is returned for data types where decimal digits are not applicable. For more information concerning decimal digits, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PSEUDO_COLUMN (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Indicates whether the column is a pseudo-column, such as Oracle ROWID:</para>
              <para>SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO</para>
              <alert class="note">
                <para>For maximum interoperability, pseudo-columns should not be quoted with the identifier quote character returned by <legacyBold>SQLGetInfo</legacyBold>.</para>
              </alert>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>After the application retrieves values for SQL_BEST_ROWID, the application can use these values to reselect that row within the defined scope. The <legacyBold>SELECT</legacyBold> statement is guaranteed to return either no rows or one row.</para>
      <para>If an application reselects a row based on the rowid column or columns and the row is not found, the application can assume that the row was deleted or the rowid columns were modified. The opposite is not true: even if the rowid has not changed, the other columns in the row may have changed.</para>
      <para>Columns returned for column type SQL_BEST_ROWID are useful for applications that need to scroll forward and back within a result set to retrieve the most recent data from a set of rows. The column or columns of the rowid are guaranteed not to change while positioned on that row.</para>
      <para>The column or columns of the rowid may remain valid even when the cursor is not positioned on the row; the application can determine this by checking the SCOPE column in the result set.</para>
      <para>Columns returned for column type SQL_ROWVER are useful for applications that need the ability to check whether any columns in a given row have been updated while the row was reselected using the rowid. For example, after reselecting a row using rowid, the application can compare the previous values in the SQL_ROWVER columns to the ones just fetched. If the value in a SQL_ROWVER column differs from the previous value, the application can alert the user that data on the display has changed.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>For a code example of a similar function, see <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns</legacyLink>.</para>
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
              <para>Returning the columns in a table or tables</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns Function</legacyLink>
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
              <para>Returning the columns of a primary key</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys Function</legacyLink>
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