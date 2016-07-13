---
title: SQLConnect Function
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
  - SQLConnect
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConnect Function
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
          <legacyBold>SQLConnect</legacyBold> establishes connections to a driver and a data source. The connection handle references storage of all information about the connection to the data source, including status, transaction state, and error information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLConnect</legacyBold>(
     SQLHDBC        <parameterReference>ConnectionHandle</parameterReference>,
     SQLCHAR *      <parameterReference>ServerName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength1</parameterReference>,
     SQLCHAR *      <parameterReference>UserName</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength2</parameterReference>,
     SQLCHAR *      <parameterReference>Authentication</parameterReference>,
     SQLSMALLINT    <parameterReference>NameLength3</parameterReference>);</legacySyntax>
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
          <legacyItalic>ServerName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Data source name. The data might be located on the same computer as the program, or on another computer somewhere on a network. For information about how an application chooses a data source, see <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>ServerName</legacyItalic> in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>UserName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] User identifier.</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength2</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>UserName</legacyItalic> in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Authentication</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Authentication string (typically the password).</para>
        </definition>
        <definedTerm>
          <legacyItalic>NameLength3</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>Authentication</legacyItalic> in characters.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLConnect</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLConnect</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The driver did not support the specified value of the <legacyItalic>ValuePtr </legacyItalic>argument in <legacyBold>SQLSetConnectAttr</legacyBold> and substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The specified <legacyItalic>ConnectionHandle</legacyItalic> had already been used to establish a connection with a data source, and the connection was still open or the user was browsing for a connection.</para>
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
              <para>The communication link between the driver and the data source to which the driver was trying to connect failed before the function completed processing.</para>
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
              <para>The value specified for the argument <legacyItalic>UserName</legacyItalic> or the value specified for the argument <legacyItalic>Authentication</legacyItalic> violated restrictions defined by the data source.</para>
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
              <para>(DM) The Driver Manager was unable to allocate memory that is required to support execution or completion of the function.</para>
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
              <para>Asynchronous processing was enabled for the <parameterReference>ConnectionHandle</parameterReference>. The <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference> function was called, and before it completed execution, <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link> was called on the <parameterReference>ConnectionHandle</parameterReference>, and then the <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference> function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
              <para>Or, the <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference> function was called, and before it completed execution, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was called on the <parameterReference>ConnectionHandle</parameterReference> from a different thread in a multithread application.</para>
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
              <para>(DM) An asynchronously executing function (not this one) was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when this function was called.</para>
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
              <para>Invalid string or buffer length </para>
            </TD>
            <TD>
              <para>(DM) The value specified for argument <legacyItalic>NameLength1</legacyItalic>,<legacyItalic> NameLength2</legacyItalic>, or <legacyItalic>NameLength3 </legacyItalic>was less than 0 but not equal to SQL_NTS.</para>
              <para>(DM) The value specified for argument <legacyItalic>NameLength1</legacyItalic> exceeded the maximum length for a data source name.</para>
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
              <para>The query timeout period expired before the connection to the data source completed. The timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_LOGIN_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY114</para>
            </TD>
            <TD>
              <para>Driver does not support connection level asynchronous function execution</para>
            </TD>
            <TD>
              <para>(DM) The application enabled the asynchronous operation on the connection handle before making the connection. However, the driver does not support asynchronous operations on the connection handle.</para>
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
              <para>(DM) The driver specified by the data source name does not support the function.</para>
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
              <para>(DM) The data source name specified in the argument <legacyItalic>ServerName</legacyItalic> was not found in the system information, nor was there a default driver specification.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM003</para>
            </TD>
            <TD>
              <para>Specified driver could not be connected to</para>
            </TD>
            <TD>
              <para>(DM) The driver listed in the data source specification in system information was not found or could not be connected to for some other reason.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM004</para>
            </TD>
            <TD>
              <para>Driver's SQLAllocHandle on SQL_HANDLE_ENV failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM005</para>
            </TD>
            <TD>
              <para>Driver's SQLAllocHandle on SQL_HANDLE_DBC failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM006</para>
            </TD>
            <TD>
              <para>Driver's SQLSetConnectAttr failed</para>
            </TD>
            <TD>
              <para>During <legacyBold>SQLConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLSetConnectAttr</legacyBold> function and the driver returned an error. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM009</para>
            </TD>
            <TD>
              <para>Unable to connect to translation DLL</para>
            </TD>
            <TD>
              <para>The driver was unable to connect to the translation DLL that was specified for the data source.</para>
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
              <para>(DM) <legacyItalic>*ServerName</legacyItalic> was longer than SQL_MAX_DSN_LENGTH characters.</para>
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
              <para>Driver's SQLConnect on SQL_HANDLE_DBC_INFO_HANDLE failed</para>
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
      <para>For information about why an application uses <legacyBold>SQLConnect</legacyBold>, see <legacyLink xlink:href="b16319d2-2c2c-4341-abb5-caa9e17362b4">Connecting with SQLConnect</legacyLink>.</para>
      <para>The Driver Manager does not connect to a driver until the application calls a function (<legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, or <legacyBold>SQLBrowseConnect</legacyBold>) to connect to the driver. Until that point, the Driver Manager works with its own handles and manages connection information. When the application calls a connection function, the Driver Manager checks whether a driver is currently connected to for the specified <legacyItalic>ConnectionHandle</legacyItalic>:</para>
      <list class="bullet">
        <listItem>
          <para>If a driver is not connected to, the Driver Manager connects to the driver and calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType </legacyItalic>of SQL_HANDLE_ENV, <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC, <legacyBold>SQLSetConnectAttr</legacyBold> (if the application specified any connection attributes), and the connection function in the driver. The Driver Manager returns SQLSTATE IM006 (Driver's <legacyBold>SQLSetConnectOption</legacyBold> failed) and SQL_SUCCESS_WITH_INFO for the connection function if the driver returned an error for <legacyBold>SQLSetConnectAttr</legacyBold>. For more information, see <legacyLink xlink:href="e93027ab-9e60-47b7-ba96-8289dae32a22">Connecting to a Data Source or Driver</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>If the specified driver is already connected to on the <legacyItalic>ConnectionHandle</legacyItalic>, the Driver Manager calls only the connection function in the driver. In this case, the driver must make sure that all connection attributes for the <legacyItalic>ConnectionHandle</legacyItalic> maintain their current settings.</para>
        </listItem>
        <listItem>
          <para>If a different driver is connected to, the Driver Manager calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC, and then, if no other driver is connected to in that environment, it calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV in the connected driver and then disconnects that driver. It then performs the same operations as when a driver is not connected to.</para>
        </listItem>
      </list>
      <para>The driver then allocates handles and initializes itself.</para>
      <para>When the application calls <legacyBold>SQLDisconnect</legacyBold>, the Driver Manager calls <legacyBold>SQLDisconnect</legacyBold> in the driver. However, it does not disconnect the driver. This keeps the driver in memory for applications that repeatedly connect to and disconnect from a data source. When the application calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC, the Driver Manager calls <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and then <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV in the driver, and then disconnects the driver.</para>
      <para>An ODBC application can establish more than one connection.</para>
    </content>
  </section>
  <section>
    <title>Driver Manager Guidelines</title>
    <content>
      <para>The contents of *<legacyItalic>ServerName</legacyItalic> affect how the Driver Manager and a driver work together to establish a connection to a data source.  </para>
      <list class="bullet">
        <listItem>
          <para>If *<legacyItalic>ServerName</legacyItalic> contains a valid data source name, the Driver Manager locates the corresponding data source specification in the system information and connects to the associated driver. The Driver Manager passes each <legacyBold>SQLConnect</legacyBold> argument to the driver.</para>
        </listItem>
        <listItem>
          <para>If the data source name cannot be found or <legacyItalic>ServerName</legacyItalic> is a null pointer, the Driver Manager locates the default data source specification and connects to the associated driver. The Driver Manager passes to the driver the <legacyItalic>UserName</legacyItalic> and <legacyItalic>Authentication</legacyItalic> arguments unmodified, and "DEFAULT" for the <legacyItalic>ServerName</legacyItalic> argument.</para>
        </listItem>
        <listItem>
          <para>If the <legacyItalic>ServerName</legacyItalic> argument is "DEFAULT", the Driver Manager locates the default data source specification and connects to the associated driver. The Driver Manager passes each <legacyBold>SQLConnect</legacyBold> argument to the driver.</para>
        </listItem>
        <listItem>
          <para>If the data source name cannot be found or <legacyItalic>ServerName</legacyItalic> is a null pointer, and the default data source specification does not exist, the Driver Manager returns SQL_ERROR with SQLSTATE IM002 (Data source name not found and no default driver specified).</para>
        </listItem>
      </list>
      <para>After it is connected to by the Driver Manager, a driver can locate its corresponding data source specification in the system information and use driver-specific information from the specification to complete its set of required connection information.</para>
      <para>If a default translation library is specified in the system information for the data source, the driver connects to it. A different translation library can be connected to by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRANSLATE_LIB attribute. A translation option can be specified by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRANSLATE_OPTION attribute.</para>
      <para>If a driver supports <legacyBold>SQLConnect</legacyBold>, the driver keyword section of the system information for the driver must contain the <legacyBold>ConnectFunctions</legacyBold> keyword with the first character set to "Y."</para>
    </content>
    <sections>
      <section>
        <title>Connection Pooling</title>
        <content>
          <para>Connection pooling allows an application to reuse a connection that has already been created. When connection pooling is enabled and <legacyBold>SQLConnect</legacyBold> is called, the Driver Manager tries to make the connection using a connection that is part of a pool of connections in an environment that has been designated for connection pooling. This environment is a shared environment that is used by all applications that use the connections in the pool.</para>
          <para>Connection pooling is enabled before the environment is allocated by calling <legacyBold>SQLSetEnvAttr</legacyBold> to set SQL_ATTR_CONNECTION_POOLING to SQL_CP_ONE_PER_DRIVER (which specifies a maximum of one pool per driver) or SQL_CP_ONE_PER_HENV (which specifies a maximum of one pool per environment). <legacyBold>SQLSetEnvAttr</legacyBold> in this case is called with <legacyItalic>EnvironmentHandle</legacyItalic> set to null, which makes the attribute a process-level attribute. If SQL_ATTR_CONNECTION_POOLING is set to SQL_CP_OFF, connection pooling is disabled.</para>
          <para>After connection pooling has been enabled, <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV is called to allocate an environment. The environment allocated by this call is a shared environment because connection pooling has been enabled. However, the environment that will be used is not determined until <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC is called.</para>
          <para>
            <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC is called to allocate a connection. The Driver Manager tries to find an existing shared environment that matches the environment attributes set by the application. If no such environment exists, one is created as an implicit <legacyItalic>shared environment</legacyItalic>. If a matching shared environment is found, the environment handle is returned to the application and its reference count is incremented.</para>
          <para>However, the connection that will be used is not determined until <legacyBold>SQLConnect</legacyBold> is called. At that point, the Driver Manager tries to find an existing connection in the connection pool that matches the criteria requested by the application. These criteria include the connection options requested in the call to <legacyBold>SQLConnect</legacyBold> (the values of the <legacyItalic>ServerName</legacyItalic>, <legacyItalic>UserName</legacyItalic>, and <legacyItalic>Authentication</legacyItalic> keywords) and any connection attributes set since <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC was called. The Driver Manager checks these criteria against the corresponding connection keywords and attributes in connections in the pool. If a match is found, the connection in the pool is used. If no match is found, a new connection is created.</para>
          <para>If the SQL_ATTR_CP_MATCH environment attribute is set to SQL_CP_STRICT_MATCH, the match must be exact for a connection in the pool to be used. If the SQL_ATTR_CP_MATCH environment attribute is set to SQL_CP_RELAXED_MATCH, the connection options in the call to <legacyBold>SQLConnect</legacyBold> must match but not all the connection attributes must match.</para>
          <para>The following rules are applied when a connection attribute, as set by the application before <legacyBold>SQLConnect</legacyBold> is called, does not match the connection attribute of the connection in the pool:</para>
          <list class="bullet">
            <listItem>
              <para>If the connection attribute must be set before the connection is made: </para>
              <para>If SQL_ATTR_CP_MATCH is SQL_CP_STRICT_MATCH, SQL_ATTR_PACKET_SIZE in the pooled connection must be identical to the attribute set by the application. If SQL_CP_RELAXED_MATCH, the values of SQL_ATTR_PACKET_SIZE can be different.</para>
              <para>The value of SQL_ATTR_LOGIN_VALUE does not affect the match. </para>
            </listItem>
            <listItem>
              <para>If the connection attribute can be set either before or after the connection is made:</para>
              <para>If the connection attribute has not been set by the application but has been set on the connection in the pool, and there is a default, the connection attribute in the pooled connection is set back to the default and a match is declared. If there is no default, the pooled connection is not considered a match.</para>
              <para>If the connection attribute has been set by the application but has not been set on the connection in the pool, the connection attribute on the pool is changed to that set by the application and a match is declared.</para>
              <para>If the connection attribute has been set by the application, and has also been set on the connection in the pool but the values are different, the value of the application's connection attribute is used and a match is declared.</para>
            </listItem>
            <listItem>
              <para>If the values of driver-specific connection attributes are not identical and SQL_ATTR_CP_MATCH is set to SQL_CP_STRICT_MATCH, the connection in the pool is not used.</para>
            </listItem>
          </list>
          <para>When the application calls <legacyBold>SQLDisconnect</legacyBold> to disconnect, the connection is returned to the connection pool and is available for reuse.</para>
        </content>
      </section>
      <section>
        <title>Optimizing Connection Pooling Performance</title>
        <content>
          <para>When distributed transactions are involved, it is possible to optimize connection pooling performance by using <legacyBold>SQL_DTC_TRANSITION_COST</legacyBold>, which is a SQLUINTEGER bitmask. The transitions referred to are the transitions of the connection attribute SQL_ATTR_ENLIST_IN_DTC going from value 0 to nonzero, and vice versa. This is a connection going from not enlisted in a distributed transaction to enlisted in a distributed transaction, and vice versa. Depending on how the driver has implemented enlistment (setting connection attribute SQL_ATTR_ENLIST_IN_DTC), these transitions may be expensive and should therefore be avoided for best performance.</para>
          <para>The value returned by the driver contains any combination of the following bits:  </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>SQL_DTC_ENLIST_EXPENSIVE</legacyBold>, when set, implies the zero to nonzero transition is significantly more expensive than a transition from nonzero to another nonzero value (enlisting a previously enlisted connection in its next transaction).</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>SQL_DTC_UNENLIST_EXPENSIVE</legacyBold>, when set, implies the nonzero to zero transition is significantly more expensive than using a connection whose SQL_ATTR_ENLIST_IN_DTC attribute is already set to zero.</para>
            </listItem>
          </list>
          <para>There is a performance versus connection usage tradeoff. If a driver indicates that one or more of these transitions are expensive, the driver manager's connection pooler responds to this by keeping more connections in the pool. Some of the connections in the pool are preferred for nontransactional use, and some are preferred for transactional use. However, if the driver indicates that these transitions are not expensive, fewer connections can be used, perhaps alternating between nontransactional and transactional use.</para>
          <para>Drivers that do not support SQL_ATTR_ENLIST_IN_DTC do not need to support SQL_DTC_TRANSITION_COST. For drivers that support SQL_ATTR_ENLIST_IN_DTC but not SQL_DTC_TRANSITION_COST, it is assumed that the transitions are not expensive, as if the driver returned 0 (no bits set) for this value.</para>
          <para>Although SQL_DTC_TRANSITION_COST was introduced in ODBC 3.5, an ODBC 2.<legacyItalic>x</legacyItalic> driver can also support it because the driver manager will query this information regardless of the driver version.</para>
        </content>
      </section>
      <section>
        <title>Code Example</title>
        <content>
          <para>In the following example, an application allocates environment and connection handles. It then connects to the SalesOrders data source with the user ID JohnS and the password Sesame and processes data. When it has finished processing data, it disconnects from the data source and frees the handles.</para>
          <code>// SQLConnect_ref.cpp
// compile with: odbc32.lib
#include &lt;windows.h&gt;
#include &lt;sqlext.h&gt;

int main() {
   SQLHENV henv;
   SQLHDBC hdbc;
   SQLHSTMT hstmt;
   SQLRETURN retcode;

   SQLCHAR * OutConnStr = (SQLCHAR * )malloc(255);
   SQLSMALLINT * OutConnStrLen = (SQLSMALLINT *)malloc(255);

   // Allocate environment handle
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);

   // Set the ODBC version environment attribute
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0); 

      // Allocate connection handle
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc); 

         // Set login timeout to 5 seconds
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);

            // Connect to data source
            retcode = SQLConnect(hdbc, (SQLCHAR*) "NorthWind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);

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
                  <para>Connecting to a data source using a connection string or dialog box</para>
                </TD>
                <TD>
                  <para>
                    <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink>
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
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>