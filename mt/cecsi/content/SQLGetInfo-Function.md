---
title: SQLGetInfo Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetInfo
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo Function
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
          <legacyBold>SQLGetInfo</legacyBold> returns general information about the driver and data source associated with a connection.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetInfo</legacyBold>(
     SQLHDBC         <parameterReference>ConnectionHandle</parameterReference>,
     SQLUSMALLINT    <parameterReference>InfoType</parameterReference>,
     SQLPOINTER      <parameterReference>InfoValuePtr</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
     SQLSMALLINT *   <parameterReference>StringLengthPtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>ConnectionHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Connection handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>InfoType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>InfoValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the information. Depending on the <legacyItalic>InfoType</legacyItalic> requested, the information returned will be one of the following: a null-terminated character string, an SQLUSMALLINT value, an SQLUINTEGER bitmask, an SQLUINTEGER flag, a SQLUINTEGER binary value, or a SQLULEN value.</para>
          <para>If the <legacyItalic>InfoType</legacyItalic> argument is SQL_DRIVER_HDESC or SQL_DRIVER_HSTMT, the <legacyItalic>InfoValuePtr</legacyItalic> argument is both input and output. (See the SQL_DRIVER_HDESC or SQL_DRIVER_HSTMT descriptors later in this function description for more information.)</para>
          <para>If <legacyItalic>InfoValuePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>InfoValuePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>InfoValuePtr</legacyItalic> buffer. If the value in <legacyItalic>*InfoValuePtr</legacyItalic> is not a character string or if <legacyItalic>InfoValuePtr</legacyItalic> is a null pointer,<legacyItalic> </legacyItalic>the <legacyItalic>BufferLength</legacyItalic> argument is ignored. The driver assumes that the size of <legacyItalic>*InfoValuePtr</legacyItalic> is SQLUSMALLINT or SQLUINTEGER, based on the <legacyItalic>InfoType</legacyItalic>. If <legacyItalic>*InfoValuePtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLGetInfoW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number; if not, SQLSTATE HY090 (Invalid string or buffer length) is returned.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of bytes (excluding the null-termination character for character data) available to return in *<legacyItalic>InfoValuePtr</legacyItalic>.</para>
          <para>For character data, if the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the information in *<legacyItalic>InfoValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> bytes minus the length of a null-termination character and is null-terminated by the driver. </para>
          <para>For all other types of data, the value of <legacyItalic>BufferLength</legacyItalic> is ignored and the driver assumes the size of *<legacyItalic>InfoValuePtr</legacyItalic> is SQLUSMALLINT or SQLUINTEGER, depending on the <legacyItalic>InfoType</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <returnValue>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </returnValue>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLGetInfo</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLGetInfo</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>01004</para>
            </TD>
            <TD>
              <para>String data, right truncated</para>
            </TD>
            <TD>
              <para>The buffer *<legacyItalic>InfoValuePtr</legacyItalic> was not large enough to return all the requested information. Therefore, the information was truncated. The length of the requested information in its untruncated form is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08003</para>
            </TD>
            <TD>
              <para>Connection not open</para>
            </TD>
            <TD>
              <para>(DM) The type of information requested in <legacyItalic>InfoType</legacyItalic> requires an open connection. Of the information types reserved by ODBC, only SQL_ODBC_VER can be returned without an open connection.</para>
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
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or<unmanagedCodeEntityReference> SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>HY024</para>
            </TD>
            <TD>
              <para>Invalid attribute value</para>
            </TD>
            <TD>
              <para>(DM) The <legacyItalic>InfoType</legacyItalic> argument was SQL_DRIVER_HSTMT, and the value pointed to by <legacyItalic>InfoValuePtr</legacyItalic> was not a valid statement handle.</para>
              <para>(DM) The <legacyItalic>InfoType</legacyItalic> argument was SQL_DRIVER_HDESC, and the value pointed to by <legacyItalic>InfoValuePtr</legacyItalic> was not a valid descriptor handle.</para>
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
              <para>(DM) The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
              <para>(DM) The value specified for <legacyItalic>BufferLength</legacyItalic> was an odd number, and <legacyItalic>*InfoValuePtr </legacyItalic>was of a Unicode data type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY096</para>
            </TD>
            <TD>
              <para>Information type out of range</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>InfoType</legacyItalic> was not valid for the version of ODBC supported by the driver.</para>
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
              <para>Optional field not implemented</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>InfoType</legacyItalic> was a driver-specific value that is not supported by the driver.</para>
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
              <para>(DM) The driver that corresponds to the <legacyItalic>ConnectionHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The currently defined information types are shown in "Information Types," later in this section; it is expected that more will be defined to take advantage of different data sources. A range of information types is reserved by ODBC; driver developers must reserve values for their own driver-specific use from Open Group. <legacyBold>SQLGetInfo</legacyBold> performs no Unicode conversion or <legacyItalic>thunking</legacyItalic> (see <link xlink:href="c06902e4-721d-42e2-b818-05f0e18e4ce0">Appendix A: ODBC Error Codes</link> of the <legacyItalic>ODBC Programmer's Reference</legacyItalic>) for driver-defined <legacyItalic>InfoTypes</legacyItalic>. For more information, see <link xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</link>. The format of the information returned in *<legacyItalic>InfoValuePtr</legacyItalic> depends on the <legacyItalic>InfoType</legacyItalic> requested. <legacyBold>SQLGetInfo</legacyBold> will return information in one of five different formats:</para>
      <list class="bullet">
        <listItem>
          <para>A null-terminated character string</para>
        </listItem>
        <listItem>
          <para>An SQLUSMALLINT value</para>
        </listItem>
        <listItem>
          <para>An SQLUINTEGER bitmask</para>
        </listItem>
        <listItem>
          <para>An SQLUINTEGER value</para>
        </listItem>
        <listItem>
          <para>A SQLUINTEGER binary value</para>
        </listItem>
      </list>
      <para>The format of each of the following information types is noted in the type's description. The application must cast the value returned in *<legacyItalic>InfoValuePtr</legacyItalic> accordingly. For an example of how an application could retrieve data from a SQLUINTEGER bitmask, see "Code Example."</para>
      <para>A driver must return a value for each information type that is defined in the following tables. If an information type does not apply to the driver or data source, the driver returns one of the values listed in the following table.</para>
      <definitionTable>
        <definedTerm>Character string ("Y" or "N")</definedTerm>
        <definition>
          <para>"N"</para>
        </definition>
        <definedTerm>Character string (not "Y" or "N")</definedTerm>
        <definition>
          <para>Empty string</para>
        </definition>
        <definedTerm>SQLUSMALLINT</definedTerm>
        <definition>
          <para>0</para>
        </definition>
        <definedTerm>SQLUINTEGER bitmask or SQLUINTEGER binary value</definedTerm>
        <definition>
          <para>0L</para>
        </definition>
      </definitionTable>
      <para>For example, if a data source does not support procedures, <legacyBold>SQLGetInfo</legacyBold> returns the values listed in the following table for the values of <legacyItalic>InfoType</legacyItalic> that are related to procedures.</para>
      <definitionTable>
        <definedTerm>SQL_PROCEDURES</definedTerm>
        <definition>
          <para>"N"</para>
        </definition>
        <definedTerm>SQL_ACCESSIBLE_PROCEDURES</definedTerm>
        <definition>
          <para>"N"</para>
        </definition>
        <definedTerm>SQL_MAX_PROCEDURE_NAME_LEN</definedTerm>
        <definition>
          <para>0</para>
        </definition>
        <definedTerm>SQL_PROCEDURE_TERM</definedTerm>
        <definition>
          <para>Empty string</para>
        </definition>
      </definitionTable>
      <para>
        <legacyBold>SQLGetInfo</legacyBold> returns SQLSTATE HY096 (Invalid argument value) for values of <legacyItalic>InfoType</legacyItalic> that are in the range of information types reserved for use by ODBC but are not defined by the version of ODBC supported by the driver. To determine what version of ODBC a driver complies with, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DRIVER_ODBC_VER information type. <legacyBold>SQLGetInfo</legacyBold> returns SQLSTATE HYC00 (Optional feature not implemented) for values of <legacyItalic>InfoType</legacyItalic> that are in the range of information types reserved for driver-specific use but are not supported by the driver.</para>
      <para>All calls to <legacyBold>SQLGetInfo</legacyBold> require an open connection, except when the <legacyItalic>InfoType</legacyItalic> is SQL_ODBC_VER, which returns the version of the Driver Manager.</para>
    </content>
  </section>
  <section>
    <title>Information Types</title>
    <content>
      <para>This section lists the information types supported by <legacyBold>SQLGetInfo</legacyBold>. Information types are grouped categorically and listed alphabetically. Information types that were added or renamed for ODBC 3<legacyItalic>.x</legacyItalic> are also listed.</para>
    </content>
  </section>
  <section>
    <title>Driver Information</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the ODBC driver, such as the number of active statements, the data source name, and the interface standards compliance level:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_ACTIVE_ENVIRONMENTS</para>
            </TD>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_DBC_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_FILE_USAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_MODE</para>
            </TD>
            <TD>
              <para>SQL_GETDATA_EXTENSIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_NOTIFICATION</para>
            </TD>
            <TD>
              <para>SQL_INFO_SCHEMA_VIEWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_ROW_COUNT</para>
            </TD>
            <TD>
              <para>SQL_KEYSET_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_SUPPORT</para>
            </TD>
            <TD>
              <para>SQL_KEYSET_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_SOURCE_NAME</para>
            </TD>
            <TD>
              <para>SQL_MAX_ASYNC_CONCURRENT_STATEMENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_AWARE_POOLING_SUPPORTED</para>
            </TD>
            <TD>
              <para>SQL_MAX_CONCURRENT_ACTIVITIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HDBC</para>
            </TD>
            <TD>
              <para>SQL_MAX_DRIVER_CONNECTIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HDESC</para>
            </TD>
            <TD>
              <para>SQL_ODBC_INTERFACE_CONFORMANCE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HENV</para>
            </TD>
            <TD>
              <para>SQL_ODBC_STANDARD_CLI_CONFORMANCE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HLIB</para>
            </TD>
            <TD>
              <para>SQL_ODBC_VER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HSTMT</para>
            </TD>
            <TD>
              <para>SQL_PARAM_ARRAY_ROW_COUNTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_NAME</para>
            </TD>
            <TD>
              <para>SQL_PARAM_ARRAY_SELECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_ODBC_VER</para>
            </TD>
            <TD>
              <para>SQL_ROW_UPDATES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_VER</para>
            </TD>
            <TD>
              <para>SQL_SEARCH_PATTERN_ESCAPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>SQL_SERVER_NAME </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES2</para>
            </TD>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>When implementing <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference>, a driver can improve performance by minimizing the number of times that information is sent or requested from the server.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>DBMS Product Information</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the DBMS product, such as the DBMS name and version:</para>
      <para>SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER</para>
    </content>
  </section>
  <section>
    <title>Data Source Information</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the data source, such as cursor characteristics and transaction capabilities:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_ACCESSIBLE_PROCEDURES</para>
            </TD>
            <TD>
              <para>SQL_MULT_RESULT_SETS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ACCESSIBLE_TABLES</para>
            </TD>
            <TD>
              <para>SQL_MULTIPLE_ACTIVE_TXN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BOOKMARK_PERSISTENCE</para>
            </TD>
            <TD>
              <para>SQL_NEED_LONG_DATA_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_TERM</para>
            </TD>
            <TD>
              <para>SQL_NULL_COLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_COLLATION_SEQ</para>
            </TD>
            <TD>
              <para>SQL_PROCEDURE_TERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONCAT_NULL_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_SCHEMA_TERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_COMMIT_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_SCROLL_OPTIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_ROLLBACK_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_TABLE_TERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_SENSITIVITY</para>
            </TD>
            <TD>
              <para>SQL_TXN_CAPABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_SOURCE_READ_ONLY</para>
            </TD>
            <TD>
              <para>SQL_TXN_ISOLATION_OPTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DEFAULT_TXN_ISOLATION</para>
            </TD>
            <TD>
              <para>SQL_USER_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESCRIBE_PARAMETER</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Supported SQL</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the SQL statements supported by the data source. The SQL syntax of each feature described by these information types is the SQL-92 syntax. These information types do not exhaustively describe the entire SQL-92 grammar. Instead, they describe those parts of the grammar for which data sources typically offer different levels of support. Specifically, most of the DDL statements in SQL-92 are covered.</para>
      <para>Applications should determine the general level of supported grammar from the SQL_SQL_CONFORMANCE information type and use the other information types to determine variations from the stated standards compliance level.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_AGGREGATE_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_DROP_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_DOMAIN</para>
            </TD>
            <TD>
              <para>SQL_DROP_TRANSLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_SCHEMA</para>
            </TD>
            <TD>
              <para>SQL_DROP_VIEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_TABLE</para>
            </TD>
            <TD>
              <para>SQL_EXPRESSIONS_IN_ORDERBY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ANSI_SQL_DATETIME_LITERALS</para>
            </TD>
            <TD>
              <para>SQL_GROUP_BY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_LOCATION </para>
            </TD>
            <TD>
              <para>SQL_IDENTIFIER_CASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_NAME</para>
            </TD>
            <TD>
              <para>SQL_IDENTIFIER_QUOTE_CHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_NAME_SEPARATOR</para>
            </TD>
            <TD>
              <para>SQL_INDEX_KEYWORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_USAGE</para>
            </TD>
            <TD>
              <para>SQL_INSERT_STATEMENT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_COLUMN_ALIAS</para>
            </TD>
            <TD>
              <para>SQL_INTEGRITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CORRELATION_NAME</para>
            </TD>
            <TD>
              <para>SQL_KEYWORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_ASSERTION</para>
            </TD>
            <TD>
              <para>SQL_LIKE_ESCAPE_CLAUSE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_CHARACTER_SET</para>
            </TD>
            <TD>
              <para>SQL_NON_NULLABLE_COLUMNS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_COLLATION</para>
            </TD>
            <TD>
              <para>SQL_SQL_CONFORMANCE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_DOMAIN</para>
            </TD>
            <TD>
              <para>SQL_OJ_CAPABILITIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_SCHEMA</para>
            </TD>
            <TD>
              <para>SQL_ORDER_BY_COLUMNS_IN_SELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TABLE</para>
            </TD>
            <TD>
              <para>SQL_OUTER_JOINS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TRANSLATION</para>
            </TD>
            <TD>
              <para>SQL_PROCEDURES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DDL_INDEX</para>
            </TD>
            <TD>
              <para>SQL_QUOTED_IDENTIFIER_CASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_ASSERTION</para>
            </TD>
            <TD>
              <para>SQL_SCHEMA_USAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_CHARACTER_SET</para>
            </TD>
            <TD>
              <para>SQL_SPECIAL_CHARACTERS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_COLLATION</para>
            </TD>
            <TD>
              <para>SQL_SUBQUERIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_DOMAIN</para>
            </TD>
            <TD>
              <para>SQL_UNION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_SCHEMA</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQL Limits</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the limits applied to identifiers and clauses in SQL statements, such as the maximum lengths of identifiers and the maximum number of columns in a select list. Limitations can be imposed by either the driver or the data source.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_MAX_BINARY_LITERAL_LEN</para>
            </TD>
            <TD>
              <para>SQL_MAX_IDENTIFIER_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CATALOG_NAME_LEN</para>
            </TD>
            <TD>
              <para>SQL_MAX_INDEX_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CHAR_LITERAL_LEN</para>
            </TD>
            <TD>
              <para>SQL_MAX_PROCEDURE_NAME_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMN_NAME_LEN</para>
            </TD>
            <TD>
              <para>SQL_MAX_ROW_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_GROUP_BY</para>
            </TD>
            <TD>
              <para>SQL_MAX_ROW_SIZE_INCLUDES_LONG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_INDEX</para>
            </TD>
            <TD>
              <para>SQL_MAX_SCHEMA_NAME_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_ORDER_BY</para>
            </TD>
            <TD>
              <para>SQL_MAX_STATEMENT_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_SELECT</para>
            </TD>
            <TD>
              <para>SQL_MAX_TABLE_NAME_LEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_TABLE</para>
            </TD>
            <TD>
              <para>SQL_MAX_TABLES_IN_SELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CURSOR_NAME_LEN</para>
            </TD>
            <TD>
              <para>SQL_MAX_USER_NAME_LEN</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Scalar Function Information</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return information about the scalar functions supported by the data source and the driver. For more information about scalar functions, see <link xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</link>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_CONVERT_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_TIMEDATE_ADD_INTERVALS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_NUMERIC_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_TIMEDATE_DIFF_INTERVALS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_STRING_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_TIMEDATE_FUNCTIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SYSTEM_FUNCTIONS</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Conversion Information</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument return a list of the SQL data types to which the data source can convert the specified SQL data type with the <legacyBold>CONVERT</legacyBold> scalar function:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_CONVERT_BIGINT</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_LONGVARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_BINARY</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_LONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_BIT</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_NUMERIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_CHAR</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_REAL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DATE</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_SMALLINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DECIMAL</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_TIME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DOUBLE</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_TIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_FLOAT</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_TINYINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTEGER</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_VARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTERVAL_YEAR_MONTH</para>
            </TD>
            <TD>
              <para>SQL_CONVERT_VARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTERVAL_DAY_TIME</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Information Types Added for ODBC 3.x</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument have been added for ODBC 3<legacyItalic>.x</legacyItalic>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_ACTIVE_ENVIRONMENTS</para>
            </TD>
            <TD>
              <para>SQL_DRIVER_AWARE_POOLING_SUPPORTED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_AGGREGATE_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_DRIVER_HDESC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_DOMAIN</para>
            </TD>
            <TD>
              <para>SQL_DROP_ASSERTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_SCHEMA</para>
            </TD>
            <TD>
              <para>SQL_DROP_CHARACTER_SET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ANSI_SQL_DATETIME_LITERALS</para>
            </TD>
            <TD>
              <para>SQL_DROP_COLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_DBC_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_DROP_DOMAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_MODE</para>
            </TD>
            <TD>
              <para>SQL_DROP_SCHEMA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_NOTIFICATION</para>
            </TD>
            <TD>
              <para>SQL_DROP_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_ROW_COUNT</para>
            </TD>
            <TD>
              <para>SQL_DROP_TRANSLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_SUPPORT</para>
            </TD>
            <TD>
              <para>SQL_DROP_VIEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_NAME</para>
            </TD>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_COLLATION_SEQ</para>
            </TD>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTERVAL_YEAR_MONTH</para>
            </TD>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTERVAL_DAY_TIME</para>
            </TD>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_ASSERTION</para>
            </TD>
            <TD>
              <para>SQL_INFO_SCHEMA_VIEWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_CHARACTER_SET</para>
            </TD>
            <TD>
              <para>SQL_INSERT_STATEMENT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_COLLATION</para>
            </TD>
            <TD>
              <para>SQL_KEYSET_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_DOMAIN</para>
            </TD>
            <TD>
              <para>SQL_KEYSET_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_SCHEMA</para>
            </TD>
            <TD>
              <para>SQL_MAX_ASYNC_CONCURRENT_STATEMENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TABLE</para>
            </TD>
            <TD>
              <para>SQL_MAX_IDENTIFIER_LEN </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TRANSLATION</para>
            </TD>
            <TD>
              <para>SQL_PARAM_ARRAY_ROW_COUNTS </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_SENSITIVITY</para>
            </TD>
            <TD>
              <para>SQL_PARAM_ARRAY_SELECTS </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DDL_INDEX</para>
            </TD>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESCRIBE_PARAMETER</para>
            </TD>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DM_VER</para>
            </TD>
            <TD>
              <para>SQL_XOPEN_CLI_YEAR</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Information Types Renamed for ODBC 3.x</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument have been renamed for ODBC 3<legacyItalic>.x</legacyItalic>.</para>
      <definitionTable>
        <definedTerm>SQL_ACTIVE_CONNECTIONS</definedTerm>
        <definition>
          <para>SQL_MAX_DRIVER_CONNECTIONS</para>
        </definition>
        <definedTerm>SQL_ACTIVE_STATEMENTS</definedTerm>
        <definition>
          <para>SQL_MAX_CONCURRENT_ACTIVITIES</para>
        </definition>
        <definedTerm>SQL_MAX_OWNER_NAME_LEN</definedTerm>
        <definition>
          <para>SQL_MAX_SCHEMA_NAME_LEN</para>
        </definition>
        <definedTerm>SQL_MAX_QUALIFIER_NAME_LEN</definedTerm>
        <definition>
          <para>SQL_MAX_CATALOG_NAME_LEN</para>
        </definition>
        <definedTerm>SQL_ODBC_SQL_OPT_IEF</definedTerm>
        <definition>
          <para>SQL_INTEGRITY</para>
        </definition>
        <definedTerm>SQL_OWNER_TERM</definedTerm>
        <definition>
          <para>SQL_SCHEMA_TERM</para>
        </definition>
        <definedTerm>SQL_OWNER_USAGE</definedTerm>
        <definition>
          <para>SQL_SCHEMA_USAGE</para>
        </definition>
        <definedTerm>SQL_QUALIFIER_LOCATION</definedTerm>
        <definition>
          <para>SQL_CATALOG_LOCATION</para>
        </definition>
        <definedTerm>SQL_QUALIFIER_NAME_SEPARATOR</definedTerm>
        <definition>
          <para>SQL_CATALOG_NAME_SEPARATOR</para>
        </definition>
        <definedTerm>SQL_QUALIFIER_TERM</definedTerm>
        <definition>
          <para>SQL_CATALOG_TERM</para>
        </definition>
        <definedTerm>SQL_QUALIFIER_USAGE</definedTerm>
        <definition>
          <para>SQL_CATALOG_USAGE</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Information Types Deprecated in ODBC 3.x</title>
    <content>
      <para>The following values of the <legacyItalic>InfoType</legacyItalic> argument have been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3<legacyItalic>.x</legacyItalic> drivers must continue to support these information types for backward compatibility with ODBC 2<legacyItalic>.x</legacyItalic> applications. (For more information about these types, see <link xlink:href="57326f57-daba-46b6-b0be-6c97213b9ef1">SQLGetInfo Support</link> in Appendix G: Driver Guidelines for Backward Compatibility.)</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_FETCH_DIRECTION</para>
            </TD>
            <TD>
              <para>SQL_POS_OPERATIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_LOCK_TYPES</para>
            </TD>
            <TD>
              <para>SQL_POSITIONED_STATEMENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ODBC_API_CONFORMANCE</para>
            </TD>
            <TD>
              <para>SQL_SCROLL_CONCURRENCY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ODBC_SQL_CONFORMANCE</para>
            </TD>
            <TD>
              <para>SQL_STATIC_SENSITIVITY</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Information Type Descriptions</title>
    <content>
      <para>The following table alphabetically lists each information type, the version of ODBC in which it was introduced, and its description.</para>
      <definitionTable>
        <definedTerm>SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the user can execute all procedures returned by <legacyBold>SQLProcedures</legacyBold>; "N" if there may be procedures returned that the user cannot execute.</para>
        </definition>
        <definedTerm>SQL_ACCESSIBLE_TABLES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the user is guaranteed <legacyBold>SELECT</legacyBold> privileges to all tables returned by <legacyBold>SQLTables</legacyBold>; "N" if there may be tables returned that the user cannot access.</para>
        </definition>
        <definedTerm>SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of active environments that the driver can support. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating support for aggregation functions:</para>
          <para>SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM </para>
          <para>An SQL-92 Entry level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_ALTER_DOMAIN(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>ALTER DOMAIN</legacyBold> statement, as defined in SQL-92, supported by the data source. An SQL-92 Full level–compliant driver will always return all the bitmasks. A return value of "0" means that the <legacyBold>ALTER DOMAIN</legacyBold> statement is not supported. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_AD_ADD_DOMAIN_CONSTRAINT = Adding a domain constraint is supported (Full level)</para>
          <para>SQL_AD_ADD_DOMAIN_DEFAULT = &lt;alter domain&gt; &lt;set domain default clause&gt; is supported (Full level)</para>
          <para>SQL_AD_CONSTRAINT_NAME_DEFINITION = &lt;constraint name definition clause&gt; is supported for naming domain constraint (Intermediate level)</para>
          <para>SQL_AD_DROP_DOMAIN_CONSTRAINT = &lt;drop domain constraint clause&gt; is supported (Full level)</para>
          <para>SQL_AD_DROP_DOMAIN_DEFAULT = &lt;alter domain&gt; &lt;drop domain default clause&gt; is supported (Full level)</para>
          <para>The following bits specify the supported &lt;constraint attributes&gt; if &lt;add domain constraint&gt; is supported (the SQL_AD_ADD_DOMAIN_CONSTRAINT bit is set):</para>
          <para>SQL_AD_ADD_CONSTRAINT_DEFERRABLE (Full level)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (Full level)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (Full level)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (Full level)</para>
        </definition>
        <definedTerm>SQL_ALTER_TABLE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>ALTER TABLE</legacyBold> statement supported by the data source. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para> SQL_AT_ADD_COLUMN_COLLATION = &lt;add column&gt; clause is supported, with facility to specify column collation (Full level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_COLUMN_DEFAULT = &lt;add column&gt; clause is supported, with facility to specify column defaults (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_COLUMN_SINGLE = &lt;add column&gt; is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_CONSTRAINT = &lt;add column&gt; clause is supported, with facility to specify column constraints (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_TABLE_CONSTRAINT = &lt;add table constraint&gt; clause is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_CONSTRAINT_NAME_DEFINITION = &lt;constraint name definition&gt; is supported for naming column and table constraints (Intermediate level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_CASCADE = &lt;drop column&gt; CASCADE is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_DEFAULT = &lt;alter column&gt; &lt;drop column default clause&gt; is supported (Intermediate level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_RESTRICT = &lt;drop column&gt; RESTRICT is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)</para>
          <para>SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = &lt;drop column&gt; RESTRICT is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_SET_COLUMN_DEFAULT = &lt;alter column&gt; &lt;set column default clause&gt; is supported (Intermediate level) (ODBC 3.0)</para>
          <para>The following bits specify the support &lt;constraint attributes&gt; if specifying column or table constraints is supported (the SQL_AT_ADD_CONSTRAINT bit is set):</para>
          <para>SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (Full level) (ODBC 3.0)</para>
        </definition>
        <definedTerm>SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)</definedTerm>
        <definition>
          <para>A SQLUINTEGER value that indicates if the driver can execute functions asynchronously on the connection handle.</para>
          <para>SQL_ASYNC_DBC_CAPABLE = The driver can execute connection functions asynchronously.</para>
          <para>SQL_ASYNC_DBC_NOT_CAPABLE = The driver can not execute connection functions asynchronously.</para>
        </definition>
        <definedTerm>SQL_ASYNC_MODE(ODBC 3.0)</definedTerm>
        <definition>
          <para>A SQLUINTEGER value that indicates the level of asynchronous support in the driver:</para>
          <para>SQL_AM_CONNECTION = Connection level asynchronous execution is supported. Either all statement handles associated with a given connection handle are in asynchronous mode or all are in synchronous mode. A statement handle on a connection cannot be in asynchronous mode while another statement handle on the same connection is in synchronous mode, and vice versa.</para>
          <para>SQL_AM_STATEMENT = Statement level asynchronous execution is supported. Some statement handles associated with a connection handle can be in asynchronous mode, while other statement handles on the same connection are in synchronous mode.</para>
          <para>SQL_AM_NONE = Asynchronous mode is not supported.</para>
        </definition>
        <definedTerm>SQL_ASYNC_NOTIFICATION</definedTerm>
        <definition>
          <para>A SQLUINTEGER value that indicates if the driver supports asynchronous notification:</para>
          <list class="bullet">
            <listItem>
              <para>
                <languageKeyword>SQL_ASYNC_NOTIFICATION_CAPABLE</languageKeyword> Asynchronous execution notification is supported by the driver.</para>
            </listItem>
            <listItem>
              <para>
                <languageKeyword>SQL_ASYNC_NOTIFICATION_NOT_CAPABLE</languageKeyword> Asynchronous execution notification is not supported by the driver.</para>
            </listItem>
          </list>
          <para>There are two categories of ODBC asynchronous operations: connection level asynchronous operations and statement level asynchronous operations.  If a driver returns SQL_ASYNC_NOTIFICATION_CAPABLE, it must support notification for all APIs that it can execute asynchronously.</para>
        </definition>
        <definedTerm>SQL_BATCH_ROW_COUNT (ODBC 3.0)</definedTerm>
        <definition>
          <para>A SQLUINTEGER bitmask that enumerates the behavior of the driver with respect to the availability of row counts. The following bitmasks are used together with the information type:</para>
          <para>SQL_BRC_ROLLED_UP = Row counts for consecutive INSERT, DELETE, or UPDATE statements are rolled up into one. If this bit is not set, row counts are available for each statement.</para>
          <para>SQL_BRC_PROCEDURES = Row counts, if any, are available when a batch is executed in a stored procedure. If row counts are available, they can be rolled up or individually available, depending on the SQL_BRC_ROLLED_UP bit.</para>
          <para>SQL_BRC_EXPLICIT = Row counts, if any, are available when a batch is executed directly by calling <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. If row counts are available, they can be rolled up or individually available, depending on the SQL_BRC_ROLLED_UP bit.</para>
        </definition>
        <definedTerm>SQL_BATCH_SUPPORT (ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the driver's support for batches. The following bitmasks are used to determine which level is supported:</para>
          <para>SQL_BS_SELECT_EXPLICIT = The driver supports explicit batches that can have result-set generating statements.</para>
          <para>SQL_BS_ROW_COUNT_EXPLICIT = The driver supports explicit batches that can have row-count generating statements.</para>
          <para>SQL_BS_SELECT_PROC = The driver supports explicit procedures that can have result-set generating statements.</para>
          <para>SQL_BS_ROW_COUNT_PROC = The driver supports explicit procedures that can have row-count generating statements.</para>
        </definition>
        <definedTerm>SQL_BOOKMARK_PERSISTENCE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the operations through which bookmarks persist.</para>
          <para>The following bitmasks are used together with the flag to determine through which options bookmarks persist:</para>
          <para>SQL_BP_CLOSE = Bookmarks are valid after an application calls <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option, or <legacyBold>SQLCloseCursor</legacyBold> to close the cursor associated with a statement.</para>
          <para>SQL_BP_DELETE = The bookmark for a row is valid after that row has been deleted.</para>
          <para>SQL_BP_DROP = Bookmarks are valid after an application calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT to drop a statement.</para>
          <para>SQL_BP_TRANSACTION = Bookmarks are valid after an application commits or rolls back a transaction.</para>
          <para>SQL_BP_UPDATE = The bookmark for a row is valid after any column in that row has been updated, including key columns.</para>
          <para>SQL_BP_OTHER_HSTMT = A bookmark associated with one statement can be used with another statement. Unless SQL_BP_CLOSE or SQL_BP_DROP is specified, the cursor on the first statement must be open.</para>
        </definition>
        <definedTerm>SQL_CATALOG_LOCATION(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates the position of the catalog in a qualified table name:</para>
          <para>SQL_CL_STARTSQL_CL_END</para>
          <para>For example, an Xbase driver returns SQL_CL_START because the directory (catalog) name is at the start of the table name, as in \EMPDATA\EMP.DBF. An ORACLE Server driver returns SQL_CL_END because the catalog is at the end of the table name, as in ADMIN.EMP@EMPDATA.</para>
          <para>An SQL-92 Full level–conformant driver will always return SQL_CL_START. A value of 0 is returned if catalogs are not supported by the data source. To determine whether catalogs are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CATALOG_NAME information type.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_QUALIFIER_LOCATION.</para>
        </definition>
        <definedTerm>SQL_CATALOG_NAME(ODBC 3.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the server supports catalog names, or "N" if it does not.</para>
          <para>An SQL-92 Full level–conformant driver will always return "Y".</para>
        </definition>
        <definedTerm>SQL_CATALOG_NAME_SEPARATOR(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: the character or characters that the data source defines as the separator between a catalog name and the qualified name element that follows or precedes it. </para>
          <para>An empty string is returned if catalogs are not supported by the data source. To determine whether catalogs are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CATALOG_NAME information type. An SQL-92 Full level–conformant driver will always return ".".</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_QUALIFIER_NAME_SEPARATOR.</para>
        </definition>
        <definedTerm>SQL_CATALOG_TERM(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the data source vendor's name for a catalog; for example, "database" or "directory". This string can be in upper, lower, or mixed case.</para>
          <para>An empty string is returned if catalogs are not supported by the data source. To determine whether catalogs are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CATALOG_NAME information type. An SQL-92 Full level–conformant driver will always return "catalog".</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_QUALIFIER_TERM.</para>
        </definition>
        <definedTerm>SQL_CATALOG_USAGE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the statements in which catalogs can be used.</para>
          <para>The following bitmasks are used to determine where catalogs can be used:</para>
          <para>SQL_CU_DML_STATEMENTS = Catalogs are supported in all Data Manipulation Language statements: <legacyBold>SELECT</legacyBold>, <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and if supported, <legacyBold>SELECT FOR UPDATE</legacyBold> and positioned update and delete statements.</para>
          <para>SQL_CU_PROCEDURE_INVOCATION = Catalogs are supported in the ODBC procedure invocation statement.</para>
          <para>SQL_CU_TABLE_DEFINITION = Catalogs are supported in all table definition statements: <legacyBold>CREATE TABLE</legacyBold>, <legacyBold>CREATE VIEW</legacyBold>, <legacyBold>ALTER TABLE</legacyBold>, <legacyBold>DROP TABLE</legacyBold>, and <legacyBold>DROP VIEW</legacyBold>.</para>
          <para>SQL_CU_INDEX_DEFINITION = Catalogs are supported in all index definition statements: <legacyBold>CREATE INDEX</legacyBold> and <legacyBold>DROP INDEX</legacyBold>.</para>
          <para>SQL_CU_PRIVILEGE_DEFINITION = Catalogs are supported in all privilege definition statements: <legacyBold>GRANT</legacyBold> and <legacyBold>REVOKE</legacyBold>. </para>
          <para>A value of 0 is returned if catalogs are not supported by the data source. To determine whether catalogs are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CATALOG_NAME information type. An SQL-92 Full level–conformant driver will always return a bitmask with all of these bits set.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_QUALIFIER_USAGE.</para>
        </definition>
        <definedTerm>SQL_COLLATION_SEQ(ODBC 3.0)</definedTerm>
        <definition>
          <para>The name of the collation sequence. This is a character string that indicates the name of the default collation for the default character set for this server (for example, 'ISO 8859-1' or EBCDIC). If this is unknown, an empty string will be returned. An SQL-92 Full level–conformant driver will always return a non-empty string.</para>
        </definition>
        <definedTerm>SQL_COLUMN_ALIAS(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports column aliases; otherwise, "N". </para>
          <para>A column alias is an alternative name that can be specified for a column in the select list by using an AS clause. An SQL-92 Entry level–conformant driver will always return "Y".</para>
        </definition>
        <definedTerm>SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates how the data source handles the concatenation of NULL valued character data type columns with non-NULL valued character data type columns:</para>
          <para>SQL_CB_NULL = Result is NULL valued.</para>
          <para>SQL_CB_NON_NULL = Result is concatenation of non-NULL valued column or columns. </para>
          <para>An SQL-92 Entry level–conformant driver will always return SQL_CB_NULL.</para>
        </definition>
        <definedTerm>SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask. The bitmask indicates the conversions supported by the data source with the <legacyBold>CONVERT</legacyBold> scalar function for data of the type named in the <legacyItalic>InfoType</legacyItalic>. If the bitmask equals zero, the data source does not support any conversions from data of the named type, including conversion to the same data type.</para>
          <para>For example, to determine if a data source supports the conversion of SQL_INTEGER data to the SQL_BIGINT data type, an application calls <legacyBold>SQLGetInfo</legacyBold> with the <legacyItalic>InfoType</legacyItalic> of SQL_CONVERT_INTEGER. The application performs an <legacyBold>AND</legacyBold> operation with the returned bitmask and SQL_CVT_BIGINT. If the resulting value is nonzero, the conversion is supported. </para>
          <para>The following bitmasks are used to determine which conversions are supported:</para>
          <para>SQL_CVT_BIGINT (ODBC 1.0)SQL_CVT_BINARY (ODBC 1.0)SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5)SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0)SQL_CVT_DECIMAL (ODBC 1.0)SQL_CVT_DOUBLE (ODBC 1.0)SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0)SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARCHAR (ODBC 1.0)SQL_CVT_NUMERIC (ODBC 1.0)SQL_CVT_REAL ODBC 1.0)SQL_CVT_SMALLINT (ODBC 1.0)SQL_CVT_TIME (ODBC 1.0)SQL_CVT_TIMESTAMP (ODBC 1.0)SQL_CVT_TINYINT (ODBC 1.0)SQL_CVT_VARBINARY (ODBC 1.0)SQL_CVT_VARCHAR (ODBC 1.0)</para>
        </definition>
        <definedTerm>SQL_CONVERT_FUNCTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the scalar conversion functions supported by the driver and associated data source.</para>
          <para>The following bitmask is used to determine which conversion functions are supported:</para>
          <para>SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT</para>
        </definition>
        <definedTerm>SQL_CORRELATION_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates whether table correlation names are supported:</para>
          <para>SQL_CN_NONE = Correlation names are not supported.</para>
          <para>SQL_CN_DIFFERENT = Correlation names are supported but must differ from the names of the tables they represent.</para>
          <para>SQL_CN_ANY = Correlation names are supported and can be any valid user-defined name. </para>
          <para>An SQL-92 Entry level–conformant driver will always return SQL_CN_ANY.</para>
        </definition>
        <definedTerm>SQL_CREATE_ASSERTION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE ASSERTION</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CA_CREATE_ASSERTION</para>
          <para>The following bits specify the supported constraint attribute if the ability to specify constraint attributes explicitly is supported (see the SQL_ALTER_TABLE and SQL_CREATE_TABLE information types):</para>
          <para>SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE</para>
          <para>An SQL-92 Full level–conformant driver will always return all of these options as supported. A return value of "0" means that the <legacyBold>CREATE ASSERTION</legacyBold> statement is not supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_CHARACTER_SET(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE CHARACTER SET</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION</para>
          <para>An SQL-92 Full level–conformant driver will always return all of these options as supported. A return value of "0" means that the <legacyBold>CREATE CHARACTER SET</legacyBold> statement is not supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_COLLATION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE COLLATION</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_CCOL_CREATE_COLLATION </para>
          <para>An SQL-92 Full level–conformant driver will always return this option as supported. A return value of "0" means that the <legacyBold>CREATE COLLATION</legacyBold> statement is not supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_DOMAIN(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE DOMAIN</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CDO_CREATE_DOMAIN = The CREATE DOMAIN statement is supported (Intermediate level).</para>
          <para>SQL_CDO_CONSTRAINT_NAME_DEFINITION = &lt;constraint name definition&gt; is supported for naming domain constraints (Intermediate level).</para>
          <para>The following bits specify the ability to create column constraints:SQL_CDO_DEFAULT = Specifying domain constraints is supported (Intermediate level)SQL_CDO_CONSTRAINT = Specifying domain defaults is supported (Intermediate level)SQL_CDO_COLLATION = Specifying domain collation is supported (Full level)</para>
          <para>The following bits specify the supported constraint attributes if specifying domain constraints is supported (SQL_CDO_DEFAULT is set):</para>
          <para>SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (Full level)SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (Full level)SQL_CDO_CONSTRAINT_DEFERRABLE (Full level)SQL_CDO_CONSTRAINT_NON_DEFERRABLE (Full level)</para>
          <para>A return value of "0" means that the <legacyBold>CREATE DOMAIN</legacyBold> statement is not supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_SCHEMA(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE SCHEMA</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET </para>
          <para>An SQL-92 Intermediate level–conformant driver will always return the SQL_CS_CREATE_SCHEMA and SQL_CS_AUTHORIZATION options as supported. These must also be supported at the SQL-92 Entry level, but not necessarily as SQL statements. An SQL-92 Full level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_TABLE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE TABLE</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CT_CREATE_TABLE = The CREATE TABLE statement is supported. (Entry level)</para>
          <para>SQL_CT_TABLE_CONSTRAINT = Specifying table constraints is supported (FIPS Transitional level)</para>
          <para>SQL_CT_CONSTRAINT_NAME_DEFINITION = The &lt;constraint name definition&gt; clause is supported for naming column and table constraints (Intermediate level)</para>
          <para>The following bits specify the ability to create temporary tables:</para>
          <para>SQL_CT_COMMIT_PRESERVE = Deleted rows are preserved on commit. (Full level)SQL_CT_COMMIT_DELETE = Deleted rows are deleted on commit. (Full level)SQL_CT_GLOBAL_TEMPORARY = Global temporary tables can be created. (Full level)SQL_CT_LOCAL_TEMPORARY = Local temporary tables can be created. (Full level)</para>
          <para>The following bits specify the ability to create column constraints:</para>
          <para>SQL_CT_COLUMN_CONSTRAINT = Specifying column constraints is supported (FIPS Transitional level)SQL_CT_COLUMN_DEFAULT = Specifying column defaults is supported (FIPS Transitional level)SQL_CT_COLUMN_COLLATION = Specifying column collation is supported (Full level)</para>
          <para>The following bits specify the supported constraint attributes if specifying column or table constraints is supported:</para>
          <para>SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (Full level)SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (Full level)SQL_CT_CONSTRAINT_DEFERRABLE (Full level)SQL_CT_CONSTRAINT_NON_DEFERRABLE (Full level)</para>
        </definition>
        <definedTerm>SQL_CREATE_TRANSLATION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE TRANSLATION</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_CTR_CREATE_TRANSLATION</para>
          <para>An SQL-92 Full level–conformant driver will always return these options as supported. A return value of "0" means that the <legacyBold>CREATE TRANSLATION</legacyBold> statement is not supported.</para>
        </definition>
        <definedTerm>SQL_CREATE_VIEW(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>CREATE VIEW</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL </para>
          <para>A return value of "0" means that the <legacyBold>CREATE VIEW</legacyBold> statement is not supported.</para>
          <para>An SQL-92 Entry level–conformant driver will always return the SQL_CV_CREATE_VIEW and SQL_CV_CHECK_OPTION options as supported. </para>
          <para>An SQL-92 Full level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_CURSOR_COMMIT_BEHAVIOR(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates how a <legacyBold>COMMIT</legacyBold> operation affects cursors and prepared statements in the data source (the behavior of the data source when you commit a transaction).</para>
          <para>The value of this attribute will reflect the current state of the next setting: SQL_COPT_SS_PRESERVE_CURSORS.</para>
          <para>SQL_CB_DELETE = Close cursors and delete prepared statements. To use the cursor again, the application must reprepare and reexecute the statement.</para>
          <para>SQL_CB_CLOSE = Close cursors. For prepared statements, the application can call <legacyBold>SQLExecute</legacyBold> on the statement without calling <legacyBold>SQLPrepare</legacyBold> again. The default for the SQL ODBC driver is SQL_CB_CLOSE. This means that the SQL ODBC driver will close your cursor(s) when you commit a transaction.  </para>
          <para>SQL_CB_PRESERVE = Preserve cursors in the same position as before the <legacyBold>COMMIT</legacyBold> operation. The application can continue to fetch data, or it can close the cursor and re-execute the statement without re-preparing it.</para>
        </definition>
        <definedTerm>SQL_CURSOR_ROLLBACK_BEHAVIOR(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates how a <legacyBold>ROLLBACK</legacyBold> operation affects cursors and prepared statements in the data source:</para>
          <para>SQL_CB_DELETE = Close cursors and delete prepared statements. To use the cursor again, the application must reprepare and reexecute the statement.</para>
          <para>SQL_CB_CLOSE = Close cursors. For prepared statements, the application can call <legacyBold>SQLExecute</legacyBold> on the statement without calling <legacyBold>SQLPrepare</legacyBold> again.</para>
          <para>SQL_CB_PRESERVE = Preserve cursors in the same position as before the <legacyBold>ROLLBACK</legacyBold> operation. The application can continue to fetch data, or it can close the cursor and reexecute the statement without repreparing it.</para>
        </definition>
        <definedTerm>SQL_CURSOR_SENSITIVITY (ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates the support for cursor sensitivity:</para>
          <para>SQL_INSENSITIVE = All cursors on the statement handle show the result set without reflecting any changes that were made to it by any other cursor within the same transaction.</para>
          <para>SQL_UNSPECIFIED = It is unspecified whether cursors on the statement handle make visible the changes that were made to a result set by another cursor within the same transaction. Cursors on the statement handle may make visible none, some, or all such changes.</para>
          <para>SQL_SENSITIVE = Cursors are sensitive to changes that were made by other cursors within the same transaction.</para>
          <para>An SQL-92 Entry level–conformant driver will always return the SQL_UNSPECIFIED option as supported. </para>
          <para>An SQL-92 Full level–conformant driver will always return the SQL_INSENSITIVE option as supported.</para>
        </definition>
        <definedTerm>SQL_DATA_SOURCE_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the data source name that was used during connection. If the application called <legacyBold>SQLConnect</legacyBold>, this is the value of the <legacyItalic>szDSN</legacyItalic> argument. If the application called <legacyBold>SQLDriverConnect</legacyBold> or <legacyBold>SQLBrowseConnect</legacyBold>, this is the value of the DSN keyword in the connection string passed to the driver. If the connection string did not contain the <legacyBold>DSN</legacyBold> keyword (such as when it contains the <legacyBold>DRIVER</legacyBold> keyword), this is an empty string.</para>
        </definition>
        <definedTerm>SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string. "Y" if the data source is set to READ ONLY mode, "N" if it is otherwise.</para>
          <para>This characteristic pertains only to the data source itself; it is not a characteristic of the driver that enables access to the data source. A driver that is read/write can be used with a data source that is read-only. If a driver is read-only, all of its data sources must be read-only and must return SQL_DATA_SOURCE_READ_ONLY.</para>
        </definition>
        <definedTerm>SQL_DATABASE_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the name of the current database in use, if the data source defines a named object called "database".</para>
          <alert class="note">
            <para>In ODBC 3<legacyItalic>.x</legacyItalic>, the value returned for this <legacyItalic>InfoType</legacyItalic> can also be returned by calling <legacyBold>SQLGetConnectAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_CURRENT_CATALOG.</para>
          </alert>
        </definition>
        <definedTerm>SQL_DATETIME_LITERALS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the SQL-92 datetime literals supported by the data source. Note that these are the datetime literals listed in the SQL-92 specification and are separate from the datetime literal escape clauses defined by ODBC. For more information about the ODBC datetime literal escape clauses, see <link xlink:href="2b42a52a-6353-494c-a179-3a7533cd729f">Date, Time, and Timestamp Literals</link>.</para>
          <para>A FIPS Transitional level–conformant driver will always return the "1" value in the bitmask for the bits in the following list. A value of "0" means that SQL-92 datetime literals are not supported.</para>
          <para>The following bitmasks are used to determine which literals are supported:</para>
          <para>SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR</para>
          <para>SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND</para>
        </definition>
        <definedTerm>SQL_DBMS_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the name of the DBMS product accessed by the driver.</para>
        </definition>
        <definedTerm>SQL_DBMS_VER(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string that indicates the version of the DBMS product accessed by the driver. The version is of the form ##.##.####, where the first two digits are the major version, the next two digits are the minor version, and the last four digits are the release version. The driver must render the DBMS product version in this form but can also append the DBMS product-specific version. For example, "04.01.0000 Rdb 4.1".</para>
        </definition>
        <definedTerm>SQL_DDL_INDEX(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates support for creation and dropping of indexes:</para>
          <para>SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX </para>
        </definition>
        <definedTerm>SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates the default transaction isolation level supported by the driver or data source, or zero if the data source does not support transactions. The following terms are used to define transaction isolation levels:</para>
          <para>
            <legacyBold>Dirty Read   </legacyBold>Transaction 1 changes a row. Transaction 2 reads the changed row before transaction 1 commits the change. If transaction 1 rolls back the change, transaction 2 will have read a row that is considered to have never existed.</para>
          <para>
            <legacyBold>Nonrepeatable Read   </legacyBold>Transaction 1 reads a row. Transaction 2 updates or deletes that row and commits this change. If transaction 1 tries to reread the row, it will receive different row values or discover that the row has been deleted.</para>
          <para>
            <legacyBold>Phantom   </legacyBold>Transaction 1 reads a set of rows that satisfy some search criteria. Transaction 2 generates one or more rows (through either inserts or updates) that match the search criteria. If transaction 1 reexecutes the statement that reads the rows, it receives a different set of rows.</para>
          <para>If the data source supports transactions, the driver returns one of the following bitmasks:</para>
          <para>SQL_TXN_READ_UNCOMMITTED = Dirty reads, nonrepeatable reads, and phantoms are possible.</para>
          <para>SQL_TXN_READ_COMMITTED = Dirty reads are not possible. Nonrepeatable reads and phantoms are possible.</para>
          <para>SQL_TXN_REPEATABLE_READ = Dirty reads and nonrepeatable reads are not possible. Phantoms are possible.</para>
          <para>SQL_TXN_SERIALIZABLE = Transactions are serializable. Serializable transactions do not allow dirty reads, nonrepeatable reads, or phantoms.</para>
        </definition>
        <definedTerm>SQL_DESCRIBE_PARAMETER(ODBC 3.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if parameters can be described; "N", if not. </para>
          <para>An SQL-92 Full level–conformant driver will usually return "Y" because it will support the <legacyBold>DESCRIBE INPUT</legacyBold> statement. Because this does not directly specify the underlying SQL support, however, describing parameters might not be supported, even in a SQL-92 Full level–conformant driver.</para>
        </definition>
        <definedTerm>SQL_DM_VER(ODBC 3.0)</definedTerm>
        <definition>
          <para>A character string with the version of the Driver Manager. The version is of the form ##.##.####.####, where:</para>
          <para>The first set of two digits is the major ODBC version, as given by the constant SQL_SPEC_MAJOR.</para>
          <para>The second set of two digits is the minor ODBC version, as given by the constant SQL_SPEC_MINOR.</para>
          <para>The third set of four digits is the Driver Manager major build number.</para>
          <para>The last set of four digits is the Driver Manager minor build number.</para>
          <para>The Windows 7 Driver Manager version is 03.80. The Windows 8 Driver Manager version is 03.81.</para>
        </definition>
        <definedTerm>SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)</definedTerm>
        <definition>
          <para>A SQLUINTEGER value that indicates if the driver support driver-aware pooling. (For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>.</para>
          <para>SQL_DRIVER_AWARE_POOLING_CAPABLE indicates that the driver can support driver-aware pooling mechanism.</para>
          <para>SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE indicates that the driver cannot support driver-aware pooling mechanism.</para>
          <para>A driver does not need to implement SQL_DRIVER_AWARE_POOLING_SUPPORTED and the Driver Manager will not honor to the driver’s return value.</para>
        </definition>
        <definedTerm>SQL_DRIVER_HDBCSQL_DRIVER_HENV(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLULEN value, the driver's environment handle or connection handle, determined by the argument <legacyItalic>InfoType</legacyItalic>.</para>
          <para>These information types are implemented by the Driver Manager alone.</para>
        </definition>
        <definedTerm>SQL_DRIVER_HDESC(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLULEN value, the driver's descriptor handle determined by the Driver Manager's descriptor handle, which must be passed on input in *<legacyItalic>InfoValuePtr</legacyItalic> from the application. In this case, <legacyItalic>InfoValuePtr</legacyItalic> is both an input and output argument. The input descriptor handle passed in *<legacyItalic>InfoValuePtr</legacyItalic> must have been either explicitly or implicitly allocated on the <legacyItalic>ConnectionHandle</legacyItalic>. </para>
          <para>The application should make a copy of the Driver Manager's descriptor handle before it calls <legacyBold>SQLGetInfo</legacyBold> with this information type, to make sure that the handle is not overwritten on output.</para>
          <para>This information type is implemented by the Driver Manager alone.</para>
        </definition>
        <definedTerm>SQL_DRIVER_HLIB(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLULEN value, the <legacyItalic>hinst</legacyItalic> from the load library returned to the Driver Manager when it loaded the driver DLL on a Microsoft Windows operating system, or its equivalent on another operating system. The handle is valid only for the connection handle specified in the call to <legacyBold>SQLGetInfo</legacyBold>.</para>
          <para>This information type is implemented by the Driver Manager alone.</para>
        </definition>
        <definedTerm>SQL_DRIVER_HSTMT(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLULEN value, the driver's statement handle determined by the Driver Manager statement handle, which must be passed on input in *<legacyItalic>InfoValuePtr</legacyItalic> from the application. In this case, <legacyItalic>InfoValuePtr</legacyItalic> is both an input and an output argument. The input statement handle passed in *<legacyItalic>InfoValuePtr</legacyItalic> must have been allocated on the argument <legacyItalic>ConnectionHandle</legacyItalic>.</para>
          <para>The application should make a copy of the Driver Manager's statement handle before it calls <legacyBold>SQLGetInfo</legacyBold> with this information type, to ensure that the handle is not overwritten on output.</para>
          <para>This information type is implemented by the Driver Manager alone.</para>
        </definition>
        <definedTerm>SQL_DRIVER_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the file name of the driver used to access the data source.</para>
        </definition>
        <definedTerm>SQL_DRIVER_ODBC_VER(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string with the version of ODBC that the driver supports. The version is of the form ##.##, where the first two digits are the major version and the next two digits are the minor version. SQL_SPEC_MAJOR and SQL_SPEC_MINOR define the major and minor version numbers. For the version of ODBC described in this manual, these are 3 and 0, and the driver should return "03.00".</para>
          <para>The ODBC Driver Manager will not modify the return value of SQLGetInfo(SQL_DRIVER_ODBC_VER) to maintain backward compatibility for existing applications. The driver specifies which value will be returned. However, a driver that supports C data type extensibility must return 3.8 (or higher) when an application calls <unmanagedCodeEntityReference>SQLSetEnvAttr</unmanagedCodeEntityReference> to set SQL_ATTR_ODBC_VERSION to 3.8. For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
        </definition>
        <definedTerm>SQL_DRIVER_VER(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the version of the driver and optionally, a description of the driver. At a minimum, the version is of the form ##.##.####, where the first two digits are the major version, the next two digits are the minor version, and the last four digits are the release version.</para>
        </definition>
        <definedTerm>SQL_DROP_ASSERTION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP ASSERTION</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_DA_DROP_ASSERTION </para>
          <para>An SQL-92 Full level–conformant driver will always return this option as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_CHARACTER_SET(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP CHARACTER SET</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_DCS_DROP_CHARACTER_SET </para>
          <para>An SQL-92 Full level–conformant driver will always return this option as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_COLLATION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP COLLATION</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_DC_DROP_COLLATION </para>
          <para>An SQL-92 Full level–conformant driver will always return this option as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_DOMAIN(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP DOMAIN</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT </para>
          <para>An SQL-92 Intermediate level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_SCHEMA(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP SCHEMA</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT </para>
          <para>An SQL-92 Intermediate level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_TABLE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP TABLE</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT </para>
          <para>An FIPS Transitional level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_TRANSLATION(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP TRANSLATION</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmask is used to determine which clauses are supported:</para>
          <para>SQL_DTR_DROP_TRANSLATION </para>
          <para>An SQL-92 Full level–conformant driver will always return this option as supported.</para>
        </definition>
        <definedTerm>SQL_DROP_VIEW(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>DROP VIEW</legacyBold> statement, as defined in SQL-92, supported by the data source.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT </para>
          <para>An FIPS Transitional level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a dynamic cursor that are supported by the driver. This bitmask contains the first subset of attributes; for the second subset, see SQL_DYNAMIC_CURSOR_ATTRIBUTES2.</para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA1_NEXT = A <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_NEXT is supported in a call to <legacyBold>SQLFetchScroll</legacyBold> when the cursor is a dynamic cursor.</para>
          <para>SQL_CA1_ABSOLUTE = <legacyItalic>FetchOrientation</legacyItalic> arguments of SQL_FETCH_FIRST, SQL_FETCH_LAST, and SQL_FETCH_ABSOLUTE are supported in a call to <legacyBold>SQLFetchScroll</legacyBold> when the cursor is a dynamic cursor. (The rowset that will be fetched is independent of the current cursor position.) </para>
          <para>SQL_CA1_RELATIVE = <legacyItalic>FetchOrientation</legacyItalic> arguments of SQL_FETCH_PRIOR and SQL_FETCH_RELATIVE are supported in a call to <legacyBold>SQLFetchScroll</legacyBold> when the cursor is a dynamic cursor. (The rowset that will be fetched depends on the current cursor position. Note that this is separated from SQL_FETCH_NEXT because in a forward-only cursor, only SQL_FETCH_NEXT is supported.) </para>
          <para>SQL_CA1_BOOKMARK = A <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_BOOKMARK is supported in a call to <legacyBold>SQLFetchScroll</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_LOCK_EXCLUSIVE = A <legacyItalic>LockType</legacyItalic> argument of SQL_LOCK_EXCLUSIVE is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor.</para>
          <para>SQL_CA1_LOCK_NO_CHANGE = A <legacyItalic>LockType</legacyItalic> argument of SQL_LOCK_NO_CHANGE is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_LOCK_UNLOCK = A <legacyItalic>LockType</legacyItalic> argument of SQL_LOCK_UNLOCK is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor.</para>
          <para>SQL_CA1_POS_POSITION = An <legacyItalic>Operation</legacyItalic> argument of SQL_POSITION is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor.</para>
          <para>SQL_CA1_POS_UPDATE = An <legacyItalic>Operation</legacyItalic> argument of SQL_UPDATE is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_POS_DELETE = An <legacyItalic>Operation</legacyItalic> argument of SQL_DELETE is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_POS_REFRESH = An <legacyItalic>Operation</legacyItalic> argument of SQL_REFRESH is supported in a call to <legacyBold>SQLSetPos</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_POSITIONED_UPDATE = An UPDATE WHERE CURRENT OF SQL statement is supported when the cursor is a dynamic cursor. (An SQL-92 Entry level–conformant driver will always return this option as supported.)</para>
          <para>SQL_CA1_POSITIONED_DELETE = A DELETE WHERE CURRENT OF SQL statement is supported when the cursor is a dynamic cursor. (An SQL-92 Entry level–conformant driver will always return this option as supported.)</para>
          <para>SQL_CA1_SELECT_FOR_UPDATE = A SELECT FOR UPDATE SQL statement is supported when the cursor is a dynamic cursor. (An SQL-92 Entry level–conformant driver will always return this option as supported.)</para>
          <para>SQL_CA1_BULK_ADD = An <legacyItalic>Operation</legacyItalic> argument of SQL_ADD is supported in a call to <legacyBold>SQLBulkOperations</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_BULK_UPDATE_BY_BOOKMARK = An <legacyItalic>Operation</legacyItalic> argument of SQL_UPDATE_BY_BOOKMARK is supported in a call to <legacyBold>SQLBulkOperations</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_BULK_DELETE_BY_BOOKMARK = An <legacyItalic>Operation</legacyItalic> argument of SQL_DELETE_BY_BOOKMARK is supported in a call to <legacyBold>SQLBulkOperations</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>SQL_CA1_BULK_FETCH_BY_BOOKMARK = An <legacyItalic>Operation</legacyItalic> argument of SQL_FETCH_BY_BOOKMARK is supported in a call to <legacyBold>SQLBulkOperations</legacyBold> when the cursor is a dynamic cursor. </para>
          <para>An SQL-92 Intermediate level–conformant driver will usually return the SQL_CA1_NEXT, SQL_CA1_ABSOLUTE, and SQL_CA1_RELATIVE options as supported, because it supports scrollable cursors through the embedded SQL FETCH statement. Because this does not directly determine the underlying SQL support, however, scrollable cursors may not be supported, even for an SQL-92 Intermediate level–conformant driver.</para>
        </definition>
        <definedTerm>SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a dynamic cursor that are supported by the driver. This bitmask contains the second subset of attributes; for the first subset, see SQL_DYNAMIC_CURSOR_ATTRIBUTES1. </para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA2_READ_ONLY_CONCURRENCY = A read-only dynamic cursor, in which no updates are allowed, is supported. (The SQL_ATTR_CONCURRENCY statement attribute can be SQL_CONCUR_READ_ONLY for a dynamic cursor). </para>
          <para>SQL_CA2_LOCK_CONCURRENCY = A dynamic cursor that uses the lowest level of locking sufficient to make sure that the row can be updated is supported. (The SQL_ATTR_CONCURRENCY statement attribute can be SQL_CONCUR_LOCK for a dynamic cursor.) These locks must be consistent with the transaction isolation level set by the SQL_ATTR_TXN_ISOLATION connection attribute.</para>
          <para>SQL_CA2_OPT_ROWVER_CONCURRENCY = A dynamic cursor that uses the optimistic concurrency control comparing row versions is supported. (The SQL_ATTR_CONCURRENCY statement attribute can be SQL_CONCUR_ROWVER for a dynamic cursor.) </para>
          <para>SQL_CA2_OPT_VALUES_CONCURRENCY = A dynamic cursor that uses the optimistic concurrency control comparing values is supported. (The SQL_ATTR_CONCURRENCY statement attribute can be SQL_CONCUR_VALUES for a dynamic cursor.) </para>
          <para>SQL_CA2_SENSITIVITY_ADDITIONS = Added rows are visible to a dynamic cursor; the cursor can scroll to those rows. (Where these rows are added to the cursor is driver-dependent.) </para>
          <para>SQL_CA2_SENSITIVITY_DELETIONS = Deleted rows are no longer available to a dynamic cursor, and do not leave a "hole" in the result set; after the dynamic cursor scrolls from a deleted row, it cannot return to that row. </para>
          <para>SQL_CA2_SENSITIVITY_UPDATES = Updates to rows are visible to a dynamic cursor; if the dynamic cursor scrolls from and returns to an updated row, the data returned by the cursor is the updated data, not the original data. </para>
          <para>SQL_CA2_MAX_ROWS_SELECT = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>SELECT</legacyBold> statements when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_MAX_ROWS_INSERT = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>INSERT</legacyBold> statements when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_MAX_ROWS_DELETE = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>DELETE</legacyBold> statements when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_MAX_ROWS_UPDATE = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>UPDATE</legacyBold> statements when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_MAX_ROWS_CATALOG = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>CATALOG</legacyBold> result sets when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_MAX_ROWS_AFFECTS_ALL = The SQL_ATTR_MAX_ROWS statement attribute affects <legacyBold>SELECT</legacyBold>, <legacyBold>INSERT</legacyBold>, <legacyBold>DELETE</legacyBold>, and <legacyBold>UPDATE</legacyBold> statements, and <legacyBold>CATALOG</legacyBold> result sets, when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_CRC_EXACT = The exact row count is available in the SQL_DIAG_CURSOR_ROW_COUNT diagnostic field when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_CRC_APPROXIMATE = An approximate row count is available in the SQL_DIAG_CURSOR_ROW_COUNT diagnostic field when the cursor is a dynamic cursor. </para>
          <para>SQL_CA2_SIMULATE_NON_UNIQUE = The driver does not guarantee that simulated positioned update or delete statements will affect only one row when the cursor is a dynamic cursor; it is the application's responsibility to guarantee this. (If a statement affects more than one row, <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns SQLSTATE 01001 [Cursor operation conflict].) To set this behavior, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_SIMULATE_CURSOR attribute set to SQL_SC_NON_UNIQUE. </para>
          <para>SQL_CA2_SIMULATE_TRY_UNIQUE = The driver tries to guarantee that simulated positioned update or delete statements will affect only one row when the cursor is a dynamic cursor. The driver always executes such statements, even if they might affect more than one row, such as when there is no unique key. (If a statement affects more than one row, <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns SQLSTATE 01001 [Cursor operation conflict].) To set this behavior, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_SIMULATE_CURSOR attribute set to SQL_SC_TRY_UNIQUE. </para>
          <para>SQL_CA2_SIMULATE_UNIQUE = The driver guarantees that simulated positioned update or delete statements will affect only one row when the cursor is a dynamic cursor. If the driver cannot guarantee this for a given statement, <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLPrepare</legacyBold> return SQLSTATE 01001 (Cursor operation conflict). To set this behavior, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> with the SQL_ATTR_SIMULATE_CURSOR attribute set to SQL_SC_UNIQUE.</para>
        </definition>
        <definedTerm>SQL_EXPRESSIONS_IN_ORDERBY(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports expressions in the <legacyBold>ORDER BY</legacyBold> list; "N" if it does not.</para>
        </definition>
        <definedTerm>SQL_FILE_USAGE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that indicates how a single-tier driver directly treats files in a data source:</para>
          <para>SQL_FILE_NOT_SUPPORTED = The driver is not a single-tier driver. For example, an ORACLE driver is a two-tier driver.</para>
          <para>SQL_FILE_TABLE = A single-tier driver treats files in a data source as tables. For example, an Xbase driver treats each Xbase file as a table.</para>
          <para>SQL_FILE_CATALOG = A single-tier driver treats files in a data source as a catalog. For example, a Microsoft Access driver treats each Microsoft Access file as a complete database.</para>
          <para>An application might use this to determine how users will select data. For example, Xbase users often think of data as stored in files, whereas ORACLE and Microsoft Access users generally think of data as stored in tables.</para>
          <para>When a user selects an Xbase data source, the application could display the Windows <legacyBold>File Open</legacyBold> common dialog box; when the user selects a Microsoft Access or ORACLE data source, the application could display a custom <legacyBold>Select Table</legacyBold> dialog box.</para>
        </definition>
        <definedTerm>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a forward-only cursor that are supported by the driver. This bitmask contains the first subset of attributes; for the second subset, see SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2. </para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK</para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (and substitute "forward-only cursor" for "dynamic cursor" in the descriptions). </para>
        </definition>
        <definedTerm>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a forward-only cursor that are supported by the driver. This bitmask contains the second subset of attributes; for the first subset, see SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1. </para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE </para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (and substitute "forward-only cursor" for "dynamic cursor" in the descriptions).</para>
        </definition>
        <definedTerm>SQL_GETDATA_EXTENSIONS(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating extensions to <legacyBold>SQLGetData</legacyBold>.</para>
          <para>The following bitmasks are used together with the flag to determine what common extensions the driver supports for <legacyBold>SQLGetData</legacyBold>:</para>
          <para>SQL_GD_ANY_COLUMN = <legacyBold>SQLGetData</legacyBold> can be called for any unbound column, including those before the last bound column. Note that the columns must be called in order of ascending column number unless SQL_GD_ANY_ORDER is also returned.</para>
          <para>SQL_GD_ANY_ORDER = <legacyBold>SQLGetData</legacyBold> can be called for unbound columns in any order. Note that <legacyBold>SQLGetData</legacyBold> can be called only for columns after the last bound column unless SQL_GD_ANY_COLUMN is also returned.</para>
          <para>SQL_GD_BLOCK = <legacyBold>SQLGetData</legacyBold> can be called for an unbound column in any row in a block (where the rowset size is greater than 1) of data after positioning to that row with <legacyBold>SQLSetPos</legacyBold>.</para>
          <para>SQL_GD_BOUND = <legacyBold>SQLGetData</legacyBold> can be called for bound columns in addition to unbound columns. A driver cannot return this value unless it also returns SQL_GD_ANY_COLUMN.</para>
          <para>SQL_GD_OUTPUT_PARAMS = <legacyBold>SQLGetData</legacyBold> can be called to return output parameter values. For more information, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
          <para>
            <legacyBold>SQLGetData</legacyBold> is required to return data only from unbound columns that occur after the last bound column, are called in order of increasing column number, and are not in a row in a block of rows.</para>
          <para>If a driver supports bookmarks (either fixed-length or variable-length), it must support calling <legacyBold>SQLGetData</legacyBold> on column 0. This support is required regardless of what the driver returns for a call to <legacyBold>SQLGetInfo</legacyBold> with the SQL_GETDATA_EXTENSIONS <legacyItalic>InfoType</legacyItalic>.</para>
        </definition>
        <definedTerm>SQL_GROUP_BY(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the relationship between the columns in the <legacyBold>GROUP BY</legacyBold> clause and the nonaggregated columns in the select list:</para>
          <para>SQL_GB_COLLATE = A <legacyBold>COLLATE</legacyBold> clause can be specified at the end of each grouping column. (ODBC 3.0)</para>
          <para>SQL_GB_NOT_SUPPORTED = <legacyBold>GROUP BY</legacyBold> clauses are not supported. (ODBC 2.0)</para>
          <para>SQL_GB_GROUP_BY_EQUALS_SELECT = The <legacyBold>GROUP BY</legacyBold> clause must contain all nonaggregated columns in the select list. It cannot contain any other columns. For example, <legacyBold>SELECT DEPT, MAX(SALARY) FROM EMPLOYEE GROUP BY DEPT</legacyBold>. (ODBC 2.0)</para>
          <para>SQL_GB_GROUP_BY_CONTAINS_SELECT = The <legacyBold>GROUP BY</legacyBold> clause must contain all nonaggregated columns in the select list. It can contain columns that are not in the select list. For example, <legacyBold>SELECT DEPT, MAX(SALARY) FROM EMPLOYEE GROUP BY DEPT, AGE</legacyBold>. (ODBC 2.0)</para>
          <para>SQL_GB_NO_RELATION = The columns in the <legacyBold>GROUP BY</legacyBold> clause and the select list are not related. The meaning of nongrouped, nonaggregated columns in the select list is data source–dependent. For example, <legacyBold>SELECT DEPT, SALARY FROM EMPLOYEE GROUP BY DEPT, AGE</legacyBold>. (ODBC 2.0)</para>
          <para>An SQL-92 Entry level–conformant driver will always return the SQL_GB_GROUP_BY_EQUALS_SELECT option as supported. An SQL-92 Full level–conformant driver will always return the SQL_GB_COLLATE option as supported. If none of the options is supported, the <legacyBold>GROUP BY</legacyBold> clause is not supported by the data source.</para>
        </definition>
        <definedTerm>SQL_IDENTIFIER_CASE(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value as follows:</para>
          <para>SQL_IC_UPPER = Identifiers in SQL are not case-sensitive and are stored in uppercase in system catalog.</para>
          <para>SQL_IC_LOWER = Identifiers in SQL are not case-sensitive and are stored in lowercase in system catalog.</para>
          <para>SQL_IC_SENSITIVE = Identifiers in SQL are case sensitive and are stored in mixed case in system catalog.</para>
          <para>SQL_IC_MIXED = Identifiers in SQL are not case-sensitive and are stored in mixed case in system catalog. </para>
          <para>Because identifiers in SQL-92 are never case-sensitive, a driver that conforms strictly to SQL-92 (any level) will never return the SQL_IC_SENSITIVE option as supported.</para>
        </definition>
        <definedTerm>SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)</definedTerm>
        <definition>
          <para>The character string that is used as the starting and ending delimiter of a quoted (delimited) identifier in SQL statements. (Identifiers passed as arguments to ODBC functions do not have to be quoted.) If the data source does not support quoted identifiers, a blank is returned. </para>
          <para>This character string can also be used for quoting catalog function arguments when the connection attribute SQL_ATTR_METADATA_ID is set to SQL_TRUE.</para>
          <para>Because the identifier quote character in SQL-92 is the double quotation mark ("), a driver that conforms strictly to SQL-92 will always return the double quotation mark character.</para>
        </definition>
        <definedTerm>SQL_INDEX_KEYWORDS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that enumerates keywords in the CREATE INDEX statement that are supported by the driver:</para>
          <para>SQL_IK_NONE = None of the keywords is supported.</para>
          <para>SQL_IK_ASC = ASC keyword is supported.</para>
          <para>SQL_IK_DESC = DESC keyword is supported.</para>
          <para>SQL_IK_ALL = All keywords are supported.</para>
          <para>To see whether the CREATE INDEX statement is supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DLL_INDEX information type.</para>
        </definition>
        <definedTerm>SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the views in the INFORMATION_SCHEMA that are supported by the driver. The views in, and the contents of, INFORMATION_SCHEMA are as defined in SQL-92. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which views are supported:</para>
          <para>SQL_ISV_ASSERTIONS = Identifies the catalog's assertions that are owned by a given user. (Full level)</para>
          <para>SQL_ISV_CHARACTER_SETS = Identifies the catalog's character sets that can be accessed by a given user. (Intermediate level)</para>
          <para>SQL_ISV_CHECK_CONSTRAINTS = Identifies the CHECK constraints that are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_COLLATIONS = Identifies the character collations for the catalog that can be accessed by a given user. (Full level)</para>
          <para>SQL_ISV_COLUMN_DOMAIN_USAGE = Identifies columns for the catalog that depend on domains defined in the catalog and are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_COLUMN_PRIVILEGES = Identifies the privileges on columns of persistent tables that are available to or granted by a given user. (FIPS Transitional level)</para>
          <para>SQL_ISV_COLUMNS = Identifies the columns of persistent tables that can be accessed by a given user. (FIPS Transitional level)</para>
          <para>SQL_ISV_CONSTRAINT_COLUMN_USAGE = Similar to CONSTRAINT_TABLE_USAGE view, columns are identified for the various constraints that are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_CONSTRAINT_TABLE_USAGE = Identifies the tables that are used by constraints (referential, unique, and assertions), and are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_DOMAIN_CONSTRAINTS = Identifies the domain constraints (of the domains in the catalog) that can be accessed by a given user. (Intermediate level)</para>
          <para>SQL_ISV_DOMAINS = Identifies the domains defined in a catalog that can be accessed by the user. (Intermediate level)</para>
          <para>SQL_ISV_KEY_COLUMN_USAGE = Identifies columns defined in the catalog that are constrained as keys by a given user. (Intermediate level)</para>
          <para>SQL_ISV_REFERENTIAL_CONSTRAINTS = Identifies the referential constraints that are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_SCHEMATA = Identifies the schemas that are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_SQL_LANGUAGES = Identifies the SQL conformance levels, options, and dialects supported by the SQL implementation. (Intermediate level)</para>
          <para>SQL_ISV_TABLE_CONSTRAINTS = Identifies the table constraints that are owned by a given user. (Intermediate level)</para>
          <para>SQL_ISV_TABLE_PRIVILEGES = Identifies the privileges on persistent tables that are available to or granted by a given user. (FIPS Transitional level)</para>
          <para>SQL_ISV_TABLES = Identifies the persistent tables defined in a catalog that can be accessed by a given user. (FIPS Transitional level)</para>
          <para>SQL_ISV_TRANSLATIONS = Identifies character translations for the catalog that can be accessed by a given user. (Full level) </para>
          <para>SQL_ISV_USAGE_PRIVILEGES = Identifies the USAGE privileges on catalog objects that are available to or owned by a given user. (FIPS Transitional level)</para>
          <para>SQL_ISV_VIEW_COLUMN_USAGE = Identifies the columns on which the catalog's views that are owned by a given user are dependent. (Intermediate level)</para>
          <para>SQL_ISV_VIEW_TABLE_USAGE = Identifies the tables on which the catalog's views that are owned by a given user are dependent. (Intermediate level) </para>
          <para>SQL_ISV_VIEWS = Identifies the viewed tables defined in this catalog that can be accessed by a given user. (FIPS Transitional level)</para>
        </definition>
        <definedTerm>SQL_INSERT_STATEMENT(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that indicates support for <legacyBold>INSERT</legacyBold> statements:</para>
          <para>SQL_IS_INSERT_LITERALS</para>
          <para>SQL_IS_INSERT_SEARCHED</para>
          <para>SQL_IS_SELECT_INTO </para>
          <para>An SQL-92 Entry level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_INTEGRITY(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports the Integrity Enhancement Facility; "N" if it does not. </para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_ODBC_SQL_OPT_IEF.</para>
        </definition>
        <definedTerm>SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a keyset cursor that are supported by the driver. This bitmask contains the first subset of attributes; for the second subset, see SQL_KEYSET_CURSOR_ATTRIBUTES2. </para>
          <para>The following bitmasks are used to determine which attributes are supported: </para>
          <para>SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK</para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (and substitute "keyset-driven cursor" for "dynamic cursor" in the descriptions).</para>
          <para>An SQL-92 Intermediate level–conformant driver will usually return the SQL_CA1_NEXT, SQL_CA1_ABSOLUTE, and SQL_CA1_RELATIVE options as supported, because the driver supports scrollable cursors through the embedded SQL FETCH statement. Because this does not directly determine the underlying SQL support, however, scrollable cursors may not be supported, even for an SQL-92 Intermediate level–conformant driver.</para>
        </definition>
        <definedTerm>SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a keyset cursor that are supported by the driver. This bitmask contains the second subset of attributes; for the first subset, see SQL_KEYSET_CURSOR_ATTRIBUTES1. </para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE</para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (and substitute "keyset-driven cursor" for "dynamic cursor" in the descriptions).</para>
        </definition>
        <definedTerm>SQL_KEYWORDS(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string that contains a comma-separated list of all data source–specific keywords. This list does not contain keywords specific to ODBC or keywords used by both the data source and ODBC. This list represents all the reserved keywords; interoperable applications should not use these words in object names.</para>
          <para>For a list of ODBC keywords, see <link xlink:href="8eeede59-a828-44bf-866c-1ca9a77a2c5e">Reserved Keywords</link> in <link xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</link>. The <legacyBold>#define</legacyBold> value SQL_ODBC_KEYWORDS contains a comma-separated list of ODBC keywords.</para>
          <para>Appendix C: SQL Grammar</para>
        </definition>
        <definedTerm>SQL_LIKE_ESCAPE_CLAUSE(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports an escape character for the percent character (%) and underscore character (_) in a <legacyBold>LIKE</legacyBold> predicate and the driver supports the ODBC syntax for defining a <legacyBold>LIKE</legacyBold> predicate escape character; "N" otherwise.</para>
        </definition>
        <definedTerm>SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum number of active concurrent statements in asynchronous mode that the driver can support on a given connection. If there is no specific limit or the limit is unknown, this value is zero.</para>
        </definition>
        <definedTerm>SQL_MAX_BINARY_LITERAL_LEN(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum length (number of hexadecimal characters, excluding the literal prefix and suffix returned by <legacyBold>SQLGetTypeInfo</legacyBold>) of a binary literal in an SQL statement. For example, the binary literal 0xFFAA has a length of 4. If there is no maximum length or the length is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_CATALOG_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a catalog name in the data source. If there is no maximum length or the length is unknown, this value is set to zero. </para>
          <para>An FIPS Full level–conformant driver will return at least 128.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_MAX_QUALIFIER_NAME_LEN.</para>
        </definition>
        <definedTerm>SQL_MAX_CHAR_LITERAL_LEN(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum length (number of characters, excluding the literal prefix and suffix returned by <legacyBold>SQLGetTypeInfo</legacyBold>) of a character literal in an SQL statement. If there is no maximum length or the length is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a column name in the data source. If there is no maximum length or the length is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 18. An FIPS Intermediate level–conformant driver will return at least 128.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMNS_IN_GROUP_BY(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of columns allowed in a <legacyBold>GROUP BY</legacyBold> clause. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
          <para>An FIPS Entry level–conformant driver will return at least 6. An FIPS Intermediate level–conformant driver will return at least 15.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of columns allowed in an index. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMNS_IN_ORDER_BY(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of columns allowed in an <legacyBold>ORDER BY</legacyBold> clause. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
          <para>An FIPS Entry level–conformant driver will return at least 6. An FIPS Intermediate level–conformant driver will return at least 15.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of columns allowed in a select list. If there is no specified limit or the limit is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 100. An FIPS Intermediate level–conformant driver will return at least 250.</para>
        </definition>
        <definedTerm>SQL_MAX_COLUMNS_IN_TABLE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of columns allowed in a table. If there is no specified limit or the limit is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 100. An FIPS Intermediate level–conformant driver will return at least 250.</para>
        </definition>
        <definedTerm>SQL_MAX_CONCURRENT_ACTIVITIES(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of active statements that the driver can support for a connection. A statement is defined as active if it has results pending, with the term "results" meaning rows from a <legacyBold>SELECT</legacyBold> operation or rows affected by an <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, or <legacyBold>DELETE</legacyBold> operation (such as a row count), or if it is in a NEED_DATA state. This value can reflect a limitation imposed by either the driver or the data source. If there is no specified limit or the limit is unknown, this value is set to zero. </para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_ACTIVE_STATEMENTS.</para>
        </definition>
        <definedTerm>SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a cursor name in the data source. If there is no maximum length or the length is unknown, this value is set to zero.</para>
          <para>An FIPS Entry level–conformant driver will return at least 18. An FIPS Intermediate level–conformant driver will return at least 128.</para>
        </definition>
        <definedTerm>SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of active connections that the driver can support for an environment. This value can reflect a limitation imposed by either the driver or the data source. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_ACTIVE_CONNECTIONS.</para>
        </definition>
        <definedTerm>SQL_MAX_IDENTIFIER_LEN(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT that indicates the maximum size in characters that the data source supports for user-defined names. </para>
          <para>An FIPS Entry level–conformant driver will return at least 18. An FIPS Intermediate level–conformant driver will return at least 128.</para>
        </definition>
        <definedTerm>SQL_MAX_INDEX_SIZE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum number of bytes allowed in the combined fields of an index. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a procedure name in the data source. If there is no maximum length or the length is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_ROW_SIZE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum length of a single row in a table. If there is no specified limit or the limit is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 2,000. An FIPS Intermediate level–conformant driver will return at least 8,000.</para>
        </definition>
        <definedTerm>SQL_MAX_ROW_SIZE_INCLUDES_LONG(ODBC 3.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the maximum row size returned for the SQL_MAX_ROW_SIZE information type includes the length of all SQL_LONGVARCHAR and SQL_LONGVARBINARY columns in the row; "N" otherwise.</para>
        </definition>
        <definedTerm>SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a schema name in the data source. If there is no maximum length or the length is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 18. An FIPS Intermediate level–conformant driver will return at least 128.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_MAX_OWNER_NAME_LEN.</para>
        </definition>
        <definedTerm>SQL_MAX_STATEMENT_LEN(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that specifies the maximum length (number of characters, including white space) of an SQL statement. If there is no maximum length or the length is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a table name in the data source. If there is no maximum length or the length is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 18. An FIPS Intermediate level–conformant driver will return at least 128.</para>
        </definition>
        <definedTerm>SQL_MAX_TABLES_IN_SELECT(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of tables allowed in the <legacyBold>FROM</legacyBold> clause of a <legacyBold>SELECT </legacyBold>statement. If there is no specified limit or the limit is unknown, this value is set to zero. </para>
          <para>An FIPS Entry level–conformant driver will return at least 15. An FIPS Intermediate level–conformant driver will return at least 50.</para>
        </definition>
        <definedTerm>SQL_MAX_USER_NAME_LEN(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum length of a user name in the data source. If there is no maximum length or the length is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_MULT_RESULT_SETS(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports multiple result sets, "N" if it does not.</para>
          <para>For more information about multiple result sets, see <link xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</link>.</para>
        </definition>
        <definedTerm>SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the driver supports more than one active transaction at the same time, "N" if only one transaction can be active at any time.</para>
          <para>The information returned for this information type does not apply in the case of distributed transactions.</para>
        </definition>
        <definedTerm>SQL_NEED_LONG_DATA_LEN(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source needs the length of a long data value (the data type is SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type) before that value is sent to the data source, "N" if it does not. For more information, see <link xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</link> and <link xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</link>.</para>
        </definition>
        <definedTerm>SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies whether the data source supports NOT NULL in columns:</para>
          <para>SQL_NNC_NULL = All columns must be nullable.</para>
          <para>SQL_NNC_NON_NULL = Columns cannot be nullable. (The data source supports the <legacyBold>NOT NULL</legacyBold> column constraint in <legacyBold>CREATE TABLE</legacyBold> statements.) </para>
          <para>An SQL-92 Entry level–conformant driver will return SQL_NNC_NON_NULL.</para>
        </definition>
        <definedTerm>SQL_NULL_COLLATION(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies where NULLs are sorted in a result set:</para>
          <para>SQL_NC_END = NULLs are sorted at the end of the result set, regardless of the ASC or DESC keywords.</para>
          <para>SQL_NC_HIGH = NULLs are sorted at the high end of the result set, depending on the ASC or DESC keywords.</para>
          <para>SQL_NC_LOW = NULLs are sorted at the low end of the result set, depending on the ASC or DESC keywords.</para>
          <para>SQL_NC_START = NULLs are sorted at the start of the result set, regardless of the ASC or DESC keywords.</para>
        </definition>
        <definedTerm>SQL_NUMERIC_FUNCTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>Note: The information type was introduced in ODBC 1.0; each bitmask is labeled with the version in which it was introduced.</para>
          <para>An SQLUINTEGER bitmask enumerating the scalar numeric functions supported by the driver and associated data source. </para>
          <para>The following bitmasks are used to determine which numeric functions are supported:</para>
          <para>SQL_FN_NUM_ABS (ODBC 1.0)SQL_FN_NUM_ACOS (ODBC 1.0)SQL_FN_NUM_ASIN (ODBC 1.0)SQL_FN_NUM_ATAN (ODBC 1.0)SQL_FN_NUM_ATAN2 (ODBC 1.0)SQL_FN_NUM_CEILING (ODBC 1.0)SQL_FN_NUM_COS (ODBC 1.0)SQL_FN_NUM_COT (ODBC 1.0)SQL_FN_NUM_DEGREES (ODBC 2.0)SQL_FN_NUM_EXP (ODBC 1.0)SQL_FN_NUM_FLOOR (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 2.0)SQL_FN_NUM_MOD (ODBC 1.0)SQL_FN_NUM_PI (ODBC 1.0)SQL_FN_NUM_POWER (ODBC 2.0)SQL_FN_NUM_RADIANS (ODBC 2.0)SQL_FN_NUM_RAND (ODBC 1.0)SQL_FN_NUM_ROUND (ODBC 2.0)SQL_FN_NUM_SIGN (ODBC 1.0)SQL_FN_NUM_SIN (ODBC 1.0)SQL_FN_NUM_SQRT (ODBC 1.0)SQL_FN_NUM_TAN (ODBC 1.0)SQL_FN_NUM_TRUNCATE (ODBC 2.0)</para>
        </definition>
        <definedTerm>SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates the level of the ODBC 3<legacyItalic>.x</legacyItalic> interface that the driver complies with.</para>
          <para>SQL_OIC_CORE: The minimum level that all ODBC drivers are expected to comply with. This level includes basic interface elements such as connection functions, functions for preparing and executing an SQL statement, basic result set metadata functions, basic catalog functions, and so on.</para>
          <para>SQL_OIC_LEVEL1: A level including the core standards compliance level functionality, plus scrollable cursors, bookmarks, positioned updates and deletes, and so on.</para>
          <para>SQL_OIC_LEVEL2: A level including level 1 standards compliance level functionality, plus advanced features such as sensitive cursors; update, delete, and refresh by bookmarks; stored procedure support; catalog functions for primary and foreign keys; multi-catalog support; and so on.</para>
          <para>For more information, see <link xlink:href="2c470e54-0600-4b2b-b1f3-9885cb28a01a">Interface Conformance Levels</link>.</para>
        </definition>
        <definedTerm>SQL_ODBC_VER(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the version of ODBC to which the Driver Manager conforms. The version is of the form ##.##.0000, where the first two digits are the major version and the next two digits are the minor version. This is implemented only in the Driver Manager.</para>
        </definition>
        <definedTerm>SQL_OJ_CAPABILITIES(ODBC 2.01)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the types of outer joins supported by the driver and data source. The following bitmasks are used to determine which types are supported:</para>
          <para>SQL_OJ_LEFT = Left outer joins are supported.</para>
          <para>SQL_OJ_RIGHT = Right outer joins are supported.</para>
          <para>SQL_OJ_FULL = Full outer joins are supported.</para>
          <para>SQL_OJ_NESTED = Nested outer joins are supported.</para>
          <para>SQL_OJ_NOT_ORDERED = The column names in the ON clause of the outer join do not have to be in the same order as their respective table names in the <legacyBold>OUTER JOIN </legacyBold>clause.</para>
          <para>SQL_OJ_INNER = The inner table (the right table in a left outer join or the left table in a right outer join) can also be used in an inner join. This does not apply to full outer joins, which do not have an inner table.</para>
          <para>SQL_OJ_ALL_COMPARISON_OPS = The comparison operator in the ON clause can be any of the ODBC comparison operators. If this bit is not set, only the equals (=) comparison operator can be used in outer joins.</para>
          <para>If none of these options is returned as supported, no outer join clause is supported.</para>
          <para>For information about the support of relational join operators in a SELECT statement, as defined by SQL-92, see SQL_SQL92_RELATIONAL_JOIN_OPERATORS.</para>
        </definition>
        <definedTerm>SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the columns in the <legacyBold>ORDER BY</legacyBold> clause must be in the select list; otherwise, "N".</para>
        </definition>
        <definedTerm>SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER enumerating the driver's properties regarding the availability of row counts in a parameterized execution. Has the following values:</para>
          <para>SQL_PARC_BATCH = Individual row counts are available for each set of parameters. This is conceptually equivalent to the driver generating a batch of SQL statements, one for each parameter set in the array. Extended error information can be retrieved by using the SQL_PARAM_STATUS_PTR descriptor field.</para>
          <para>SQL_PARC_NO_BATCH = There is only one row count available, which is the cumulative row count resulting from the execution of the statement for the entire array of parameters. This is conceptually equivalent to treating the statement together with the complete parameter array as one atomic unit. Errors are handled the same as if one statement were executed.</para>
        </definition>
        <definedTerm>SQL_PARAM_ARRAY_SELECTS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER enumerating the driver's properties regarding the availability of result sets in a parameterized execution. Has the following values:</para>
          <para>SQL_PAS_BATCH = There is one result set available per set of parameters. This is conceptually equivalent to the driver generating a batch of SQL statements, one for each parameter set in the array.</para>
          <para>SQL_PAS_NO_BATCH = There is only one result set available, which represents the cumulative result set resulting from the execution of the statement for the complete array of parameters. This is conceptually equivalent to treating the statement together with the complete parameter array as one atomic unit.</para>
          <para>SQL_PAS_NO_SELECT = A driver does not allow a result-set generating statement to be executed with an array of parameters.</para>
        </definition>
        <definedTerm>SQL_PROCEDURE_TERM(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the data source vendor's name for a procedure; for example, "database procedure", "stored procedure", "procedure", "package", or "stored query".</para>
        </definition>
        <definedTerm>SQL_PROCEDURES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the data source supports procedures and the driver supports the ODBC procedure invocation syntax; "N" otherwise.</para>
        </definition>
        <definedTerm>SQL_POS_OPERATIONS(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLINTEGER bitmask enumerating the support operations in <legacyBold>SQLSetPos</legacyBold>.</para>
          <para>The following bitmasks are used together with the flag to determine which options are supported.</para>
          <para>SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0) </para>
        </definition>
        <definedTerm>SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value as follows:</para>
          <para>SQL_IC_UPPER = Quoted identifiers in SQL are not case-sensitive and are stored in uppercase in the system catalog.</para>
          <para>SQL_IC_LOWER = Quoted identifiers in SQL are not case-sensitive and are stored in lowercase in the system catalog.</para>
          <para>SQL_IC_SENSITIVE = Quoted identifiers in SQL are case sensitive and are stored in mixed case in the system catalog. (In an SQL-92–compliant database, quoted identifiers are always case-sensitive.)</para>
          <para>SQL_IC_MIXED = Quoted identifiers in SQL are not case-sensitive and are stored in mixed case in the system catalog.</para>
          <para>An SQL-92 Entry level–conformant driver will always return SQL_IC_SENSITIVE.</para>
        </definition>
        <definedTerm>SQL_ROW_UPDATES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if a keyset-driven or mixed cursor maintains row versions or values for all fetched rows and therefore can detect any updates that were made to a row by any user since the row was last fetched. (This applies only to updates, not to deletions or insertions.) The driver can return the SQL_ROW_UPDATED flag to the row status array when <legacyBold>SQLFetchScroll</legacyBold> is called. Otherwise, "N".</para>
        </definition>
        <definedTerm>SQL_SCHEMA_TERM(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the data source vendor's name for a schema; for example, "owner", "Authorization ID", or "Schema".</para>
          <para>The character string can be returned in upper, lower, or mixed case.</para>
          <para>An SQL-92 Entry level–conformant driver will always return "schema".</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_OWNER_TERM.</para>
        </definition>
        <definedTerm>SQL_SCHEMA_USAGE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the statements in which schemas can be used:</para>
          <para>SQL_SU_DML_STATEMENTS = Schemas are supported in all Data Manipulation Language statements: <legacyBold>SELECT</legacyBold>, <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and if supported, <legacyBold>SELECT FOR UPDATE</legacyBold> and positioned update and delete statements.</para>
          <para>SQL_SU_PROCEDURE_INVOCATION = Schemas are supported in the ODBC procedure invocation statement.</para>
          <para>SQL_SU_TABLE_DEFINITION = Schemas are supported in all table definition statements: <legacyBold>CREATE TABLE</legacyBold>, <legacyBold>CREATE VIEW</legacyBold>, <legacyBold>ALTER TABLE</legacyBold>, <legacyBold>DROP TABLE</legacyBold>, and <legacyBold>DROP VIEW</legacyBold>.</para>
          <para>SQL_SU_INDEX_DEFINITION = Schemas are supported in all index definition statements: <legacyBold>CREATE INDEX</legacyBold> and <legacyBold>DROP INDEX</legacyBold>.</para>
          <para>SQL_SU_PRIVILEGE_DEFINITION = Schemas are supported in all privilege definition statements: <legacyBold>GRANT</legacyBold> and <legacyBold>REVOKE</legacyBold>.</para>
          <para>An SQL-92 Entry level–conformant driver will always return the SQL_SU_DML_STATEMENTS, SQL_SU_TABLE_DEFINITION, and SQL_SU_PRIVILEGE_DEFINITION options, as supported.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> has been renamed for ODBC 3.0 from the ODBC 2.0 <legacyItalic>InfoType</legacyItalic> SQL_OWNER_USAGE.</para>
        </definition>
        <definedTerm>SQL_SCROLL_OPTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>Note: The information type was introduced in ODBC 1.0; each bitmask is labeled with the version in which it was introduced.</para>
          <para>An SQLUINTEGER bitmask enumerating the scroll options supported for scrollable cursors.</para>
          <para>The following bitmasks are used to determine which options are supported:</para>
          <para>SQL_SO_FORWARD_ONLY = The cursor only scrolls forward. (ODBC 1.0)</para>
          <para>SQL_SO_STATIC = The data in the result set is static. (ODBC 2.0)</para>
          <para>SQL_SO_KEYSET_DRIVEN = The driver saves and uses the keys for every row in the result set. (ODBC 1.0)</para>
          <para>SQL_SO_DYNAMIC = The driver keeps the keys for every row in the rowset (the keyset size is the same as the rowset size). (ODBC 1.0)</para>
          <para>SQL_SO_MIXED = The driver keeps the keys for every row in the keyset, and the keyset size is greater than the rowset size. The cursor is keyset-driven inside the keyset and dynamic outside the keyset. (ODBC 1.0)</para>
          <para>For information about scrollable cursors, see <link xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</link>.</para>
        </definition>
        <definedTerm>SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string specifying what the driver supports as an escape character that allows the use of the pattern match metacharacters underscore (_) and percent sign (%) as valid characters in search patterns. This escape character applies only for those catalog function arguments that support search strings. If this string is empty, the driver does not support a search-pattern escape character.</para>
          <para>Because this information type does not indicate general support of the escape character in the <legacyBold>LIKE</legacyBold> predicate, SQL-92 does not include requirements for this character string.</para>
          <para>This <legacyItalic>InfoType</legacyItalic> is limited to catalog functions. For a description of the use of the escape character in search pattern strings, see <link xlink:href="1d3f0ea6-87af-4836-807f-955e7df2b5df">Pattern Value Arguments</link>.</para>
        </definition>
        <definedTerm>SQL_SERVER_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the actual data source–specific server name; useful when a data source name is used during <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, and<legacyBold> SQLBrowseConnect</legacyBold>.</para>
        </definition>
        <definedTerm>SQL_SPECIAL_CHARACTERS(ODBC 2.0)</definedTerm>
        <definition>
          <para>A character string that contains all special characters (that is, all characters except a through z, A through Z, 0 through 9, and underscore) that can be used in an identifier name, such as a table name, column name, or index name, on the data source. For example, "#$^". If an identifier contains one or more of these characters, the identifier must be a delimited identifier.</para>
        </definition>
        <definedTerm>SQL_SQL_CONFORMANCE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates the level of SQL-92 supported by the driver: </para>
          <para>SQL_SC_SQL92_ENTRY = Entry level SQL-92 compliant.</para>
          <para>SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 transitional level compliant.</para>
          <para>SQL_SC_SQL92_FULL = Full level SQL-92 compliant.</para>
          <para>SQL_SC_ SQL92_INTERMEDIATE = Intermediate level SQL-92 compliant.</para>
        </definition>
        <definedTerm>SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the datetime scalar functions that are supported by the driver and the associated data source, as defined in SQL-92.</para>
          <para>The following bitmasks are used to determine which datetime functions are supported:</para>
          <para>SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP</para>
        </definition>
        <definedTerm>SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the rules supported for a foreign key in a <legacyBold>DELETE</legacyBold> statement, as defined in SQL-92.</para>
          <para>The following bitmasks are used to determine which clauses are supported by the data source:</para>
          <para>SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL</para>
          <para>An FIPS Transitional level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the rules supported for a foreign key in an <legacyBold>UPDATE</legacyBold> statement, as defined in SQL-92.</para>
          <para>The following bitmasks are used to determine which clauses are supported by the data source:</para>
          <para>SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL </para>
          <para>An SQL-92 Full level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_SQL92_GRANT(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses supported in the <legacyBold>GRANT</legacyBold> statement, as defined in SQL-92. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported by the data source:</para>
          <para>SQL_SG_DELETE_TABLE (Entry level)SQL_SG_INSERT_COLUMN (Intermediate level)SQL_SG_INSERT_TABLE (Entry level) SQL_SG_REFERENCES_TABLE (Entry level)SQL_SG_REFERENCES_COLUMN (Entry level)SQL_SG_SELECT_TABLE (Entry level)SQL_SG_UPDATE_COLUMN (Entry level)SQL_SG_UPDATE_TABLE (Entry level) SQL_SG_USAGE_ON_DOMAIN (FIPS Transitional level)SQL_SG_USAGE_ON_CHARACTER_SET (FIPS Transitional level)SQL_SG_USAGE_ON_COLLATION (FIPS Transitional level)SQL_SG_USAGE_ON_TRANSLATION (FIPS Transitional level)SQL_SG_WITH_GRANT_OPTION (Entry level)</para>
        </definition>
        <definedTerm>SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the numeric value scalar functions that are supported by the driver and the associated data source, as defined in SQL-92.</para>
          <para>The following bitmasks are used to determine which numeric functions are supported:</para>
          <para>SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION</para>
        </definition>
        <definedTerm>SQL_SQL92_PREDICATES(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the predicates supported in a <legacyBold>SELECT</legacyBold> statement, as defined in SQL-92. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which options are supported by the data source:</para>
          <para>SQL_SP_BETWEEN (Entry level)SQL_SP_COMPARISON (Entry level)SQL_SP_EXISTS (Entry level)SQL_SP_IN (Entry level)SQL_SP_ISNOTNULL (Entry level)SQL_SP_ISNULL (Entry level)SQL_SP_LIKE (Entry level)SQL_SP_MATCH_FULL (Full level)SQL_SP_MATCH_PARTIAL(Full level)SQL_SP_MATCH_UNIQUE_FULL (Full level)SQL_SP_MATCH_UNIQUE_PARTIAL (Full level)SQL_SP_OVERLAPS (FIPS Transitional level)SQL_SP_QUANTIFIED_COMPARISON (Entry level)SQL_SP_UNIQUE (Entry level)</para>
        </definition>
        <definedTerm>SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the relational join operators supported in a <legacyBold>SELECT</legacyBold> statement, as defined in SQL-92. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which options are supported by the data source:</para>
          <para>SQL_SRJO_CORRESPONDING_CLAUSE (Intermediate level)SQL_SRJO_CROSS_JOIN (Full level)SQL_SRJO_EXCEPT_JOIN (Intermediate level)SQL_SRJO_FULL_OUTER_JOIN (Intermediate level) SQL_SRJO_INNER_JOIN (FIPS Transitional level)SQL_SRJO_INTERSECT_JOIN (Intermediate level)SQL_SRJO_LEFT_OUTER_JOIN (FIPS Transitional level)SQL_SRJO_NATURAL_JOIN (FIPS Transitional level)SQL_SRJO_RIGHT_OUTER_JOIN (FIPS Transitional level)SQL_SRJO_UNION_JOIN (Full level)</para>
          <para>SQL_SRJO_INNER_JOIN indicates support for the <legacyBold>INNER JOIN </legacyBold>syntax, not for the inner join capability. Support for the <legacyBold>INNER JOIN</legacyBold> syntax is FIPS TRANSITIONAL, whereas support for the inner join capability is <legacyBold>ENTRY</legacyBold>.</para>
        </definition>
        <definedTerm>SQL_SQL92_REVOKE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses supported in the <legacyBold>REVOKE</legacyBold> statement, as defined in SQL-92, supported by the data source. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported by the data source:</para>
          <para>SQL_SR_CASCADE (FIPS Transitional level) SQL_SR_DELETE_TABLE (Entry level)SQL_SR_GRANT_OPTION_FOR (Intermediate level) SQL_SR_INSERT_COLUMN (Intermediate level)SQL_SR_INSERT_TABLE (Entry level)SQL_SR_REFERENCES_COLUMN (Entry level)SQL_SR_REFERENCES_TABLE (Entry level)SQL_SR_RESTRICT (FIPS Transitional level)SQL_SR_SELECT_TABLE (Entry level)SQL_SR_UPDATE_COLUMN (Entry level)SQL_SR_UPDATE_TABLE (Entry level)SQL_SR_USAGE_ON_DOMAIN (FIPS Transitional level)SQL_SR_USAGE_ON_CHARACTER_SET (FIPS Transitional level)SQL_SR_USAGE_ON_COLLATION (FIPS Transitional level)SQL_SR_USAGE_ON_TRANSLATION (FIPS Transitional level)</para>
        </definition>
        <definedTerm>SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the row value constructor expressions supported in a <legacyBold>SELECT</legacyBold> statement, as defined in SQL-92. The following bitmasks are used to determine which options are supported by the data source:</para>
          <para>SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY</para>
        </definition>
        <definedTerm>SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the string scalar functions that are supported by the driver and the associated data source, as defined in SQL-92.</para>
          <para>The following bitmasks are used to determine which string functions are supported:</para>
          <para>SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING</para>
        </definition>
        <definedTerm>SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the value expressions supported, as defined in SQL-92.</para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which options are supported by the data source:</para>
          <para>SQL_SVE_CASE (Intermediate level)SQL_SVE_CAST (FIPS Transitional level)SQL_SVE_COALESCE (Intermediate level)SQL_SVE_NULLIF (Intermediate level)</para>
        </definition>
        <definedTerm>SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the CLI standard or standards to which the driver conforms. The following bitmasks are used to determine which levels the driver complies with:</para>
          <para>SQL_SCC_XOPEN_CLI_VERSION1: The driver complies with the Open Group CLI version 1.</para>
          <para>SQL_SCC_ISO92_CLI: The driver complies with the ISO 92 CLI.</para>
        </definition>
        <definedTerm>SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a static cursor that are supported by the driver. This bitmask contains the first subset of attributes; for the second subset, see SQL_STATIC_CURSOR_ATTRIBUTES2. </para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK</para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (and substitute "static cursor" for "dynamic cursor" in the descriptions).</para>
          <para>An SQL-92 Intermediate level–conformant driver will usually return the SQL_CA1_NEXT, SQL_CA1_ABSOLUTE, and SQL_CA1_RELATIVE options as supported, because the driver supports scrollable cursors through the embedded SQL FETCH statement. Because this does not directly determine the underlying SQL support, however, scrollable cursors may not be supported, even for an SQL-92 Intermediate level–conformant driver.</para>
        </definition>
        <definedTerm>SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask that describes the attributes of a static cursor that are supported by the driver. This bitmask contains the second subset of attributes; for the first subset, see SQL_STATIC_CURSOR_ATTRIBUTES1.</para>
          <para>The following bitmasks are used to determine which attributes are supported:</para>
          <para>SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE</para>
          <para>For descriptions of these bitmasks, see SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (and substitute "static cursor" for "dynamic cursor" in the descriptions).</para>
        </definition>
        <definedTerm>SQL_STRING_FUNCTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>Note: The information type was introduced in ODBC 1.0; each bitmask is labeled with the version in which it was introduced.</para>
          <para>An SQLUINTEGER bitmask enumerating the scalar string functions supported by the driver and associated data source.</para>
          <para>The following bitmasks are used to determine which string functions are supported:</para>
          <para>SQL_FN_STR_ASCII (ODBC 1.0)SQL_FN_STR_BIT_LENGTH (ODBC 3.0)SQL_FN_STR_CHAR (ODBC 1.0)SQL_FN_STR_CHAR_LENGTH (ODBC 3.0)SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0)SQL_FN_STR_CONCAT (ODBC 1.0)SQL_FN_STR_DIFFERENCE (ODBC 2.0)SQL_FN_STR_INSERT (ODBC 1.0)SQL_FN_STR_LCASE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0)SQL_FN_STR_REPEAT (ODBC 1.0)SQL_FN_STR_REPLACE (ODBC 1.0)SQL_FN_STR_RIGHT (ODBC 1.0)SQL_FN_STR_RTRIM (ODBC 1.0)SQL_FN_STR_SOUNDEX (ODBC 2.0)SQL_FN_STR_SPACE (ODBC 2.0)SQL_FN_STR_SUBSTRING (ODBC 1.0)SQL_FN_STR_UCASE (ODBC 1.0)</para>
          <para>If an application can call the <legacyBold>LOCATE</legacyBold> scalar function with the <legacyItalic>string_exp1</legacyItalic>, <legacyItalic>string_exp2</legacyItalic>, and <legacyItalic>start</legacyItalic> arguments, the driver returns the SQL_FN_STR_LOCATE bitmask. If an application can call the LOCATE scalar function with only the <legacyItalic>string_exp1</legacyItalic> and <legacyItalic>string_exp2</legacyItalic> arguments, the driver returns the SQL_FN_STR_LOCATE_2 bitmask. Drivers that fully support the <legacyBold>LOCATE</legacyBold> scalar function return both bitmasks.</para>
          <para>(For more information, see <link xlink:href="270f669e-8aab-4db0-95a4-f2b3c69538b3">String Functions</link> in Appendix E, "Scalar Functions.")</para>
        </definition>
        <definedTerm>SQL_SUBQUERIES(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the predicates that support subqueries:</para>
          <para>SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED</para>
          <para>The SQL_SQ_CORRELATED_SUBQUERIES bitmask indicates that all predicates that support subqueries support correlated subqueries.</para>
          <para>An SQL-92 Entry level–conformant driver will always return a bitmask in which all of these bits are set.</para>
        </definition>
        <definedTerm>SQL_SYSTEM_FUNCTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the scalar system functions supported by the driver and associated data source. </para>
          <para>The following bitmasks are used to determine which system functions are supported:</para>
          <para>SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME</para>
        </definition>
        <definedTerm>SQL_TABLE_TERM(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the data source vendor's name for a table; for example, "table" or "file".</para>
          <para>This character string can be in upper, lower, or mixed case. </para>
          <para>An SQL-92 Entry level–conformant driver will always return "table".</para>
        </definition>
        <definedTerm>SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the timestamp intervals supported by the driver and associated data source for the TIMESTAMPADD scalar function.</para>
          <para>The following bitmasks are used to determine which intervals are supported:</para>
          <para>SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR</para>
          <para>An FIPS Transitional level–conformant driver will always return a bitmask in which all of these bits are set.</para>
        </definition>
        <definedTerm>SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the timestamp intervals supported by the driver and associated data source for the TIMESTAMPDIFF scalar function.</para>
          <para>The following bitmasks are used to determine which intervals are supported:</para>
          <para>SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR </para>
          <para>An FIPS Transitional level–conformant driver will always return a bitmask in which all of these bits are set.</para>
        </definition>
        <definedTerm>SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)</definedTerm>
        <definition>
          <para>Note: The information type was introduced in ODBC 1.0; each bitmask is labeled with the version in which it was introduced.</para>
          <para>An SQLUINTEGER bitmask enumerating the scalar date and time functions supported by the driver and associated data source.</para>
          <para>The following bitmasks are used to determine which date and time functions are supported:</para>
          <para>SQL_FN_TD_CURRENT_DATE ODBC 3.0)SQL_FN_TD_CURRENT_TIME (ODBC 3.0)SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0)SQL_FN_TD_CURDATE (ODBC 1.0)SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0)SQL_FN_TD_DAYOFMONTH (ODBC 1.0)SQL_FN_TD_DAYOFWEEK (ODBC 1.0)SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0)SQL_FN_TD_HOUR (ODBC 1.0)SQL_FN_TD_MINUTE (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0)SQL_FN_TD_MONTHNAME (ODBC 2.0)SQL_FN_TD_NOW (ODBC 1.0)SQL_FN_TD_QUARTER (ODBC 1.0)SQL_FN_TD_SECOND (ODBC 1.0)SQL_FN_TD_TIMESTAMPADD (ODBC 2.0)SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0)SQL_FN_TD_WEEK (ODBC 1.0)SQL_FN_TD_YEAR (ODBC 1.0)</para>
        </definition>
        <definedTerm>SQL_TXN_CAPABLE(ODBC 1.0)</definedTerm>
        <definition>
          <para>Note: The information type was introduced in ODBC 1.0; each return value is labeled with the version in which it was introduced.</para>
          <para>An SQLUSMALLINT value describing the transaction support in the driver or data source:</para>
          <para>SQL_TC_NONE = Transactions not supported. (ODBC 1.0)</para>
          <para>SQL_TC_DML = Transactions can contain only Data Manipulation Language (DML) statements (<legacyBold>SELECT</legacyBold>, <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>). Data Definition Language (DDL) statements encountered in a transaction cause an error. (ODBC 1.0)</para>
          <para>SQL_TC_DDL_COMMIT = Transactions can contain only DML statements. DDL statements (<legacyBold>CREATE TABLE</legacyBold>, <legacyBold>DROP INDEX</legacyBold>, and so on) encountered in a transaction cause the transaction to be committed. (ODBC 2.0)</para>
          <para>SQL_TC_DDL_IGNORE = Transactions can contain only DML statements. DDL statements encountered in a transaction are ignored. (ODBC 2.0)</para>
          <para>SQL_TC_ALL = Transactions can contain DDL statements and DML statements in any order. (ODBC 1.0) </para>
          <para>(Because support of transactions is mandatory in SQL-92, an SQL-92 conformant driver [any level] will never return SQL_TC_NONE.)</para>
        </definition>
        <definedTerm>SQL_TXN_ISOLATION_OPTION(ODBC 1.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the transaction isolation levels available from the driver or data source. </para>
          <para>The following bitmasks are used together with the flag to determine which options are supported:</para>
          <para>SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE</para>
          <para>For descriptions of these isolation levels, see the description of SQL_DEFAULT_TXN_ISOLATION.</para>
          <para>To set the transaction isolation level, an application calls <legacyBold>SQLSetConnectAttr</legacyBold> to set the SQL_ATTR_TXN_ISOLATION attribute. For more information, see <link xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</link>.</para>
          <para>An SQL-92 Entry level–conformant driver will always return SQL_TXN_SERIALIZABLE as supported. A FIPS Transitional level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_UNION(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the support for the <legacyBold>UNION</legacyBold> clause:</para>
          <para>SQL_U_UNION = The data source supports the <legacyBold>UNION</legacyBold> clause.</para>
          <para>SQL_U_UNION_ALL = The data source supports the <legacyBold>ALL</legacyBold> keyword in the <legacyBold>UNION</legacyBold> clause. (<legacyBold>SQLGetInfo</legacyBold> returns both SQL_U_UNION and SQL_U_UNION_ALL in this case.)</para>
          <para>An SQL-92 Entry level–conformant driver will always return both of these options as supported.</para>
        </definition>
        <definedTerm>SQL_USER_NAME(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string with the name used in a particular database, which can be different from the login name.</para>
        </definition>
        <definedTerm>SQL_XOPEN_CLI_YEAR(ODBC 3.0)</definedTerm>
        <definition>
          <para>A character string that indicates the year of publication of the Open Group specification with which the version of the ODBC Driver Manager fully complies.</para>
        </definition>
        <definedTerm>SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the user can execute all procedures returned by <legacyBold>SQLProcedures</legacyBold>; "N" if there may be procedures returned that the user cannot execute.</para>
        </definition>
        <definedTerm>SQL_ACCESSIBLE_TABLES(ODBC 1.0)</definedTerm>
        <definition>
          <para>A character string: "Y" if the user is guaranteed <legacyBold>SELECT</legacyBold> privileges to all tables returned by <legacyBold>SQLTables</legacyBold>; "N" if there may be tables returned that the user cannot access.</para>
        </definition>
        <definedTerm>SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUSMALLINT value that specifies the maximum number of active environments that the driver can support. If there is no specified limit or the limit is unknown, this value is set to zero.</para>
        </definition>
        <definedTerm>SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating support for aggregation functions:</para>
          <para>SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM </para>
          <para>An SQL-92 Entry level–conformant driver will always return all of these options as supported.</para>
        </definition>
        <definedTerm>SQL_ALTER_DOMAIN(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>ALTER DOMAIN</legacyBold> statement, as defined in SQL-92, supported by the data source. An SQL-92 Full level–compliant driver will always return all of the bitmasks. A return value of "0" means that the <legacyBold>ALTER DOMAIN</legacyBold> statement is not supported.</para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para>SQL_AD_ADD_DOMAIN_CONSTRAINT = Adding a domain constraint is supported (Full level)</para>
          <para>SQL_AD_ADD_DOMAIN_DEFAULT = &lt;alter domain&gt; &lt;set domain default clause&gt; is supported (Full level)</para>
          <para>SQL_AD_CONSTRAINT_NAME_DEFINITION = &lt;constraint name definition clause&gt; is supported for naming domain constraint (Intermediate level)</para>
          <para>SQL_AD_DROP_DOMAIN_CONSTRAINT = &lt;drop domain constraint clause&gt; is supported (Full level)</para>
          <para>SQL_AD_DROP_DOMAIN_DEFAULT = &lt;alter domain&gt; &lt;drop domain default clause&gt; is supported (Full level)</para>
          <para>The following bits specify the supported &lt;constraint attributes&gt; if &lt;add domain constraint&gt; is supported (the SQL_AD_ADD_DOMAIN_CONSTRAINT bit is set):</para>
          <para>SQL_AD_ADD_CONSTRAINT_DEFERRABLE (Full level)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (Full level)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (Full level)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (Full level)</para>
        </definition>
        <definedTerm>SQL_ALTER_TABLE(ODBC 2.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the clauses in the <legacyBold>ALTER TABLE</legacyBold> statement supported by the data source. </para>
          <para>The SQL-92 or FIPS conformance level at which this feature must be supported is shown in parentheses next to each bitmask.</para>
          <para>The following bitmasks are used to determine which clauses are supported:</para>
          <para> SQL_AT_ADD_COLUMN_COLLATION = &lt;add column&gt; clause is supported, with facility to specify column collation (Full level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_COLUMN_DEFAULT = &lt;add column&gt; clause is supported, with facility to specify column defaults (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_COLUMN_SINGLE = &lt;add column&gt; is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_CONSTRAINT = &lt;add column&gt; clause is supported, with facility to specify column constraints (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_ADD_TABLE_CONSTRAINT = &lt;add table constraint&gt; clause is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_CONSTRAINT_NAME_DEFINITION = &lt;constraint name definition&gt; is supported for naming column and table constraints (Intermediate level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_CASCADE = &lt;drop column&gt; CASCADE is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_DEFAULT = &lt;alter column&gt; &lt;drop column default clause&gt; is supported (Intermediate level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_COLUMN_RESTRICT = &lt;drop column&gt; RESTRICT is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)</para>
          <para>SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = &lt;drop column&gt; RESTRICT is supported (FIPS Transitional level) (ODBC 3.0)</para>
          <para>SQL_AT_SET_COLUMN_DEFAULT = &lt;alter column&gt; &lt;set column default clause&gt; is supported (Intermediate level) (ODBC 3.0)</para>
          <para>The following bits specify the support &lt;constraint attributes&gt; if specifying column or table constraints is supported (the SQL_AT_ADD_CONSTRAINT bit is set):</para>
          <para>SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (Full level) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (Full level) (ODBC 3.0)</para>
        </definition>
        <definedTerm>SQL_ASYNC_MODE(ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER value that indicates the level of asynchronous support in the driver:</para>
          <para>SQL_AM_CONNECTION = Connection level asynchronous execution is supported. Either all statement handles associated with a given connection handle are in asynchronous mode or all are in synchronous mode. A statement handle on a connection cannot be in asynchronous mode while another statement handle on the same connection is in synchronous mode, and vice versa.</para>
          <para>SQL_AM_STATEMENT = Statement level asynchronous execution is supported. Some statement handles associated with a connection handle can be in asynchronous mode, whereas other statement handles on the same connection are in synchronous mode.</para>
          <para>SQL_AM_NONE = Asynchronous mode is not supported.</para>
        </definition>
        <definedTerm>SQL_BATCH_ROW_COUNT (ODBC 3.0)</definedTerm>
        <definition>
          <para>An SQLUINTEGER bitmask enumerating the behavior of the driver with respect to the availability of row counts. The following bitmasks are used together with the information type:</para>
          <para>SQL_BRC_ROLLED_UP = Row counts for consecutive INSERT, DELETE, or UPDATE statements are rolled up into one. If this bit is not set, row counts are available for each statement.</para>
          <para>SQL_BRC_PROCEDURES = Row counts, if any, are available when a batch is executed in a stored procedure. If row counts are available, they can be rolled up or individually available, depending on the SQL_BRC_ROLLED_UP bit.</para>
          <para>SQL_BRC_EXPLICIT = Row counts, if any, are available when a batch is executed directly by calling <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. If row counts are available, they can be rolled up or individually available, depending on the SQL_BRC_ROLLED_UP bit.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <codeExample>
    <description>
      <content>
        <para>
          <legacyBold>SQLGetInfo</legacyBold> returns lists of supported options as an SQLUINTEGER bitmask in *<legacyItalic>InfoValuePtr</legacyItalic>. The bitmask for each option is used together with the flag to determine whether the option is supported.</para>
        <para>For example, an application could use the following code to determine whether the SUBSTRING scalar function is supported by the driver associated with the connection.</para>
        <para>For another example of using <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference>, see <link xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables</link>.</para>
      </content>
    </description>
    <code>SQLUINTEGER fFuncs;

SQLGetInfo(hdbc, 
           SQL_STRING_FUNCTIONS,
           (SQLPOINTER)&amp;fFuncs,
           sizeof(fFuncs),
           NULL);

// SUBSTRING supported
if (fFuncs &amp; SQL_FN_STR_SUBSTRING) 
   ;   // do something

// SUBSTRING not supported
else
   ;   // do something else</code>
  </codeExample>
  <section>
    <title>Related Functions</title>
    <content>
      <definitionTable>
        <definedTerm>Returning the setting of a connection attribute</definedTerm>
        <definition>
          <para>
            <link xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</link>
          </para>
        </definition>
        <definedTerm>Determining whether a driver supports a function</definedTerm>
        <definition>
          <para>
            <link xlink:href="0451d2f9-0f4f-46ba-b252-670956a52183">SQLGetFunctions Function</link>
          </para>
        </definition>
        <definedTerm>Returning the setting of a statement attribute</definedTerm>
        <definition>
          <para>
            <link xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</link>
          </para>
        </definition>
        <definedTerm>Returning information about a data source's data types</definedTerm>
        <definition>
          <para>
            <link xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo Function</link>
          </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>