---
title: SQLForeignKeys Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLForeignKeys
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
translation.priority.ht: 
  - en-gb
---
# SQLForeignKeys Function
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
          <legacyBold>SQLForeignKeys</legacyBold> can return:</para>
        <list class="bullet">
          <listItem>
            <para>A list of foreign keys in the specified table (columns in the specified table that refer to primary keys in other tables).</para>
          </listItem>
          <listItem>
            <para>A list of foreign keys in other tables that refer to the primary key in the specified table.</para>
          </listItem>
        </list>
        <para>The driver returns each list as a result set on the specified statement. </para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLForeignKeys</legacyBold>(
     SQLHSTMT       <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *      <parameterReference>PKCatalogName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength1</parameterReference>,
     SQLCHAR *      <parameterReference>PKSchemaName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength2</parameterReference>,
     SQLCHAR *      <parameterReference>PKTableName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength3</parameterReference>,
     SQLCHAR *      <parameterReference>FKCatalogName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength4</parameterReference>,
     SQLCHAR *      <parameterReference>FKSchemaName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength5</parameterReference>,
     SQLCHAR *      <parameterReference>FKTableName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength6</parameterReference>);</legacySyntax>
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
          <legacyItalic>PKCatalogName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Primary key table catalog name. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have catalogs. <legacyItalic>PKCatalogName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>PKCatalogName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>PKCatalogName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>PKCatalogName</legacyItalic>, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>PKSchemaName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Primary key table schema name. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have schemas. <legacyItalic>PKSchemaName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>PKSchemaName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>PKSchemaName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>PKSchemaName</legacyItalic>, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>PKTableName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Primary key table name. <legacyItalic>PKTableName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>PKTableName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>PKTableName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength3</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>PKTableName</legacyItalic>, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FKCatalogName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Foreign key table catalog name. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have catalogs. <legacyItalic>FKCatalogName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>FKCatalogName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>FKCatalogName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant. </para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength4</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>FKCatalogName</legacyItalic>, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FKSchemaName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Foreign key table schema name. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, an empty string ("") denotes those tables that do not have schemas. <legacyItalic>FKSchemaName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>FKSchemaName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>FKSchemaName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength5</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>FKSchemaName</legacyItalic>, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>FKTableName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Foreign key table name. <legacyItalic>FKTableName</legacyItalic> cannot contain a string search pattern.</para>
          <para>If the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE, <legacyItalic>FKTableName</legacyItalic> is treated as an identifier and its case is not significant. If it is SQL_FALSE, <legacyItalic>FKTableName</legacyItalic> is an ordinary argument; it is treated literally, and its case is significant.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength6</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>FKTableName</legacyItalic>, in characters.</para>
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
      <para>When <legacyBold>SQLForeignKeys</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLForeignKeys</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>Memory allocation  error</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>, and then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
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
              <para>(DM) The arguments <legacyItalic>PKTableName</legacyItalic> and <legacyItalic>FKTableName</legacyItalic> were both null pointers.</para>
              <para>The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, the <legacyItalic>FKCatalogName</legacyItalic> or <legacyItalic>PKCatalogName</legacyItalic> argument was a null pointer, and the SQL_CATALOG_NAME <legacyItalic>InfoType</legacyItalic> returns that catalog names are supported.</para>
              <para>(DM) The SQL_ATTR_METADATA_ID statement attribute was set to SQL_TRUE, and the <legacyItalic>FKSchemaName</legacyItalic>, <legacyItalic>PKSchemaName</legacyItalic>, <legacyItalic>FKTableName</legacyItalic>, or<legacyItalic> PKTableName</legacyItalic> argument was a null pointer.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the SQLForeignKeys function was called.</para>
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
              <para>The value of one of the name length arguments exceeded the maximum length value for the corresponding name. (See "Comments.")</para>
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
      <para>For information about how the information returned by this function might be used, see <legacyLink xlink:href="d5915d0c-eec3-4382-850e-bd863763c99a">Uses of Catalog Data</legacyLink>.</para>
      <para>If *<legacyItalic>PKTableName</legacyItalic> contains a table name, <legacyBold>SQLForeignKeys</legacyBold> returns a result set that contains the primary key of the specified table and all the foreign keys that refer to it. The list of foreign keys in other tables does not include foreign keys that point to unique constraints in the specified table.</para>
      <para>If *<legacyItalic>FKTableName</legacyItalic> contains a table name, <legacyBold>SQLForeignKeys</legacyBold> returns a result set that contains all the foreign keys in the specified table that point to primary keys in other tables, and the primary keys in the other tables to which they refer. The list of foreign keys in the specified table does not contain foreign keys that refer to unique constraints in other tables.</para>
      <para>If both *<legacyItalic>PKTableName</legacyItalic> and *<legacyItalic>FKTableName</legacyItalic> contain table names, <legacyBold>SQLForeignKeys</legacyBold> returns the foreign keys in the table specified in *<legacyItalic>FKTableName</legacyItalic> that refer to the primary key of the table specified in *<legacyItalic>PKTableName</legacyItalic>. This should be one key at most.</para>
      <alert class="note">
        <para>For more information about the general use, arguments, and returned data of ODBC catalog functions, see <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
      </alert>
      <para>
        <legacyBold>SQLForeignKeys</legacyBold> returns results as a standard result set. If the foreign keys associated with a primary key are requested, the result set is ordered by FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME, and KEY_SEQ. If the primary keys associated with a foreign key are requested, the result set is ordered by PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME, and KEY_SEQ. The following table lists the columns in the result set.</para>
      <para>The lengths of VARCHAR columns are not shown in the table; the actual lengths depend on the data source. To determine the actual lengths of the PKTABLE_CAT or FKTABLE_CAT, PKTABLE_SCHEM or FKTABLE_SCHEM, PKTABLE_NAME or FKTABLE_NAME, and PKCOLUMN_NAME or FKCOLUMN_NAME columns, an application can call <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, and SQL_MAX_COLUMN_NAME_LEN options.</para>
      <para>The following columns have been renamed for ODBC 3<legacyItalic>.x.</legacyItalic> The column name changes do not affect backward compatibility because applications bind by column number.</para>
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
              <para>PKTABLE_QUALIFIER</para>
            </TD>
            <TD>
              <para>PKTABLE_CAT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PKTABLE_OWNER</para>
            </TD>
            <TD>
              <para>PKTABLE_SCHEM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKTABLE_QUALIFIER</para>
            </TD>
            <TD>
              <para>FK_TABLE_CAT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKTABLE_OWNER</para>
            </TD>
            <TD>
              <para>FKTABLE_SCHEM</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following table lists the columns in the result set. Additional columns beyond column 14 (REMARKS) can be defined by the driver. An application should gain access to driver-specific columns by counting down from the end of the result set instead of specifying an explicit ordinal position. For more information, see <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>.</para>
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
              <para>PKTABLE_CAT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Primary key table catalog name; NULL if not applicable to the data source. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have catalogs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PKTABLE_SCHEM (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Varchar </para>
            </TD>
            <TD>
              <para>Primary key table schema name; NULL if not applicable to the data source. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have schemas.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PKTABLE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Primary key table name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PKCOLUMN_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Primary key column name. The driver returns an empty string for a column that does not have a name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKTABLE_CAT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Foreign key table catalog name; NULL if not applicable to the data source. If a driver supports catalogs for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have catalogs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKTABLE_SCHEM (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Varchar </para>
            </TD>
            <TD>
              <para>Foreign key table schema name; NULL if not applicable to the data source. If a driver supports schemas for some tables but not for others, such as when the driver retrieves data from different DBMSs, it returns an empty string ("") for those tables that do not have schemas.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKTABLE_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Foreign key table name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKCOLUMN_NAME (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Foreign key column name. The driver returns an empty string for a column that does not have a name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>KEY_SEQ (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>9</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>Column sequence number in key (starting with 1).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>UPDATE_RULE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Action to be applied to the foreign key when the SQL operation is <legacyBold>UPDATE</legacyBold>. Can have one of the following values. (The referenced table is the table that has the primary key; the referencing table is the table that has the foreign key.)</para>
              <para>SQL_CASCADE: When the primary key of the referenced table is updated, the foreign key of the referencing table is also updated. </para>
              <para>SQL_NO_ACTION: If an update of the primary key of the referenced table would cause a "dangling reference" in the referencing table (that is, rows in the referencing table would have no counterparts in the referenced table), the update is rejected. If an update of the foreign key of the referencing table would introduce a value that does not exist as a value of the primary key of the referenced table, the update is rejected. (This action is the same as the SQL_RESTRICT action in ODBC 2<legacyItalic>.x</legacyItalic>.)</para>
              <para>SQL_SET_NULL: When one or more rows in the referenced table are updated in such a way that one or more components of the primary key are changed, the components of the foreign key in the referencing table that correspond to the changed components of the primary key are set to NULL in all matching rows of the referencing table.</para>
              <para>SQL_SET_DEFAULT: When one or more rows in the referenced table are updated in such a way that one or more components of the primary key are changed, the components of the foreign key in the referencing table that correspond to the changed components of the primary key are set to the applicable default values in all matching rows of the referencing table.</para>
              <para>NULL if not applicable to the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DELETE_RULE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Action to be applied to the foreign key when the SQL operation is <legacyBold>DELETE</legacyBold>. Can have one of the following values. (The referenced table is the table that has the primary key; the referencing table is the table that has the foreign key.)</para>
              <para>SQL_CASCADE: When a row in the referenced table is deleted, all the matching rows in the referencing tables are also deleted.</para>
              <para>SQL_NO_ACTION: If a delete of a row in the referenced table would cause a "dangling reference" in the referencing table (that is, rows in the referencing table would have no counterparts in the referenced table), the update is rejected. (This action is the same as the SQL_RESTRICT action in ODBC 2<legacyItalic>.x</legacyItalic>.)</para>
              <para>SQL_SET_NULL: When one or more rows in the referenced table are deleted, each component of the foreign key of the referencing table is set to NULL in all matching rows of the referencing table.</para>
              <para>SQL_SET_DEFAULT: When one or more rows in the referenced table are deleted, each component of the foreign key of the referencing table is set to the applicable default in all matching rows of the referencing table.</para>
              <para>NULL if not applicable to the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FK_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>12</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Foreign key name. NULL if not applicable to the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PK_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>13</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Primary key name. NULL if not applicable to the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEFERRABILITY (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>14</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>As illustrated in the following table, this example uses three tables, named ORDERS, LINES, and CUSTOMERS.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ORDERS</para>
            </TD>
            <TD>
              <para>LINES</para>
            </TD>
            <TD>
              <para>CUSTOMERS</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ORDERID</para>
            </TD>
            <TD>
              <para>ORDERID</para>
            </TD>
            <TD>
              <para>CUSTID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CUSTID</para>
            </TD>
            <TD>
              <para>LINES</para>
            </TD>
            <TD>
              <para>NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OPENDATE</para>
            </TD>
            <TD>
              <para>PARTID</para>
            </TD>
            <TD>
              <para>ADDRESS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SALESPERSON</para>
            </TD>
            <TD>
              <para>QUANTITY</para>
            </TD>
            <TD>
              <para>PHONE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>STATUS</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>In the ORDERS table, CUSTID identifies the customer to whom the sale has been made. It is a foreign key that refers to CUSTID in the CUSTOMERS table.</para>
      <para>In the LINES table, ORDERID identifies the sales order with which the line item is associated. It is a foreign key that refers to ORDERID in the ORDERS table.</para>
      <para>This example calls <legacyBold>SQLPrimaryKeys</legacyBold> to get the primary key of the ORDERS table. The result set will have one row; the significant columns are shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>TABLE_NAME</para>
            </TD>
            <TD>
              <para>COLUMN_NAME</para>
            </TD>
            <TD>
              <para>KEY_SEQ</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ORDERS</para>
            </TD>
            <TD>
              <para>ORDERID</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Next, the example calls <legacyBold>SQLForeignKeys</legacyBold> to get the foreign keys in other tables that reference the primary key of the ORDERS table. The result set will have one row; the significant columns are shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>PKTABLE_NAME</para>
            </TD>
            <TD>
              <para>PKCOLUMN_NAME</para>
            </TD>
            <TD>
              <para>FKTABLE_NAME</para>
            </TD>
            <TD>
              <para>FKCOLUMN_NAME</para>
            </TD>
            <TD>
              <para>KEY_SEQ</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ORDERS</para>
            </TD>
            <TD>
              <para>CUSTID</para>
            </TD>
            <TD>
              <para>LINES</para>
            </TD>
            <TD>
              <para>CUSTID</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Finally, the example calls <legacyBold>SQLForeignKeys</legacyBold> to get the foreign keys in the ORDERS table that refer to the primary keys of other tables. The result set will have one row; the significant columns are shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>PKTABLE_NAME</para>
            </TD>
            <TD>
              <para>PKCOLUMN_NAME</para>
            </TD>
            <TD>
              <para>FKTABLE_NAME</para>
            </TD>
            <TD>
              <para>FKCOLUMN_NAME</para>
            </TD>
            <TD>
              <para>KEY_SEQ</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CUSTOMERS</para>
            </TD>
            <TD>
              <para>CUSTID</para>
            </TD>
            <TD>
              <para>ORDERS</para>
            </TD>
            <TD>
              <para>CUSTID</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <code>#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1

LPSTR   szTable;              /* Table to display */

UCHAR szPkTable[TAB_LEN];   /* Primary key table name */
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */
UCHAR szPkCol[COL_LEN];     /* Primary key column */
UCHAR szFkCol[COL_LEN];     /* Foreign key column */

SQLHSTMT      hstmt;
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;
SQLSMALLINT   iKeySeq;
SQLRETURN     retcode;

// Bind the columns that describe the primary and foreign keys.
// Ignore the table schema, name, and catalog for this example.

SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &amp;cbPkTable);
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &amp;cbPkCol);
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &amp;iKeySeq, TAB_LEN, &amp;cbKeySeq);
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &amp;cbFkTable);
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &amp;cbFkCol);

strcpy_s(szTable, sizeof(szTable), "ORDERS");

/* Get the names of the columns in the primary key. */

retcode = SQLPrimaryKeys(hstmt,
         NULL, 0,             /* Catalog name */
         NULL, 0,             /* Schema name */
         szTable, SQL_NTS);   /* Table name */

while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {

   /* Fetch and display the result set. This will be a list of the */
   /* columns in the primary key of the ORDERS table. */

   retcode = SQLFetch(hstmt);
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,
      iKeySeq);
}

/* Close the cursor (the hstmt is still allocated). */

SQLFreeStmt(hstmt, SQL_CLOSE);

/* Get all the foreign keys that refer to ORDERS primary key.*/ 

retcode = SQLForeignKeys(hstmt,
         NULL, 0,            /* Primary catalog */
         NULL, 0,            /* Primary schema */
         szTable, SQL_NTS,   /* Primary table */
         NULL, 0,            /* Foreign catalog */
         NULL, 0,            /* Foreign schema */
         NULL, 0);           /* Foreign table */

while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {

/* Fetch and display the result set. This will be all of the */
/* foreign keys in other tables that refer to the ORDERS */
/* primary key. */

   retcode = SQLFetch(hstmt);
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
      fprintf(out, "%-s ( %-s ) &lt;-- %-s ( %-s )\n", szPkTable,
               szPkCol, szFkTable, szFkCol);
}

/* Close the cursor (the hstmt is still allocated). */

SQLFreeStmt(hstmt, SQL_CLOSE);

/* Get all the foreign keys in the ORDERS table. */

retcode = SQLForeignKeys(hstmt,
         NULL, 0,             /* Primary catalog */
         NULL, 0,             /* Primary schema */
         NULL, 0,             /* Primary table */
         NULL, 0,             /* Foreign catalog */
         NULL, 0,             /* Foreign schema */
         szTable, SQL_NTS);   /* Foreign table */

while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {

/* Fetch and display the result set. This will be all of the */
/* primary keys in other tables that are referred to by foreign */
/* keys in the ORDERS table. */

   retcode = SQLFetch(hstmt);
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
      fprintf(out, "%-s ( %-s )--&gt; %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);
}

/* Free the hstmt. */
SQLFreeStmt(hstmt, SQL_DROP);</code>
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
              <para>Returning the columns of a primary key</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys Function</legacyLink>
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
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>