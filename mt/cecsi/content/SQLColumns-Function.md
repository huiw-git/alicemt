---
title: SQLColumns Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLColumns
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
translation.priority.ht: 
  - en-gb
---
# SQLColumns Function
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
          <legacyBold>SQLColumns</legacyBold> returns the list of column names in specified tables. The driver returns this information as a result set on the specified <legacyItalic>StatementHandle</legacyItalic>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLColumns</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *      <parameterReference>CatalogName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength1</parameterReference>,
     SQLCHAR *      <parameterReference>SchemaName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength2</parameterReference>,
     SQLCHAR *      <parameterReference>TableName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength3</parameterReference>,
     SQLCHAR *      <parameterReference>ColumnName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength4</parameterReference>);</legacySyntax>
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
          <para>[Input] Catalog name. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") indicates those tables that do not have catalogs. <legacyItalic>CatalogName</legacyItalic> cannot contain a string search pattern.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>CatalogName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>CatalogName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>.</para>
      </alert>
      <definitionTable>
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
          <para>[Input] String search pattern for schema names. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") indicates those tables that do not have schemas.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>SchemaName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>SchemaName</legacyItalic> is a pattern value argument; it is treated literally, and its case is significant.</para>
      </alert>
      <definitionTable>
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
          <para>[Input] String search pattern for table names.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>TableName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>TableName</legacyItalic> is a pattern value argument; it is treated literally, and its case is significant.</para>
      </alert>
      <definitionTable>
        <definedTerm>
          <legacyItalic>NameLength3</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>TableName</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ColumnName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] String search pattern for column names. </para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>ColumnName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>ColumnName</legacyItalic> is a pattern value argument; it is treated literally, and its case is significant.</para>
      </alert>
      <definitionTable>
        <definedTerm>
          <legacyItalic>NameLength4</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length in characters of *<legacyItalic>ColumnName</legacyItalic>.</para>
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
      <para>When <legacyBold>SQLColumns</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLColumns</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>A cursor was open on the <legacyItalic>StatementHandle</legacyItalic> but <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had not been called.</para>
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
              <para>The transaction was rolled back because of a resource deadlock with another transaction.</para>
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
              <para>Memory allocation error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory that is required to support execution or completion of the function.</para>
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
              <para>(DM) The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, and the <legacyItalic>SchemaName</legacyItalic>, <legacyItalic>TableName</legacyItalic>, or <legacyItalic>ColumnName</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLColumns</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>The value of one of the name length arguments exceeded the maximum length value for the corresponding catalog or name. The maximum length of each catalog or name can be obtained by calling <legacyBold>SQLGetInfo</legacyBold> with the <legacyItalic>InfoType</legacyItalic> values. (See "Comments.")</para>
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
              <para>A catalog name was specified, and the driver or data source does not support catalogs.</para>
              <para>A schema name was specified, and the driver or data source does not support schemas.</para>
              <para>A string search pattern was specified for the schema name, table name, or column name, and the data source does not support search patterns for one or more of those arguments.</para>
              <para>The combination of the current settings of the SQL_ATTR_CONCURRENCY and SQL_ATTR_CURSOR_TYPE statement attributes was not supported by the driver or data source. </para>
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
              <para>The query timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtAttr</legacyBold>, SQL_ATTR_QUERY_TIMEOUT.</para>
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
      <para>This function typically is used before statement execution to retrieve information about columns for a table or tables from the data source's catalog. <legacyBold>SQLColumns</legacyBold> can be used to retrieve data for all types of items returned by <legacyBold>SQLTables</legacyBold>. In addition to base tables, this may include (but is not limited to) views, synonyms, system tables, and so on. By contrast, the functions <legacyBold>SQLColAttribute</legacyBold> and <legacyBold>SQLDescribeCol</legacyBold> describe the columns in a result set and the function <legacyBold>SQLNumResultCols</legacyBold> returns the number of columns in a result set. For more information, see <legacyLink xlink:href="d5915d0c-eec3-4382-850e-bd863763c99a">Uses of Catalog Data</legacyLink>.</para>
      <alert class="note">
        <para>For more information about the general use, arguments, and returned data of ODBC catalog functions, see <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
      </alert>
      <para>
        <legacyBold>SQLColumns</legacyBold> returns the results as a standard result set, ordered by TABLE_CAT, TABLE_SCHEM, TABLE_NAME, and ORDINAL_POSITION. </para>
      <alert class="note">
        <para>When an application works with an ODBC 2.<legacyItalic>x</legacyItalic> driver, no ORDINAL_POSITION column is returned in the result set. As a result, when working with ODBC 2.<legacyItalic>x</legacyItalic> drivers, the order of the columns in the column list returned by <legacyBold>SQLColumns</legacyBold> is not necessarily the same as the order of the columns returned when the application performs a SELECT statement on all columns in that table.</para>
      </alert>
      <alert class="note">
        <para>  <legacyBold>SQLColumns</legacyBold> might not return all columns. For example, a driver might not return information about pseudo-columns, such as Oracle ROWID. Applications can use any valid column, whether it is returned by <legacyBold>SQLColumns</legacyBold>.</para>
        <para>Some columns that can be returned by <legacyBold>SQLStatistics</legacyBold> are not returned by <legacyBold>SQLColumns</legacyBold>. For example, <legacyBold>SQLColumns</legacyBold> does not return the columns in an index created over an expression or filter, such as SALARY + BENEFITS or DEPT = 0012.</para>
      </alert>
      <para>The lengths of VARCHAR columns are not shown in the table; the actual lengths depend on the data source. To determine the actual lengths of the TABLE_CAT, TABLE_SCHEM, TABLE_NAME, and COLUMN_NAME columns, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, and SQL_MAX_COLUMN_NAME_LEN options.</para>
      <para>The following columns have been renamed for ODBC 3.<legacyItalic>x</legacyItalic>. The column name changes do not affect backward compatibility because applications bind by column number.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC 2.0 column</para>
            </TD>
            <TD>
              <para>ODBC 3.<legacyItalic>x</legacyItalic> column</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>TABLE_QUALIFIER</para>
            </TD>
            <TD>
              <para>TABLE_CAT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TABLE_OWNER</para>
            </TD>
            <TD>
              <para>TABLE_SCHEM</para>
            </TD>
          </tr>
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
          <tr>
            <TD>
              <para>RADIX</para>
            </TD>
            <TD>
              <para>NUM_PREC_RADIX</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following columns have been added to the result set returned by <legacyBold>SQLColumns</legacyBold> for ODBC 3.<legacyItalic>x</legacyItalic>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>   CHAR_OCTET_LENGTH </para>
            </TD>
            <TD>
              <para>ORDINAL_POSITION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>   COLUMN_DEF</para>
            </TD>
            <TD>
              <para>SQL_DATA_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>   IS_NULLABLE </para>
            </TD>
            <TD>
              <para>SQL_DATETIME_SUB</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following table lists the columns in the result set. Additional columns beyond column 18 (IS_NULLABLE) can be defined by the driver. An application should gain access to driver-specific columns by counting down from the end of the result set instead of specifying an explicit ordinal position. For more information, see <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Column name</para>
            </TD>
            <TD>
              <para>Column</para>
              <para>number</para>
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
              <para>TABLE_CAT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Catalog name; NULL if not applicable to the data source. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have catalogs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TABLE_SCHEM (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Varchar </para>
            </TD>
            <TD>
              <para>Schema name; NULL if not applicable to the data source. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have schemas.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TABLE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Table name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>4</para>
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
              <para>5</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>SQL data type. This can be an ODBC SQL data type or a driver-specific SQL data type. For datetime and interval data types, this column returns the concise data type (such as SQL_TYPE_DATE or SQL_INTERVAL_YEAR_TO_MONTH, instead of the nonconcise data type such as SQL_DATETIME or SQL_INTERVAL). For a list of valid ODBC SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> in Appendix D: Data Types. For information about driver-specific SQL data types, see the driver's documentation.</para>
              <para>The data types returned for ODBC 3.<legacyItalic>x</legacyItalic> and ODBC 2.<legacyItalic>x</legacyItalic> applications may be different. For more information, see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TYPE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Data source–dependent data type name; for example, "CHAR", "VARCHAR", "MONEY", "LONG VARBINAR", or "CHAR ( ) FOR BIT DATA".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_SIZE (ODBC 1.0) </para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>If DATA_TYPE is SQL_CHAR or SQL_VARCHAR, this column contains the maximum length in characters of the column. For datetime data types, this is the total number of characters required to display the value when it is converted to characters. For numeric data types, this is either the total number of digits or the total number of bits allowed in the column, according to the NUM_PREC_RADIX column. For interval data types, this is the number of characters in the character representation of the interval literal (as defined by the interval leading precision, see <legacyLink xlink:href="e9eb38d8-f9db-4401-8c62-aa394054cbbf">Interval Data Type Length</legacyLink> in Appendix D: Data Types). For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BUFFER_LENGTH (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>The length in bytes of data transferred on an SQLGetData, SQLFetch, or SQLFetchScroll operation if SQL_C_DEFAULT is specified. For numeric data, this size may differ from the size of the data stored on the data source. This value might differ from COLUMN_SIZE column for character data. For more information about length, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DECIMAL_DIGITS (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>9</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>The total number of significant digits to the right of the decimal point. For SQL_TYPE_TIME and SQL_TYPE_TIMESTAMP, this column contains the number of digits in the fractional seconds component. For the other data types, this is the decimal digits of the column on the data source. For interval data types that contain a time component, this column contains the number of digits to the right of the decimal point (fractional seconds). For interval data types that do not contain a time component, this column is 0. For more information about decimal digits, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types. NULL is returned for data types where DECIMAL_DIGITS is not applicable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUM_PREC_RADIX (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>For numeric data types, either 10 or 2. If it is 10, the values in COLUMN_SIZE and DECIMAL_DIGITS give the number of decimal digits allowed for the column. For example, a DECIMAL(12,5) column would return a NUM_PREC_RADIX of 10, a COLUMN_SIZE of 12, and a DECIMAL_DIGITS of 5; a FLOAT column could return a NUM_PREC_RADIX of 10, a COLUMN_SIZE of 15, and a DECIMAL_DIGITS of NULL.</para>
              <para>If it is 2, the values in COLUMN_SIZE and DECIMAL_DIGITS give the number of bits allowed in the column. For example, a FLOAT column could return a RADIX of 2, a COLUMN_SIZE of 53, and a DECIMAL_DIGITS of NULL.</para>
              <para>NULL is returned for data types where NUM_PREC_RADIX is not applicable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULLABLE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>SQL_NO_NULLS if the column could not include NULL values.</para>
              <para>SQL_NULLABLE if the column accepts NULL values.</para>
              <para>SQL_NULLABLE_UNKNOWN if it is not known whether the column accepts NULL values.</para>
              <para>The value returned for this column differs from the value returned for the IS_NULLABLE column. The NULLABLE column indicates with certainty that a column can accept NULLs, but cannot indicate with certainty that a column does not accept NULLs. The IS_NULLABLE column indicates with certainty that a column cannot accept NULLs, but cannot indicate with certainty that a column accepts NULLs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REMARKS (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>12</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>A description of the column.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_DEF (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>13</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>The default value of the column. The value in this column should be interpreted as a string if it is enclosed in quotation marks.</para>
              <para>If NULL was specified as the default value, this column is the word NULL, not enclosed in quotation marks. If the default value cannot be represented without truncation, this column contains TRUNCATED, without enclosing single quotation marks. If no default value was specified, this column is NULL.</para>
              <para>The value of COLUMN_DEF can be used in generating a new column definition, except when it contains the value TRUNCATED.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_TYPE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>14</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>SQL data type, as it appears in the SQL_DESC_TYPE record field in the IRD. This can be an ODBC SQL data type or a driver-specific SQL data type. This column is the same as the DATA_TYPE column, except for datetime and interval data types. This column returns the nonconcise data type (such as SQL_DATETIME or SQL_INTERVAL), instead of the concise data type (such as SQL_TYPE_DATE or SQL_INTERVAL_YEAR_TO_MONTH) for datetime and interval data types. If this column returns SQL_DATETIME or SQL_INTERVAL, the specific data type can be determined from the SQL_DATETIME_SUB column. For a list of valid ODBC SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> in Appendix D: Data Types. For information about driver-specific SQL data types, see the driver's documentation.</para>
              <para>The data types returned for ODBC 3.<legacyItalic>x</legacyItalic> and ODBC 2.<legacyItalic>x</legacyItalic> applications may be different. For more information, see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATETIME_SUB (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>15</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>The subtype code for datetime and interval data types. For other data types, this column returns a NULL. For more information about datetime and interval subcodes, see "SQL_DESC_DATETIME_INTERVAL_CODE" in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CHAR_OCTET_LENGTH (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>16</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>The maximum length in bytes of a character or binary data type column. For all other data types, this column returns a NULL.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ORDINAL_POSITION (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>17</para>
            </TD>
            <TD>
              <para>Integer not NULL</para>
            </TD>
            <TD>
              <para>The ordinal position of the column in the table. The first column in the table is number 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IS_NULLABLE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>18</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>"NO" if the column does not include NULLs.</para>
              <para>"YES" if the column could include NULLs.</para>
              <para>This column returns a zero-length string if nullability is unknown. </para>
              <para>ISO rules are followed to determine nullability. An ISO SQL–compliant DBMS cannot return an empty string. </para>
              <para>The value returned for this column differs from the value returned for the NULLABLE column. (See the description of the NULLABLE column.)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>In the following example, an application declares buffers for the result set returned by <legacyBold>SQLColumns</legacyBold>. It calls <legacyBold>SQLColumns</legacyBold> to return a result set that describes each column in the EMPLOYEE table. It then calls <legacyBold>SQLBindCol</legacyBold> to bind the columns in the result set to the buffers. Finally, the application fetches each row of data with <legacyBold>SQLFetch</legacyBold> and processes it.</para>
      <code>// SQLColumns_Function.cpp
// compile with: ODBC32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;
#define STR_LEN 128 + 1
#define REM_LEN 254 + 1

// Declare buffers for result set data
SQLCHAR szSchema[STR_LEN];
SQLCHAR szCatalog[STR_LEN];
SQLCHAR szColumnName[STR_LEN];
SQLCHAR szTableName[STR_LEN];
SQLCHAR szTypeName[STR_LEN];
SQLCHAR szRemarks[REM_LEN];
SQLCHAR szColumnDefault[STR_LEN];
SQLCHAR szIsNullable[STR_LEN];

SQLINTEGER ColumnSize;
SQLINTEGER BufferLength;
SQLINTEGER CharOctetLength;
SQLINTEGER OrdinalPosition;

SQLSMALLINT DataType;
SQLSMALLINT DecimalDigits;
SQLSMALLINT NumPrecRadix;
SQLSMALLINT Nullable;
SQLSMALLINT SQLDataType;
SQLSMALLINT DatetimeSubtypeCode;

SQLHSTMT hstmt = NULL;

// Declare buffers for bytes available to return
SQLINTEGER cbCatalog;
SQLINTEGER cbSchema;
SQLINTEGER cbTableName;
SQLINTEGER cbColumnName;
SQLINTEGER cbDataType;
SQLINTEGER cbTypeName;
SQLINTEGER cbColumnSize;
SQLLEN cbBufferLength;
SQLINTEGER cbDecimalDigits;
SQLINTEGER cbNumPrecRadix;
SQLINTEGER cbNullable;
SQLINTEGER cbRemarks;
SQLINTEGER cbColumnDefault;
SQLINTEGER cbSQLDataType;
SQLINTEGER cbDatetimeSubtypeCode;
SQLINTEGER cbCharOctetLength;
SQLINTEGER cbOrdinalPosition;
SQLINTEGER cbIsNullable;

int main() {
   SQLHENV henv;
   SQLHDBC hdbc;
   SQLHSTMT hstmt = 0;
   SQLRETURN retcode;

   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);

   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
      // Bind columns in result set to buffers
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&amp;cbCatalog);
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &amp;cbSchema);
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&amp;cbTableName);
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &amp;cbColumnName);
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &amp;DataType, 0, &amp;cbDataType);
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &amp;cbTypeName);
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &amp;ColumnSize, 0, &amp;cbColumnSize);
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &amp;BufferLength, 0, &amp;cbBufferLength);
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &amp;DecimalDigits, 0, &amp;cbDecimalDigits);
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &amp;NumPrecRadix, 0, &amp;cbNumPrecRadix);
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &amp;Nullable, 0, &amp;cbNullable);
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &amp;cbRemarks);
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &amp;cbColumnDefault);
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &amp;SQLDataType, 0, &amp;cbSQLDataType);
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &amp;DatetimeSubtypeCode, 0, &amp;cbDatetimeSubtypeCode);
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &amp;CharOctetLength, 0, &amp;cbCharOctetLength);
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &amp;OrdinalPosition, 0, &amp;cbOrdinalPosition);
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &amp;cbIsNullable);

      while (SQL_SUCCESS == retcode) {
         retcode = SQLFetch(hstmt);
         /*
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)
            0;   // show_error();
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
            0;   // Process fetched data
         else
            break;
        */
      }
   }
}</code>
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
              <para>Returning privileges for a column or columns</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e">SQLColumnPrivileges Function</legacyLink>
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
              <para>Fetching multiple rows of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning columns that uniquely identify a row, or columns automatically updated by a transaction</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bb2d9f21-bda0-4e50-a8be-f710db660034">SQLSpecialColumns Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning table statistics and indexes</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="45210682-cfea-4e5d-9951-bcf1cbe10f41">SQLStatistics Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning a list of tables in a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning privileges for a table or tables</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8cfdb64f-64c5-47e6-ad57-0533ac630afa">SQLTablePrivileges Function</legacyLink>
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