---
title: "SQLGetTypeInfo Function"
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
  - SQLGetTypeInfo
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
caps.latest.revision: 20
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetTypeInfo Function
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
          <legacyBold>SQLGetTypeInfo</legacyBold> returns information about data types supported by the data source. The driver returns the information in the form of an SQL result set. The data types are intended for use in Data Definition Language (DDL) statements.</para>
        <alert class="important">
          <para>Applications must use the type names returned in the TYPE_NAME column of the <legacyBold>SQLGetTypeInfo</legacyBold> result set in <legacyBold>ALTER TABLE</legacyBold> and <legacyBold>CREATE TABLE</legacyBold> statements. <legacyBold>SQLGetTypeInfo</legacyBold> may return more than one row with the same value in the DATA_TYPE column.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetTypeInfo</legacyBold>(
     SQLHSTMT      <parameterReference>StatementHandle</parameterReference>,
     SQLSMALLINT   <parameterReference>DataType</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle for the result set.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The SQL data type. This must be one of the values in the <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> section of Appendix D: Data Types, or a driver-specific SQL data type. SQL_ALL_TYPES specifies that information about all data types should be returned.</para>
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
      <para>When <legacyBold>SQLGetTypeInfo</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetTypeInfo </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>A specified statement attribute was invalid because of implementation working conditions, so a similar value was temporarily substituted. (Call <legacyBold>SQLGetStmtAttr</legacyBold> to determine the temporarily substituted value.) The substitute value is valid for the <legacyItalic>StatementHandle</legacyItalic> until the cursor is closed. The statement attributes that can be changed are: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT, and SQL_ATTR_SIMULATE_CURSOR. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>A cursor was open on the <legacyItalic>StatementHandle,</legacyItalic> and <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called. This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA, and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
              <para>A result set was open on the <legacyItalic>StatementHandle</legacyItalic>, but <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had not been called.</para>
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
              <para>The associated connection failed during the execution of this function and the state of the transaction cannot be determined.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause. </para>
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
              <para>HY004</para>
            </TD>
            <TD>
              <para>Invalid SQL data type</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>DataType</legacyItalic> was neither a valid ODBC SQL data type identifier nor a driver-specific data type identifier supported by the driver.</para>
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
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>, then the function was called and, before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The function was called and, before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLGetTypeInfo</unmanagedCodeEntityReference> function was called.</para>
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
              <para>(DM) The driver corresponding to the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
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
        <legacyBold>SQLGetTypeInfo</legacyBold> returns the results as a standard result set, ordered by DATA_TYPE and then by how closely the data type maps to the corresponding ODBC SQL data type. Data types defined by the data source take precedence over user-defined data types. Consequently, the sort order is not necessarily consistent but can be generalized as DATA_TYPE first, followed by TYPE_NAME, both ascending. For example, suppose that a data source defined INTEGER and COUNTER data types, where COUNTER is auto-incrementing, and that a user-defined data type WHOLENUM has also been defined. These would be returned in the order INTEGER, WHOLENUM, and COUNTER, because WHOLENUM maps closely to the ODBC SQL data type SQL_INTEGER, while the auto-incrementing data type, even though supported by the data source, does not map closely to an ODBC SQL data type. For information about how this information might be used, see <legacyLink xlink:href="96ac9859-5976-4b06-ae1f-2fec3231e266">DDL Statements</legacyLink>.</para>
      <para>If the <legacyItalic>DataType</legacyItalic> argument specifies a data type which is valid for the version of ODBC supported by the driver, but is not supported by the driver, then it will return an empty result set. </para>
      <alert class="note">
        <para>For more information about the general use, arguments, and returned data of ODBC catalog functions, see <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
      </alert>
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
              <para>PRECISION</para>
            </TD>
            <TD>
              <para>COLUMN_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MONEY</para>
            </TD>
            <TD>
              <para>FIXED_PREC_SCALE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AUTO_INCREMENT</para>
            </TD>
            <TD>
              <para>AUTO_UNIQUE_VALUE</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following columns have been added to the results set returned by <legacyBold>SQLGetTypeInfo</legacyBold> for ODBC 3.<legacyItalic>x</legacyItalic>:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_DATA_TYPE</para>
        </listItem>
        <listItem>
          <para>INTERVAL_PRECISION</para>
        </listItem>
        <listItem>
          <para>SQL_DATETIME_SUB</para>
        </listItem>
        <listItem>
          <para>NUM_PREC_RADIX</para>
        </listItem>
      </list>
      <para>The following table lists the columns in the result set. Additional columns beyond column 19 (INTERVAL_PRECISION) can be defined by the driver. An application should gain access to driver-specific columns by counting down from the end of the result set rather than specifying an explicit ordinal position. For more information, see <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>.</para>
      <alert class="note">
        <para>  <legacyBold>SQLGetTypeInfo</legacyBold> might not return all data types. For example, a driver might not return user-defined data types. Applications can use any valid data type, regardless of whether it is returned by <legacyBold>SQLGetTypeInfo</legacyBold>. The data types returned by <legacyBold>SQLGetTypeInfo</legacyBold> are those supported by the data source. They are intended for use in Data Definition Language (DDL) statements. Drivers can return result-set data using data types other than the types returned by <legacyBold>SQLGetTypeInfo</legacyBold>. In creating the result set for a catalog function, the driver might use a data type that is not supported by the data source.</para>
      </alert>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Column name</para>
            </TD>
            <TD>
              <para>Column </para>
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
              <para>TYPE_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Varchar not NULL</para>
            </TD>
            <TD>
              <para>Data source–dependent data-type name; for example, "CHAR()", "VARCHAR()", "MONEY", "LONG VARBINARY", or "CHAR ( ) FOR BIT DATA". Applications must use this name in <legacyBold>CREATE TABLE</legacyBold> and <legacyBold>ALTER TABLE</legacyBold> statements.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DATA_TYPE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>SQL data type. This can be an ODBC SQL data type or a driver-specific SQL data type. For datetime or interval data types, this column returns the concise data type (such as SQL_TYPE_TIME or SQL_INTERVAL_YEAR_TO_MONTH). For a list of valid ODBC SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink> in Appendix D: Data Types. For information about driver-specific SQL data types, see the driver's documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COLUMN_SIZE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>The maximum column size that the server supports for this data type. For numeric data, this is the maximum precision. For string data, this is the length in characters. For datetime data types, this is the length in characters of the string representation (assuming the maximum allowed precision of the fractional seconds component). NULL is returned for data types where column size is not applicable. For interval data types, this is the number of characters in the character representation of the interval literal (as defined by the interval leading precision; see <legacyLink xlink:href="e9eb38d8-f9db-4401-8c62-aa394054cbbf">Interval Data Type Length</legacyLink> in Appendix D: Data Types).</para>
              <para>For more information on column size, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LITERAL_PREFIX (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Character or characters used to prefix a literal; for example, a single quotation mark (') for character data types or 0x for binary data types; NULL is returned for data types where a literal prefix is not applicable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LITERAL_SUFFIX (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Character or characters used to terminate a literal; for example, a single quotation mark (') for character data types; NULL is returned for data types where a literal suffix is not applicable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE_PARAMS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>A list of keywords, separated by commas, corresponding to each parameter that the application may specify in parentheses when using the name that is returned in the TYPE_NAME field. The keywords in the list can be any of the following: length, precision, or scale. They appear in the order that the syntax requires them to be used. For example, CREATE_PARAMS for DECIMAL would be "precision,scale"; CREATE_PARAMS for VARCHAR would equal "length." NULL is returned if there are no parameters for the data type definition; for example, INTEGER.</para>
              <para>The driver supplies the CREATE_PARAMS text in the language of the country/region where it is used.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULLABLE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>Whether the data type accepts a NULL value:</para>
              <para>SQL_NO_NULLS if the data type does not accept NULL values.</para>
              <para>SQL_NULLABLE if the data type accepts NULL values.</para>
              <para>SQL_NULLABLE_UNKNOWN if it is not known whether the column accepts NULL values.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CASE_SENSITIVE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>Whether a character data type is case-sensitive in collations and comparisons:</para>
              <para>SQL_TRUE if the data type is a character data type and is case-sensitive.</para>
              <para>SQL_FALSE if the data type is not a character data type or is not case-sensitive.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SEARCHABLE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>9</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>How the data type is used in a <legacyBold>WHERE</legacyBold> clause:</para>
              <para>SQL_PRED_NONE if the column cannot be used in a <legacyBold>WHERE</legacyBold> clause. (This is the same as the SQL_UNSEARCHABLE value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_PRED_CHAR if the column can be used in a <legacyBold>WHERE</legacyBold> clause, but only with the <legacyBold>LIKE</legacyBold> predicate. (This is the same as the SQL_LIKE_ONLY value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_PRED_BASIC if the column can be used in a <legacyBold>WHERE</legacyBold> clause with all the comparison operators except <legacyBold>LIKE</legacyBold> (comparison, quantified comparison, <legacyBold>BETWEEN</legacyBold>, <legacyBold>DISTINCT</legacyBold>, <legacyBold>IN</legacyBold>, <legacyBold>MATCH</legacyBold>, and <legacyBold>UNIQUE</legacyBold>). (This is the same as the SQL_ALL_EXCEPT_LIKE value in ODBC 2.<legacyItalic>x</legacyItalic>.)</para>
              <para>SQL_SEARCHABLE if the column can be used in a <legacyBold>WHERE</legacyBold> clause with any comparison operator.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>UNSIGNED_ATTRIBUTE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Whether the data type is unsigned:</para>
              <para>SQL_TRUE if the data type is unsigned.</para>
              <para>SQL_FALSE if the data type is signed.</para>
              <para>NULL is returned if the attribute is not applicable to the data type or the data type is not numeric.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FIXED_PREC_SCALE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para>Smallint not NULL</para>
            </TD>
            <TD>
              <para>Whether the data type has predefined fixed precision and scale (which are data source–specific), such as a money data type:</para>
              <para>SQL_TRUE if it has predefined fixed precision and scale.</para>
              <para>SQL_FALSE if it does not have predefined fixed precision and scale.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AUTO_UNIQUE_VALUE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>12</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>Whether the data type is autoincrementing:</para>
              <para>SQL_TRUE if the data type is autoincrementing.</para>
              <para>SQL_FALSE if the data type is not autoincrementing.</para>
              <para>NULL is returned if the attribute is not applicable to the data type or the data type is not numeric.</para>
              <para>An application can insert values into a column having this attribute, but typically cannot update the values in the column. </para>
              <para>When an insert is made into an auto-increment column, a unique value is inserted into the column at insert time. The increment is not defined, but is data source–specific. An application should not assume that an auto-increment column starts at any particular point or increments by any particular value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOCAL_TYPE_NAME (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>13</para>
            </TD>
            <TD>
              <para>Varchar</para>
            </TD>
            <TD>
              <para>Localized version of the data source–dependent name of the data type. NULL is returned if a localized name is not supported by the data source. This name is intended for display only, such as in dialog boxes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MINIMUM_SCALE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>14</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>The minimum scale of the data type on the data source. If a data type has a fixed scale, the MINIMUM_SCALE and MAXIMUM_SCALE columns both contain this value. For example, an SQL_TYPE_TIMESTAMP column might have a fixed scale for fractional seconds. NULL is returned where scale is not applicable. For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MAXIMUM_SCALE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>15</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>The maximum scale of the data type on the data source. NULL is returned where scale is not applicable. If the maximum scale is not defined separately on the data source, but is instead defined to be the same as the maximum precision, this column contains the same value as the COLUMN_SIZE column. For more information, see <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink> in Appendix D: Data Types.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_TYPE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>16</para>
            </TD>
            <TD>
              <para>Smallint NOT NULL</para>
            </TD>
            <TD>
              <para>The value of the SQL data type as it appears in the SQL_DESC_TYPE field of the descriptor. This column is the same as the DATA_TYPE column, except for interval and datetime data types.</para>
              <para>For interval and datetime data types, the SQL_DATA_TYPE field in the result set will return SQL_INTERVAL or SQL_DATETIME, and the SQL_DATETIME_SUB field will return the subcode for the specific interval or datetime data type. (See <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.) </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATETIME_SUB (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>17</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>When the value of SQL_DATA_TYPE is SQL_DATETIME or SQL_INTERVAL, this column contains the datetime/interval subcode. For data types other than datetime and interval, this field is NULL.</para>
              <para>For interval or datetime data types, the SQL_DATA_TYPE field in the result set will return SQL_INTERVAL or SQL_DATETIME, and the SQL_DATETIME_SUB field will return the subcode for the specific interval or datetime data type. (See <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NUM_PREC_RADIX (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>18</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
            <TD>
              <para>If the data type is an approximate numeric type, this column contains the value 2 to indicate that COLUMN_SIZE specifies a number of bits. For exact numeric types, this column contains the value 10 to indicate that COLUMN_SIZE specifies a number of decimal digits. Otherwise, this column is NULL.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INTERVAL_PRECISION (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>19</para>
            </TD>
            <TD>
              <para>Smallint</para>
            </TD>
            <TD>
              <para>If the data type is an interval data type, then this column contains the value of the interval leading precision. (See <legacyLink xlink:href="eb73bd77-2e7e-4498-a266-4d7c990a0d56">Interval Data Type Precision</legacyLink> in Appendix D: Data Types.) Otherwise, this column is NULL.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Attribute information can apply to data types or to specific columns in a result set. <legacyBold>SQLGetTypeInfo</legacyBold> returns information about attributes associated with data types; <legacyBold>SQLColAttribute</legacyBold> returns information about attributes associated with columns in a result set.</para>
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
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="8c45c598-cb01-4789-a571-e93619a18ed9">SQLColAttribute Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a block of data or scrolling through a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a single row or a block of data in a forward-only direction</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning information about a driver or data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink> </para>
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