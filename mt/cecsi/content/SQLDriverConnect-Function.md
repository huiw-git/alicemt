---
title: SQLDriverConnect Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLDriverConnect
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDriverConnect Function
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
          <legacyBold>SQLDriverConnect</legacyBold> is an alternative to <legacyBold>SQLConnect</legacyBold>. It supports data sources that require more connection information than the three arguments in <legacyBold>SQLConnect</legacyBold>, dialog boxes to prompt the user for all connection information, and data sources that are not defined in the system information.</para>
        <para>
          <legacyBold>SQLDriverConnect</legacyBold> provides the following connection attributes:</para>
        <list class="bullet">
          <listItem>
            <para>Establish a connection using a connection string that contains the data source name, one or more user IDs, one or more passwords, and other information required by the data source.</para>
          </listItem>
          <listItem>
            <para>Establish a connection using a partial connection string or no additional information; in this case, the Driver Manager and the driver can each prompt the user for connection information.</para>
          </listItem>
          <listItem>
            <para>Establish a connection to a data source that is not defined in the system information. If the application supplies a partial connection string, the driver can prompt the user for connection information.</para>
          </listItem>
          <listItem>
            <para>Establish a connection to a data source using a connection string constructed from the information in a .dsn file.</para>
          </listItem>
        </list>
        <para>After a connection is established, <legacyBold>SQLDriverConnect</legacyBold> returns the completed connection string. The application can use this string for subsequent connection requests. For more information, see <legacyLink xlink:href="e46e959f-d3c5-4ddb-810a-107bfcb83fd2">Connecting with SQLDriverConnect</legacyLink>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLDriverConnect</legacyBold>(
     SQLHDBC         <parameterReference>ConnectionHandle</parameterReference>,
     SQLHWND         <parameterReference>WindowHandle</parameterReference>,
     SQLCHAR *       <parameterReference>InConnectionString</parameterReference>,
     SQLSMALLINT     <parameterReference>StringLength1</parameterReference>,
     SQLCHAR *       <parameterReference>OutConnectionString</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
     SQLSMALLINT *   <parameterReference>StringLength2Ptr</parameterReference>,
     SQLUSMALLINT    <parameterReference>DriverCompletion</parameterReference>);</legacySyntax>
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
          <legacyItalic>WindowHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Window handle. The application can pass the handle of the parent window, if applicable, or a null pointer if either the window handle is not applicable or <legacyBold>SQLDriverConnect</legacyBold> will not present any dialog boxes.</para>
        </definition>
        <definedTerm>
          <legacyItalic>InConnectionString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A full connection string (see the syntax in "Comments"), a partial connection string, or an empty string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>InConnectionString</legacyItalic>, in characters if the string is Unicode, or bytes if string is ANSI or DBCS.</para>
        </definition>
        <definedTerm>
          <legacyItalic>OutConnectionString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer for the completed connection string. Upon successful connection to the target data source, this buffer contains the completed connection string. Applications should allocate at least 1,024 characters for this buffer.</para>
          <para>If <legacyItalic>OutConnectionString</legacyItalic> is NULL, <legacyItalic>StringLength2Ptr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>OutConnectionString</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<legacyItalic>OutConnectionString</legacyItalic> buffer, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength2Ptr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null-termination character) available to return in *<legacyItalic>OutConnectionString</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the completed connection string in *<legacyItalic>OutConnectionString</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DriverCompletion</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Flag that indicates whether the Driver Manager or driver must prompt for more connection information:</para>
          <para>SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE,  SQL_DRIVER_COMPLETE_REQUIRED, or SQL_DRIVER_NOPROMPT.   </para>
          <para>(For additional information, see "Comments.") </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLDriverConnect</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with an <legacyItalic>fHandleType</legacyItalic> of SQL_HANDLE_DBC and an <legacyItalic>hHandle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLDriverConnect</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>OutConnectionString</legacyItalic> was not large enough to return the entire connection string, so the connection string was truncated. The length of the untruncated connection string is returned in *<legacyItalic>StringLength2Ptr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S00</para>
            </TD>
            <TD>
              <para>Invalid connection string attribute</para>
            </TD>
            <TD>
              <para>An invalid attribute keyword was specified in the connection string (<legacyItalic>InConnectionString</legacyItalic>), but the driver was able to connect to the data source anyway. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The driver did not support the specified value pointed to by the <legacyItalic>ValuePtr</legacyItalic> argument in <legacyBold>SQLSetConnectAttr</legacyBold> and substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S08</para>
            </TD>
            <TD>
              <para>Error saving file DSN</para>
            </TD>
            <TD>
              <para>The string in <legacyItalic>*InConnectionString</legacyItalic> contained a <legacyBold>FILEDSN</legacyBold> keyword, but the .dsn file was not saved. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S09</para>
            </TD>
            <TD>
              <para>Invalid keyword</para>
            </TD>
            <TD>
              <para>(DM) The string in <legacyItalic>*InConnectionString</legacyItalic> contained a <legacyBold>SAVEFILE</legacyBold> keyword but not a <legacyBold>DRIVER</legacyBold> or a <legacyBold>FILEDSN</legacyBold> keyword. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08001</para>
            </TD>
            <TD>
              <para>Client unable to establish connection</para>
            </TD>
            <TD>
              <para>The driver was unable to establish a connection with the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08002</para>
            </TD>
            <TD>
              <para>Connection name in use</para>
            </TD>
            <TD>
              <para>(DM) The specified <legacyItalic>ConnectionHandle</legacyItalic> had already been used to establish a connection with a data source, and the connection was still open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08004</para>
            </TD>
            <TD>
              <para>Server rejected the connection</para>
            </TD>
            <TD>
              <para>The data source rejected the establishment of the connection for implementation-defined reasons.</para>
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
              <para>The communication link between the driver and the data source to which the driver was attempting to connect failed before the <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function completed processing.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>28000</para>
            </TD>
            <TD>
              <para>Invalid authorization specification</para>
            </TD>
            <TD>
              <para>Either the user identifier or the authorization string, or both, as specified in the connection string (<legacyItalic>InConnectionString</legacyItalic>), violated restrictions defined by the data source.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*szMessageText</legacyItalic> buffer describes the error and its cause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error: Invalid file dsn</para>
            </TD>
            <TD>
              <para>(DM) The string in *<parameterReference>InConnectionString</parameterReference> contained a FILEDSN keyword, but the name of the .dsn file was not found.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error: Unable to create file buffer</para>
            </TD>
            <TD>
              <para>(DM) The string in *<parameterReference>InConnectionString</parameterReference> contained a FILEDSN keyword, but the .dsn file was unreadable.</para>
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
              <para>The Driver Manager was unable to allocate memory required to support execution or completion of the <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function.</para>
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
              <para>Asynchronous processing was enabled for the <parameterReference>ConnectionHandle</parameterReference>. The function was called, and before it completed execution, the <legacyLink xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle function</legacyLink> was called on the <parameterReference>ConnectionHandle</parameterReference>, and then the <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
              <para>Or, the <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function was called, and before it completed execution, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was called on the <parameterReference>ConnectionHandle</parameterReference> from a different thread in a multithread application.</para>
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
              <para>(DM) Another asynchronously executing function (not <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference>) was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when the <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function was called.</para>
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
              <para>The <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
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
              <para>(DM) The value specified for argument <legacyItalic>StringLength1</legacyItalic> was less than 0 and was not equal to SQL_NTS.</para>
              <para>(DM) The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
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
              <para>(DM) The <legacyItalic>DriverCompletion</legacyItalic> argument was SQL_DRIVER_PROMPT, and the <legacyItalic>WindowHandle</legacyItalic> argument was a null pointer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY110</para>
            </TD>
            <TD>
              <para>Invalid driver completion</para>
            </TD>
            <TD>
              <para>(DM) The value specified for the argument <legacyItalic>DriverCompletion</legacyItalic> was not equal to SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED, or SQL_DRIVER_NOPROMPT.</para>
              <para>(DM) Connection pooling was enabled, and the value specified for the argument <legacyItalic>DriverCompletion</legacyItalic> was not equal to SQL_DRIVER_NOPROMPT.</para>
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
              <para>The driver does not support the version of ODBC behavior that the application requested.</para>
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
              <para>The login timeout period expired before the connection to the data source completed. The timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_LOGIN_TIMEOUT.</para>
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
              <para>(DM) The driver corresponding to the specified data source name does not support the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM002</para>
            </TD>
            <TD>
              <para>Data source not found and no default driver specified</para>
            </TD>
            <TD>
              <para>(DM) The data source name specified in the connection string (<legacyItalic>InConnectionString</legacyItalic>) was not found in the system information, and there was no default driver specification.</para>
              <para>(DM) ODBC data source and default driver information could not be found in the system information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM003</para>
            </TD>
            <TD>
              <para>Specified driver could not be loaded</para>
            </TD>
            <TD>
              <para>(DM) The driver listed in the data source specification in the system information or specified by the <legacyBold>DRIVER</legacyBold> keyword was not found or could not be loaded for some other reason.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM004</para>
            </TD>
            <TD>
              <para>Driver's <legacyBold>SQLAllocHandle</legacyBold> on SQL_HANDLE_ENV failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLDriverConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with an <legacyItalic>fHandleType</legacyItalic> of SQL_HANDLE_ENV and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM005</para>
            </TD>
            <TD>
              <para>Driver's <legacyBold>SQLAllocHandle</legacyBold> on SQL_HANDLE_DBC failed.</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLDriverConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with an <legacyItalic>fHandleType</legacyItalic> of SQL_HANDLE_DBC and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM006</para>
            </TD>
            <TD>
              <para>Driver's <legacyBold>SQLSetConnectAttr</legacyBold> failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLDriverConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLSetConnectAttr</legacyBold> function and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM007</para>
            </TD>
            <TD>
              <para>No data source or driver specified; dialog prohibited</para>
            </TD>
            <TD>
              <para>No data source name or driver was specified in the connection string, and <legacyItalic>DriverCompletion</legacyItalic> was SQL_DRIVER_NOPROMPT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM008</para>
            </TD>
            <TD>
              <para>Dialog failed</para>
            </TD>
            <TD>
              <para>The driver attempted to display its login dialog box and failed.</para>
              <para>  <legacyItalic>WindowHandle</legacyItalic> was a null pointer, and <legacyItalic>DriverCompletion</legacyItalic> was not SQL_DRIVER_NO_PROMPT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM009</para>
            </TD>
            <TD>
              <para>Unable to load translation DLL</para>
            </TD>
            <TD>
              <para>The driver was unable to load the translation DLL that was specified for the data source or for the connection.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM010</para>
            </TD>
            <TD>
              <para>Data source name too long</para>
            </TD>
            <TD>
              <para>(DM) The attribute value for the DSN keyword was longer than SQL_MAX_DSN_LENGTH characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM011</para>
            </TD>
            <TD>
              <para>Driver name too long</para>
            </TD>
            <TD>
              <para>(DM) The attribute value for the <legacyBold>DRIVER</legacyBold> keyword was longer than 255 characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM012</para>
            </TD>
            <TD>
              <para>DRIVER keyword syntax error</para>
            </TD>
            <TD>
              <para>(DM) The keyword-value pair for the <legacyBold>DRIVER</legacyBold> keyword contained a syntax error.</para>
              <para>(DM) The string in <legacyItalic>*InConnectionString</legacyItalic> contained a <legacyBold>FILEDSN</legacyBold> keyword, but the .dsn file did not contain a <legacyBold>DRIVER</legacyBold> keyword or a <legacyBold>DSN</legacyBold> keyword.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM014</para>
            </TD>
            <TD>
              <para>The specified DSN contains an architecture mismatch between the Driver and Application</para>
            </TD>
            <TD>
              <para>(DM) 32-bit application uses a DSN connecting to a 64-bit driver; or vice versa.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM015</para>
            </TD>
            <TD>
              <para>Driver's SQLDriverConnect on SQL_HANDLE_DBC_INFO_HANDLE failed</para>
            </TD>
            <TD>
              <para>If a driver returns SQL_ERROR, the Driver Manager will return SQL_ERROR to the application and the connection will fail.</para>
              <para>For more information about SQL_HANDLE_DBC_INFO_TOKEN, see <link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link>.</para>
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
          <tr>
            <TD>
              <para>S1118</para>
            </TD>
            <TD>
              <para>Driver does not support asynchronous notification</para>
            </TD>
            <TD>
              <para>When the driver does not support asynchronous notification, you cannot set SQL_ATTR_ASYNC_DBC_EVENT or SQL_ATTR_ASYNC_DBC_RETCODE_PTR.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>A connection string has the following syntax:</para>
      <para>
        <legacyItalic>connection-string</legacyItalic> ::= <legacyItalic>empty-string</legacyItalic>[;] | <legacyItalic>attribute</legacyItalic>[;] | <legacyItalic>attribute</legacyItalic>; <legacyItalic>connection-string</legacyItalic></para>
      <para>
        <legacyItalic>empty-string</legacyItalic> ::=<legacyItalic>attribute</legacyItalic> ::= <legacyItalic>attribute-keyword</legacyItalic>=<legacyItalic>attribute-value</legacyItalic> | DRIVER=[{]<legacyItalic>attribute-value</legacyItalic>[}]</para>
      <para>
        <legacyItalic>attribute-keyword</legacyItalic> ::= DSN | UID | PWD | <legacyItalic>driver-defined-attribute-keyword</legacyItalic></para>
      <para>
        <legacyItalic>attribute-value</legacyItalic> ::= <legacyItalic>character-string</legacyItalic></para>
      <para>
        <legacyItalic>driver-defined-attribute-keyword</legacyItalic> ::= <legacyItalic>identifier</legacyItalic></para>
      <para>where <legacyItalic>character-string</legacyItalic> has zero or more characters; <legacyItalic>identifier</legacyItalic> has one or more characters; <legacyItalic>attribute-keyword</legacyItalic> is not case-sensitive; <legacyItalic>attribute-value</legacyItalic> may be case-sensitive; and the value of the <legacyBold>DSN</legacyBold> keyword does not consist solely of blanks. </para>
      <para>Because of connection string and initialization file grammar, keywords and attribute values that contain the characters <legacyBold>[]{}(),;?*=!@</legacyBold> not enclosed with braces should be avoided. The value of the <legacyBold>DSN</legacyBold> keyword cannot consist only of blanks and should not contain leading blanks. Because of the grammar of the system information, keywords and data source names cannot contain the backslash (\) character.</para>
      <para>Applications do not have to add braces around the attribute value after the <legacyBold>DRIVER </legacyBold>keyword unless the attribute contains a semicolon (;), in which case the braces are required. If the attribute value that the driver receives includes braces, the driver should not remove them but they should be part of the returned connection string.</para>
      <para>A DSN or connection string value enclosed with braces ({}) containing any of the characters <legacyBold>[]{}(),;?*=!@</legacyBold> is passed intact to the driver. However, when using these characters in a keyword, the Driver Manager returns an error when working with file DSNs but passes the connection string to the driver for regular connection strings. Avoid using embedded braces in a keyword value.</para>
      <para>The connection string may include any number of driver-defined keywords. Because the <legacyBold>DRIVER</legacyBold> keyword does not use information from the system information, the driver must define enough keywords so that a driver can connect to a data source using only the information in the connection string. (For more information, see "Driver Guidelines," later in this section.) The driver defines which keywords are required to connect to the data source.</para>
      <para>The following table describes the attribute values of the <legacyBold>DSN</legacyBold>, <legacyBold>FILEDSN</legacyBold>, <legacyBold>DRIVER</legacyBold>, <legacyBold>UID</legacyBold>, <legacyBold>PWD</legacyBold>, and <legacyBold>SAVEFILE</legacyBold> keywords.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
            </TD>
            <TD>
              <para>Attribute value description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>DSN</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Name of a data source as returned by <legacyBold>SQLDataSources</legacyBold> or the data sources dialog box of <legacyBold>SQLDriverConnect</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>FILEDSN</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Name of a .dsn file from which a connection string will be built for the data source. These data sources are called file data sources.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>DRIVER</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Description of the driver as returned by the <legacyBold>SQLDrivers</legacyBold> function. For example, Rdb or SQL Server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>UID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>A user ID.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>PWD</legacyBold>
              </para>
            </TD>
            <TD>
              <para>The password corresponding to the user ID, or an empty string if there is no password for the user ID (PWD=;).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SAVEFILE</legacyBold>
              </para>
            </TD>
            <TD>
              <para>The file name of a .dsn file in which the attribute values of keywords used in making the present, successful connection should be saved.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For information about how an application chooses a data source or driver, see <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>.</para>
      <para>If any keywords are repeated in the connection string, the driver uses the value associated with the first occurrence of the keyword. If the <legacyBold>DSN</legacyBold> and <legacyBold>DRIVER</legacyBold> keywords are included in the same connection string, the Driver Manager and the driver use whichever keyword appears first. </para>
      <para>The <legacyBold>FILEDSN</legacyBold> and <legacyBold>DSN</legacyBold> keywords are mutually exclusive: whichever keyword appears first is used, and the one that appears second is ignored. The <legacyBold>FILEDSN</legacyBold> and <legacyBold>DRIVER</legacyBold> keywords, on the other hand, are not mutually exclusive. If any keyword appears in a connection string with <legacyBold>FILEDSN</legacyBold>, then the attribute value of the keyword in the connection string is used rather than the attribute value of the same keyword in the .dsn file. </para>
      <para>If the <legacyBold>FILEDSN</legacyBold> keyword is used, the keywords specified in a .dsn file are used to create a connection string. (For more information, see "File Data Sources," later in this section.) The <legacyBold>UID</legacyBold> keyword is optional; a .dsn file may be created with only the <legacyBold>DRIVER</legacyBold> keyword. The <legacyBold>PWD</legacyBold> keyword is not stored in a .dsn file. The default directory for saving and loading a .dsn file will be a combination of the path specified by <legacyBold>CommonFileDir</legacyBold> in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Windows\CurrentVersion and "ODBC\DataSources". (If CommonFileDir were "C:\Program Files\Common Files", the default directory would be "C:\Program Files\Common Files\ODBC\Data Sources".) </para>
      <alert class="note">
        <para>A .dsn file can be manipulated directly by calling the <legacyLink xlink:href="ead464aa-cdc3-47dd-a0c0-997711205d31">SQLReadFileDSN</legacyLink> and <legacyLink xlink:href="9e18f56f-1061-416b-83d4-ffeec42ab5a9">SQLWriteFileDSN</legacyLink> functions in the installer DLL.</para>
      </alert>
      <para>If the <legacyBold>SAVEFILE</legacyBold> keyword is used, the attribute values of keywords used in making the present, successful connection will be saved as a .dsn file with the name of the attribute value of the <legacyBold>SAVEFILE</legacyBold> keyword. The <legacyBold>SAVEFILE</legacyBold> keyword must be used in conjunction with the <legacyBold>DRIVER</legacyBold> keyword, the <legacyBold>FILEDSN</legacyBold> keyword, or both, or the function returns SQL_SUCCESS_WITH_INFO with SQLSTATE 01S09 (Invalid keyword). The <legacyBold>SAVEFILE</legacyBold> keyword must appear before the <legacyBold>DRIVER</legacyBold> keyword in the connection string, or the results will be undefined.</para>
    </content>
  </section>
  <section>
    <title>Driver Manager Guidelines</title>
    <content>
      <para>The Driver Manager constructs a connection string to pass to the driver in the <legacyItalic>InConnectionString</legacyItalic> argument of the driver's <legacyBold>SQLDriverConnect</legacyBold> function. The Driver Manager does not modify the <legacyItalic>InConnectionString</legacyItalic> argument passed to it by the application.</para>
      <para>The action of the Driver Manager is based on the value of the <legacyItalic>DriverCompletion</legacyItalic> argument:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_DRIVER_PROMPT: If the connection string does not contain either the <legacyBold>DRIVER</legacyBold>, <legacyBold>DSN</legacyBold>, or <legacyBold>FILEDSN</legacyBold> keyword, the Driver Manager displays the Data Sources dialog box. It constructs a connection string from the data source name returned by the dialog box and any other keywords passed to it by the application. If the data source name returned by the dialog box is empty, the Driver Manager specifies the keyword-value pair DSN=Default. (This dialog box will not display a data source with the name "Default".)</para>
        </listItem>
        <listItem>
          <para>SQL_DRIVER_COMPLETE or SQL_DRIVER_COMPLETE_REQUIRED: If the connection string specified by the application includes the <legacyBold>DSN</legacyBold> keyword, the Driver Manager copies the connection string specified by the application. Otherwise, it takes the same actions as it does when <legacyItalic>DriverCompletion</legacyItalic> is SQL_DRIVER_PROMPT.</para>
        </listItem>
        <listItem>
          <para>SQL_DRIVER_NOPROMPT: The Driver Manager copies the connection string specified by the application.</para>
        </listItem>
      </list>
      <para>If the connection string specified by the application contains the <legacyBold>DRIVER</legacyBold> keyword, the Driver Manager copies the connection string specified by the application.</para>
      <para>Using the connection string it has constructed, the Driver Manager determines which driver to use, connects to that driver, and passes the connection string it has constructed to the driver; for more information about the interaction of the Driver Manager and the driver, see the "Comments" section in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>. If the connection string does not contain the <legacyBold>DRIVER</legacyBold> keyword, the Driver Manager determines which driver to use as follows:  </para>
      <list class="ordered">
        <listItem>
          <para>If the connection string contains the <legacyBold>DSN</legacyBold> keyword, the Driver Manager retrieves the driver associated with the data source from the system information.</para>
        </listItem>
        <listItem>
          <para>If the connection string does not contain the <legacyBold>DSN</legacyBold> keyword or the data source is not found, the Driver Manager retrieves the driver associated with the Default data source from the system information. (For more information, see <legacyLink xlink:href="a2259db8-feb7-4f0a-afc8-88e235d86be7">Default Subkey</legacyLink>.) The Driver Manager changes the value of the <legacyBold>DSN</legacyBold> keyword in the connection string to "DEFAULT".</para>
        </listItem>
        <listItem>
          <para>If the <legacyBold>DSN</legacyBold> keyword in the connection string is set to "DEFAULT", the Driver Manager retrieves the driver associated with the Default data source from the system information.</para>
        </listItem>
        <listItem>
          <para>If the data source is not found and the Default data source is not found, the Driver Manager returns SQL_ERROR with SQLSTATE IM002 (Data source not found and no default driver specified).</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>File Data Sources</title>
    <content>
      <para>If the connection string specified by the application in the call to <legacyBold>SQLDriverConnect</legacyBold> contains the <legacyBold>FILEDSN</legacyBold> keyword, and this keyword is not superseded by either the <legacyBold>DSN</legacyBold> or <legacyBold>DRIVER</legacyBold> keyword, then the Driver Manager creates a connection string using the information in the .dsn file and the <legacyItalic>InConnectionString</legacyItalic> argument. The Driver Manager proceeds as follows:  </para>
      <list class="ordered">
        <listItem>
          <para>Checks whether the file name of the .dsn file is valid. If not, it returns SQL_ERROR with SQLSTATE IM014 (Invalid name of file DSN). If the file name is an empty string ("") and SQL_DRIVER_NOPROMPT is not specified, then the <legacyBold>File-Open</legacyBold> dialog box is displayed. If the file name contains a valid path but no file name or an invalid file name, and SQL_DRIVER_NOPROMPT is not specified, then the <legacyBold>File-Open</legacyBold> dialog box is displayed with the current directory set to the one specified in the file name. If the file name is an empty string ("") or the file name contains a valid path but no file name or an invalid file name, and SQL_DRIVER_NOPROMPT is specified, then SQL_ERROR is returned with SQLSTATE IM014 (Invalid name of file DSN).</para>
        </listItem>
        <listItem>
          <para>Reads all keywords in the [ODBC] section of the .dsn file. If the <legacyBold>DRIVER</legacyBold> keyword is not present, it returns SQL_ERROR with SQLSTATE IM012 (Driver keyword syntax error), except where the .dsn file is unshareable and thus contains only the <legacyBold>DSN</legacyBold> keyword. </para>
          <para>If the file data source is unshareable, the Driver Manager reads the value of the <legacyBold>DSN</legacyBold> keyword and connects as necessary to the user or system data source pointed to by the unshareable file data source. Steps 3 through 5 are not performed. </para>
        </listItem>
        <listItem>
          <para>Constructs a connection string for the driver. The driver connection string is the union of the keywords specified in the .dsn file and those specified in the original application connection string. Rules for the construction of the driver connection string where keywords overlap are as follows: </para>
          <list class="bullet">
            <listItem>
              <para>If the <legacyBold>DRIVER</legacyBold> keyword exists in the application connection string and the drivers specified by the <legacyBold>DRIVER</legacyBold> keywords are not the same in the .dsn file and the application connection string, then the driver information in the .dsn file is ignored and the driver information in the application connection string is used. If the drivers specified by the <legacyBold>DRIVER</legacyBold> keyword are the same in the .dsn file and the application's connection string, then where all keywords overlap, those specified in the application connection string have precedence over those specified in the .dsn file.</para>
            </listItem>
            <listItem>
              <para>In the new connection string, the <legacyBold>FILEDSN</legacyBold> keyword is eliminated.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Loads the driver by looking in the registry entry HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.INI\&lt;Driver Name&gt;\Driver where &lt;Driver Name&gt; is specified by the <legacyBold>DRIVER</legacyBold> keyword.</para>
        </listItem>
        <listItem>
          <para>Passes the driver the new connections string.</para>
        </listItem>
      </list>
      <para>For examples of .dsn files, see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>SAVEFILE Keyword</title>
    <content>
      <para>If the connection string specified by the application contains the <legacyBold>SAVEFILE</legacyBold> keyword, then the Driver Manager saves the connection string in a .dsn file. The Driver Manager proceeds as follows:  </para>
      <list class="ordered">
        <listItem>
          <para>Checks whether the file name of the .dsn file included as the attribute value of the <legacyBold>SAVEFILE</legacyBold> keyword is valid. If not, it returns SQL_ERROR with SQLSTATE IM014 (Invalid name of file DSN). The validity of the file name is determined by standard system naming rules. If the file name is an empty string ("") and the <legacyItalic>DriverCompletion</legacyItalic> argument is not SQL_DRIVER_NOPROMPT, then the file name is valid. If the file name already exists, then if <legacyItalic>DriverCompletion</legacyItalic> is SQL_DRIVER_NOPROMPT, the file is overwritten. If <legacyItalic>DriverCompletion</legacyItalic> is SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, or SQL_DRIVER_COMPLETE_REQUIRED, a dialog box prompts the user to specify whether the file should be overwritten. If No is entered, then the <legacyBold>File-Save</legacyBold> dialog box appears.</para>
        </listItem>
        <listItem>
          <para>If the driver returns SQL_SUCCESS and the file name was not an empty string, then the Driver Manager writes the connection information returned in the <legacyItalic>OutConnectionString</legacyItalic> argument to the specified file with the format specified in the "Connection Strings" section earlier in this section.</para>
        </listItem>
        <listItem>
          <para>If the driver returns SQL_SUCCESS and the file name was an empty string (""), then the Driver Manager calls the <legacyBold>File-Save</legacyBold> common dialog box with the <legacyItalic>hwnd</legacyItalic> specified and writes the connection information returned in <legacyItalic>OutConnectionString</legacyItalic> to the file specified in the File-Save common dialog box with the format specified in the "Connection Strings" section earlier in this section.</para>
        </listItem>
        <listItem>
          <para>If the driver returns SQL_SUCCESS, it returns the <legacyItalic>OutConnectionString</legacyItalic> argument containing the connection string to the application.</para>
        </listItem>
        <listItem>
          <para>If the driver returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, then the Driver Manager returns the SQLSTATE to the application.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Driver Guidelines</title>
    <content>
      <para>The driver checks whether the connection string passed to it by the Driver Manager contains the <legacyBold>DSN</legacyBold> or <legacyBold>DRIVER</legacyBold> keyword. If the connection string contains the <legacyBold>DRIVER</legacyBold> keyword, the driver cannot retrieve information about the data source from the system information. If the connection string contains the <legacyBold>DSN</legacyBold> keyword or does not contain either the <legacyBold>DSN</legacyBold> or the <legacyBold>DRIVER</legacyBold> keyword, the driver can retrieve information about the data source from the system information as follows:  </para>
      <list class="ordered">
        <listItem>
          <para>If the connection string contains the <legacyBold>DSN</legacyBold> keyword, the driver retrieves the information for the specified data source.</para>
        </listItem>
        <listItem>
          <para>If the connection string does not contain the <legacyBold>DSN</legacyBold> keyword, the specified data source is not found, or the <legacyBold>DSN</legacyBold> keyword is set to "DEFAULT", the driver retrieves the information for the Default data source.</para>
        </listItem>
      </list>
      <para>The driver uses any information it retrieves from the system information to augment the information passed to it in the connection string. If the information in the system information duplicates information in the connection string, the driver uses the information in the connection string.</para>
      <para>Based on the value of <legacyItalic>DriverCompletion</legacyItalic>, the driver prompts the user for connection information, such as the user ID and password, and connects to the data source:  </para>
      <list class="bullet">
        <listItem>
          <para>SQL_DRIVER_PROMPT: The driver displays a dialog box, using the values from the connection string and system information (if any) as initial values. When the user exits the dialog box, the driver connects to the data source. It also constructs a connection string from the value of the <legacyBold>DSN</legacyBold> or <legacyBold>DRIVER</legacyBold> keyword in *<legacyItalic>InConnectionString</legacyItalic> and the information returned from the dialog box. It places this connection string in the *<legacyItalic>OutConnectionString</legacyItalic> buffer.</para>
        </listItem>
        <listItem>
          <para>SQL_DRIVER_COMPLETE or SQL_DRIVER_COMPLETE_REQUIRED: If the connection string contains enough information, and that information is correct, the driver connects to the data source and copies *<legacyItalic>InConnectionString</legacyItalic> to *<legacyItalic>OutConnectionString</legacyItalic>. If any information is missing or incorrect, the driver takes the same actions as it does when <legacyItalic>DriverCompletion</legacyItalic> is SQL_DRIVER_PROMPT, except that if <legacyItalic>DriverCompletion</legacyItalic> is SQL_DRIVER_COMPLETE_REQUIRED, the driver disables the controls for any information not required to connect to the data source.</para>
        </listItem>
        <listItem>
          <para>SQL_DRIVER_NOPROMPT: If the connection string contains enough information, the driver connects to the data source and copies *<legacyItalic>InConnectionString</legacyItalic> to *<legacyItalic>OutConnectionString</legacyItalic>. Otherwise, the driver returns SQL_ERROR for <legacyBold>SQLDriverConnect</legacyBold>.</para>
        </listItem>
      </list>
      <para>On successful connection to the data source, the driver also sets *<legacyItalic>StringLength2Ptr</legacyItalic> to the length of the output connection string that is available to return in *<legacyItalic>OutConnectionString</legacyItalic>.</para>
      <para>If the user cancels a dialog box presented by the Driver Manager or the driver, <legacyBold>SQLDriverConnect</legacyBold> returns SQL_NO_DATA.</para>
      <para>For information about how the Driver Manager and the driver interact during the connection process, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.</para>
      <para>If a driver supports <legacyBold>SQLDriverConnect</legacyBold>, the driver keyword section of the system information for the driver must contain the <legacyBold>ConnectFunctions</legacyBold> keyword with the second character set to "Y".</para>
    </content>
  </section>
  <section>
    <title>Connecting When Connection Pooling Is Enabled</title>
    <content>
      <para>Connection pooling allows an application to reuse a connection that has already been created. When <legacyBold>SQLDriverConnect</legacyBold> is called, the Driver Manager attempts to make the connection using a connection that is part of a pool of connections in an environment that has been designated for connection pooling. For more information on connection pooling, see <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>.</para>
      <para>An application can set SQL_ATTR_RESET_CONNECTION before calling SQLDisconnect on a connection where pooling is enabled. For more information, see <link xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</link>.</para>
      <para>The following restrictions apply when an application calls <legacyBold>SQLDriverConnect</legacyBold> to connect to a pooled connection:</para>
      <list class="bullet">
        <listItem>
          <para>No connection pooling processing is performed when the <legacyBold>SAVEFILE</legacyBold> keyword is specified in the connection string.</para>
        </listItem>
        <listItem>
          <para>If connection pooling is enabled, <legacyBold>SQLDriverConnect</legacyBold> can be called only with a <legacyItalic>DriverCompletion</legacyItalic> argument of SQL_DRIVER_NOPROMPT; if <legacyBold>SQLDriverConnect</legacyBold> is called with any other <legacyItalic>DriverCompletion</legacyItalic>, SQLSTATE HY110 (Invalid driver completion) will be returned.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Connection Attributes</title>
    <content>
      <para>The SQL_ATTR_LOGIN_TIMEOUT connection attribute, set using <legacyBold>SQLSetConnectAttr</legacyBold>, defines the number of seconds to wait for a login request to complete with a successful connection by the driver before returning to the application. If the user is prompted to complete the connection string, a waiting period for each login request begins when the driver starts the connection process.</para>
      <para>The driver opens the connection in SQL_MODE_READ_WRITE access mode by default. To set the access mode to SQL_MODE_READ_ONLY, the application must call <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_ACCESS_MODE attribute prior to calling <legacyBold>SQLDriverConnect</legacyBold>.</para>
      <para>If a default translation library is specified in the system information for the data source, the driver loads it. A different translation library can be loaded by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRANSLATE_LIB attribute. A translation option can be specified by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRANSLATE_OPTION option.</para>
      <para>For more information, see <legacyLink xlink:href="e46e959f-d3c5-4ddb-810a-107bfcb83fd2">Connecting with SQLDriverConnect</legacyLink>.</para>
      <code>// SQLDriverConnect_ref.cpp
// compile with: odbc32.lib user32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;

int main() {
   SQLHENV henv;
   SQLHDBC hdbc;
   SQLHSTMT hstmt;
   SQLRETURN retcode;

   SQLCHAR OutConnStr[255];
   SQLSMALLINT OutConnStrLen;

   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle

   // Allocate environment handle
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);

   // Set the ODBC version environment attribute
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0); 

      // Allocate connection handle
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 

         // Set login timeout to 5 seconds
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

            retcode = SQLDriverConnect( // SQL_NULL_HDBC
               hdbc, 
               desktopHandle, 
               (SQLCHAR*)"driver=SQL Server", 
               _countof("driver=SQL Server"),
               OutConnStr,
               255, 
               &amp;OutConnStrLen,
               SQL_DRIVER_PROMPT );

            // Allocate statement handle
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {               
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt); 

               // Process data
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);
               }

               SQLDisconnect(hdbc);
            }

            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
         }
      }
      SQLFreeHandle(SQL_HANDLE_ENV, henv);
   }
}</code>
      <para>Also see <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>.</para>
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
              <para>Discovering and enumerating values required to connect to a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Disconnecting from a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9e84a58e-db48-4821-a0cd-5c711fcbe36b">SQLDisconnect Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning driver descriptions and attributes</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers Function</legacyLink>
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
              <para>Setting a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>
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