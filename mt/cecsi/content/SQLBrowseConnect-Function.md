---
title: "SQLBrowseConnect Function"
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
  - SQLBrowseConnect
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
caps.latest.revision: 35
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBrowseConnect Function
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
          <legacyBold>SQLBrowseConnect</legacyBold> supports an iterative method of discovering and enumerating the attributes and attribute values required to connect to a data source. Each call to <legacyBold>SQLBrowseConnect</legacyBold> returns successive levels of attributes and attribute values. When all levels have been enumerated, a connection to the data source is completed and a complete connection string is returned by <legacyBold>SQLBrowseConnect</legacyBold>. A return code of SQL_SUCCESS or SQL_SUCCESS_WITH_INFO indicates that all connection information has been specified and the application is now connected to the data source.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLBrowseConnect</legacyBold>(
     SQLHDBC         <parameterReference>ConnectionHandle</parameterReference>,
     SQLCHAR *       <parameterReference>InConnectionString</parameterReference>,
     SQLSMALLINT     <parameterReference>StringLength1</parameterReference>,
     SQLCHAR *       <parameterReference>OutConnectionString</parameterReference>,
     SQLSMALLINT     <parameterReference>BufferLength</parameterReference>,
     SQLSMALLINT *   <parameterReference>StringLength2Ptr</parameterReference>);</legacySyntax>
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
          <legacyItalic>InConnectionString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Browse request connection string (see "<legacyItalic>InConnectionString</legacyItalic> Argument" in "Comments").</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>InConnectionString</legacyItalic> in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>OutConnectionString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a character buffer in which to return the browse result connection string (see "<legacyItalic>OutConnectionString</legacyItalic> Argument" in "Comments").</para>
          <para>If <legacyItalic>OutConnectionString</legacyItalic> is NULL, <legacyItalic>StringLength2Ptr</legacyItalic> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>OutConnectionString</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length, in characters, of the *<legacyItalic>OutConnectionString</legacyItalic> buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength2Ptr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The total number of characters (excluding null-termination) available to return in *<legacyItalic>OutConnectionString</legacyItalic>. If the number of characters available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the connection string in *<legacyItalic>OutConnectionString</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_ERROR, SQL_SUCCESS_WITH_INFO, or SQL_NEED_DATA, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle of ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLBrowseConnect </legacyBold>and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The buffer *<legacyItalic>OutConnectionString</legacyItalic> was not large enough to return the entire browse result connection string, so the string was truncated. The buffer *<legacyItalic>StringLength2Ptr</legacyItalic> contains the length of the untruncated browse result connection string. (Function returns SQL_NEED_DATA.)</para>
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
              <para>An invalid attribute keyword was specified in the browse request connection string (<legacyItalic>InConnectionString</legacyItalic>). (Function returns SQL_NEED_DATA.)</para>
              <para>An attribute keyword was specified in the browse request connection string (<legacyItalic>InConnectionString</legacyItalic>) that does not apply to the current connection level. (Function returns SQL_NEED_DATA.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S02</para>
            </TD>
            <TD>
              <para>Value changed</para>
            </TD>
            <TD>
              <para>The driver did not support the specified value of the <legacyItalic>ValuePtr</legacyItalic> argument in <legacyBold>SQLSetConnectAttr</legacyBold> and substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) The specified connection had already been used to establish a connection with a data source, and the connection was open.</para>
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
              <para>The communication link between the driver and the data source to which the driver was attempting to connect failed before the function completed processing.</para>
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
              <para>Either the user identifier or the authorization string or both, as specified in the browse request connection string (<legacyItalic>InConnectionString</legacyItalic>), violated restrictions defined by the data source.</para>
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
              <para>(DM) The Driver Manager was unable to allocate memory required to support execution or completion of the function.</para>
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
              <para>An asynchronous operation was canceled by calling <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>. Then, the original function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
              <para>An operation was canceled by calling <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on the <parameterReference>ConnectionHandle</parameterReference> from a different thread in a multithread application. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error </para>
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
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>(DM) The value specified for argument <legacyItalic>StringLength1</legacyItalic> was less than 0 and was not equal to SQL_NTS.</para>
              <para>(DM) The value specified for argument <legacyItalic>BufferLength</legacyItalic> was less than 0.</para>
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
              <para>(DM) The application enabled the asynchronous operation on the connection handle before making the connection. However, the driver does not support asynchronous operation on connection handle.</para>
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
              <para>(DM) The data source name specified in the browse request connection string (<legacyItalic>InConnectionString</legacyItalic>) was not found in the system information, nor was there a default driver specification.</para>
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
              <para>Driver's <legacyBold>SQLAllocHandle</legacyBold> on SQL_HANDLE _ENV failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLBrowseConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and the driver returned an error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM005</para>
            </TD>
            <TD>
              <para>Driver's <legacyBold>SQLAllocHandle</legacyBold> on SQL_HANDLE_DBC failed</para>
            </TD>
            <TD>
              <para>(DM) During <legacyBold>SQLBrowseConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLAllocHandle</legacyBold> function with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and the driver returned an error.</para>
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
              <para>(DM) During <legacyBold>SQLBrowseConnect</legacyBold>, the Driver Manager called the driver's <legacyBold>SQLSetConnectAttr</legacyBold> function and the driver returned an error.</para>
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
              <para>(DM) The attribute value for the DRIVER keyword was longer than 255 characters.</para>
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
              <para>(DM) The keyword-value pair for the DRIVER keyword contained a syntax error.</para>
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
    <title>InConnectionString Argument</title>
    <content>
      <para>A browse request connection string has the following syntax:</para>
      <para>
        <legacyItalic>connection-string</legacyItalic> ::= <legacyItalic>attribute</legacyItalic>[;] | <legacyItalic>attribute</legacyItalic>; <legacyItalic>connection-stringattribute</legacyItalic> ::= <legacyItalic>attribute-keyword</legacyItalic>=<legacyItalic>attribute-value</legacyItalic> | DRIVER=[{]<legacyItalic>attribute-value[</legacyItalic>}]<legacyItalic>attribute-keyword</legacyItalic> ::= DSN | UID | PWD           | <legacyItalic>driver-defined-attribute-keywordattribute-value</legacyItalic> ::= <legacyItalic>character-stringdriver-defined-attribute-keyword</legacyItalic> ::= <legacyItalic>identifier</legacyItalic></para>
      <para>where <legacyItalic>character-string</legacyItalic> has zero or more characters; <legacyItalic>identifier</legacyItalic> has one or more characters; <legacyItalic>attribute-keyword</legacyItalic> is not case-sensitive; <legacyItalic>attribute-value</legacyItalic> may be case-sensitive; and the value of the <legacyBold>DSN</legacyBold> keyword does not consist solely of blanks. Because of connection string and initialization file grammar, keywords and attribute values that contain the characters <legacyBold>[]{}(),;?*=!@</legacyBold> should be avoided. Because of the grammar in the system information, keywords and data source names cannot contain the backslash (\) character. For an ODBC 2.<legacyItalic>x</legacyItalic> driver, braces are required around the attribute value for the DRIVER keyword.</para>
      <para>If any keywords are repeated in the browse request connection string, the driver uses the value associated with the first occurrence of the keyword. If the <legacyBold>DSN</legacyBold> and <legacyBold>DRIVER</legacyBold> keywords are included in the same browse request connection string, the Driver Manager and driver use whichever keyword appears first.</para>
      <para>For information about how an application chooses a data source or driver, see <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>OutConnectionString Argument</title>
    <content>
      <para>The browse result connection string is a list of connection attributes. A connection attribute consists of an attribute keyword and a corresponding attribute value. The browse result connection string has the following syntax:</para>
      <para>
        <legacyItalic>connection-string</legacyItalic> ::= <legacyItalic>attribute</legacyItalic>[;] | <legacyItalic>attribute</legacyItalic>; <legacyItalic>connection-stringattribute</legacyItalic> ::= [*]<legacyItalic>attribute-keyword=attribute-valueattribute-keyword</legacyItalic> ::= <legacyItalic>ODBC-attribute-keyword</legacyItalic>           | <legacyItalic>driver-defined-attribute-keywordODBC-attribute-keyword</legacyItalic> = {UID | PWD}[:<legacyItalic>localized-identifier</legacyItalic>]<legacyItalic>driver-defined-attribute-keyword</legacyItalic> ::= <legacyItalic>identifier</legacyItalic>[:<legacyItalic>localized-identifier</legacyItalic>]<legacyItalic>attribute-value</legacyItalic> ::= {<legacyItalic>attribute-value-list</legacyItalic>} | ? (The braces are literal; they are returned by the driver.)<legacyItalic>attribute-value-list</legacyItalic> ::= <legacyItalic>character-string</legacyItalic> [:<legacyItalic>localized-character string</legacyItalic>] | <legacyItalic>character-string</legacyItalic> [:<legacyItalic>localized-character string</legacyItalic>], <legacyItalic>attribute-value-list</legacyItalic></para>
      <para>where <legacyItalic>character-string</legacyItalic> and <legacyItalic>localized-character string</legacyItalic> have zero or more characters; <legacyItalic>identifier</legacyItalic> and <legacyItalic>localized-identifier</legacyItalic> have one or more characters; <legacyItalic>attribute-keyword</legacyItalic> is not case-sensitive; and <legacyItalic>attribute-value</legacyItalic> may be case-sensitive. Because of connection string and initialization file grammar, keywords, localized identifiers, and attribute values that contain the characters <legacyBold>[]{}(),;?*=!@</legacyBold> should be avoided. Because of the grammar in the system information, keywords and data source names cannot contain the backslash (\) character.</para>
      <para>The browse result connection string syntax is used according to the following semantic rules:  </para>
      <list class="bullet">
        <listItem>
          <para>If an asterisk (*) precedes an <legacyItalic>attribute-keyword</legacyItalic>, the <legacyItalic>attribute</legacyItalic> is optional and can be omitted in the next call to <legacyBold>SQLBrowseConnect</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>The attribute keywords <legacyBold>UID</legacyBold> and <legacyBold>PWD</legacyBold> have the same meaning as defined in <legacyBold>SQLDriverConnect</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>A <legacyItalic>driver-defined-attribute-keyword</legacyItalic> names the kind of attribute for which an attribute value may be supplied. For example, it might be <legacyBold>SERVER</legacyBold>, <legacyBold>DATABASE</legacyBold>, <legacyBold>HOST</legacyBold>, or <legacyBold>DBMS</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyItalic>ODBC-attribute-keywords</legacyItalic> and <legacyItalic>driver-defined-attribute-keywords</legacyItalic> include a localized or user-friendly version of the keyword. This might be used by applications as a label in a dialog box. However, <legacyBold>UID</legacyBold>, <legacyBold>PWD</legacyBold>, or the <legacyItalic>identifier</legacyItalic> alone must be used when passing a browse request string to the driver.</para>
        </listItem>
        <listItem>
          <para>The {<legacyItalic>attribute-value-list</legacyItalic>} is an enumeration of actual values valid for the corresponding <legacyItalic>attribute-keyword</legacyItalic>. Note that the braces ({}) do not indicate a list of choices; they are returned by the driver. For example, it might be a list of server names or a list of database names.</para>
        </listItem>
        <listItem>
          <para>If the <legacyItalic>attribute-value</legacyItalic> is a single question mark (?), a single value corresponds to the <legacyItalic>attribute-keyword</legacyItalic>. For example, UID=JohnS; PWD=Sesame.</para>
        </listItem>
        <listItem>
          <para>Each call to <legacyBold>SQLBrowseConnect</legacyBold> returns only the information required to satisfy the next level of the connection process. The driver associates state information with the connection handle so that the context can always be determined on each call.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Using SQLBrowseConnect</title>
    <content>
      <para>
        <legacyBold>SQLBrowseConnect</legacyBold> requires an allocated connection. The Driver Manager loads the driver that was specified in or that corresponds to the data source name specified in the initial browse request connection string; for information about when this occurs, see the "Comments" section in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>. The driver may establish a connection with the data source during the browsing process. If <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_ERROR, outstanding connections are terminated and the connection is returned to an unconnected state.</para>
      <alert class="note">
        <para>  <legacyBold>SQLBrowseConnect</legacyBold> does not support connection pooling. If <legacyBold>SQLBrowseConnect</legacyBold> is called while connection pooling is enabled, SQLSTATE HY000 (General error) will be returned.</para>
      </alert>
      <para>When <legacyBold>SQLBrowseConnect</legacyBold> is called for the first time on a connection, the browse request connection string must contain the <legacyBold>DSN</legacyBold> keyword or the <legacyBold>DRIVER</legacyBold> keyword. If the browse request connection string contains the <legacyBold>DSN</legacyBold> keyword, the Driver Manager locates a corresponding data source specification in the system information:  </para>
      <list class="bullet">
        <listItem>
          <para>If the Driver Manager finds the corresponding data source specification, it loads the associated driver DLL; the driver can retrieve information about the data source from the system information.</para>
        </listItem>
        <listItem>
          <para>If the Driver Manager cannot find the corresponding data source specification, it locates the default data source specification and loads the associated driver DLL; the driver can retrieve information about the default data source from the system information. "DEFAULT" is passed to the driver for the DSN.</para>
        </listItem>
        <listItem>
          <para>If the Driver Manager cannot find the corresponding data source specification and there is no default data source specification, it returns SQL_ERROR with SQLSTATE IM002 (Data source not found and no default driver specified).</para>
        </listItem>
      </list>
      <para>If the browse request connection string contains the <legacyBold>DRIVER</legacyBold> keyword, the Driver Manager loads the specified driver; it does not attempt to locate a data source in the system information. Because the <legacyBold>DRIVER</legacyBold> keyword does not use information from the system information, the driver must define enough keywords so that a driver can connect to a data source using only the information in the browse request connection strings.</para>
      <para>On each call to <legacyBold>SQLBrowseConnect</legacyBold>, the application specifies the connection attribute values in the browse request connection string. The driver returns successive levels of attributes and attribute values in the browse result connection string; it returns SQL_NEED_DATA as long as there are connection attributes that have not yet been enumerated in the browse request connection string. The application uses the contents of the browse result connection string to build the browse request connection string for the next call to <legacyBold>SQLBrowseConnect</legacyBold>. All mandatory attributes (those not preceded by an asterisk in the <legacyItalic>OutConnectionString</legacyItalic> argument) must be included in the next call to <legacyBold>SQLBrowseConnect</legacyBold>. Note that the application cannot use the contents of previous browse result connection strings when building the current browse request connection string; that is, it cannot specify different values for attributes set in previous levels.</para>
      <para>When all levels of connection and their associated attributes have been enumerated, the driver returns SQL_SUCCESS, the connection to the data source is complete, and a complete connection string is returned to the application. The connection string is suitable to use, in conjunction with <legacyBold>SQLDriverConnect</legacyBold>, with the SQL_DRIVER_NOPROMPT option to establish another connection. The complete connection string cannot be used in another call to <legacyBold>SQLBrowseConnect</legacyBold>, however; if <legacyBold>SQLBrowseConnect</legacyBold> were called again, the entire sequence of calls would have to be repeated.</para>
      <para>
        <legacyBold>SQLBrowseConnect</legacyBold> also returns SQL_NEED_DATA if there are recoverable, nonfatal errors during the browse process; for example, an invalid password or attribute keyword supplied by the application. When SQL_NEED_DATA is returned and the browse result connection string is unchanged, an error has occurred and the application can call <legacyBold>SQLGetDiagRec</legacyBold> to return the SQLSTATE for browse-time errors. This permits the application to correct the attribute and continue the browse.</para>
      <para>An application can terminate the browse process at any time by calling <legacyBold>SQLDisconnect</legacyBold>. The driver will terminate any outstanding connections and return the connection to an unconnected state.</para>
      <para>If asynchronous operations are enabled on the connection handle, <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference> might also return SQL_STILL_EXECUTING. When it returns SQL_NEED_DATA, an application must use <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> to cancel the browse process. If <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference> returns SQL_STILL_EXECUTING, an application should use <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> to cancel the operation in progress. Calling <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> after the function returns SQL_NEED_DATA has no effect.</para>
      <para>For more information, see <legacyLink xlink:href="6c2e9f76-b766-48df-b109-246bb05ae45d">Connecting with SQLBrowseConnect</legacyLink>.</para>
      <para>If a driver supports <legacyBold>SQLBrowseConnect</legacyBold>, the driver keyword section in the system information for the driver must contain the <legacyBold>ConnectFunctions</legacyBold> keyword with the third character set to "Y."</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <codeInline>Trusted_Connection=yes</codeInline> instead of user ID and password information in the connection string.</para>
      </alert>
      <para>In the following example, an application calls <legacyBold>SQLBrowseConnect</legacyBold> repeatedly. Each time <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_NEED_DATA, it passes back information about the data it needs in *<legacyItalic>OutConnectionString</legacyItalic>. The application passes <legacyItalic>OutConnectionString</legacyItalic> to its routine <legacyBold>GetUserInput</legacyBold> (not shown). <legacyBold>GetUserInput</legacyBold> parses the information, builds and displays a dialog box, and returns the information entered by the user in *<legacyItalic>InConnectionString</legacyItalic>. The application passes the user's information to the driver in the next call to <legacyBold>SQLBrowseConnect</legacyBold>. After the application has provided all necessary information for the driver to connect to the data source, <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_SUCCESS and the application proceeds.</para>
      <para>For a more detailed example of connecting to a SQL Server driver by calling <legacyBold>SQLBrowseConnect</legacyBold>, see <legacyLink xlink:href="6e0d5fd1-ec93-4348-a77a-08f5ba738bc6">SQL Server Browsing Example</legacyLink>.</para>
      <para>For example, to connect to the data source Sales, the following actions might occur. First, the application passes the following string to <legacyBold>SQLBrowseConnect</legacyBold>:</para>
      <code>"DSN=Sales"</code>
      <para>The Driver Manager loads the driver associated with the data source Sales. It then calls the driver's <legacyBold>SQLBrowseConnect</legacyBold> function with the same arguments it received from the application. The driver returns the following string in *<legacyItalic>OutConnectionString</legacyItalic>:</para>
      <code>"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"</code>
      <para>The application passes this string to its <legacyBold>GetUserInput</legacyBold> routine, which builds a dialog box that asks the user to select the red, blue, or green server and to enter a user ID and password. The routine passes the following user-specified information back in *<legacyItalic>InConnectionString</legacyItalic>, which the application passes to <legacyBold>SQLBrowseConnect</legacyBold>:</para>
      <code>"HOST=red;UID=Smith;PWD=Sesame"</code>
      <para>
        <legacyBold>SQLBrowseConnect</legacyBold> uses this information to connect to the red server as Smith with the password Sesame, and then returns the following string in *<legacyItalic>OutConnectionString</legacyItalic>:</para>
      <code>"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"</code>
      <para>The application passes this string to its <legacyBold>GetUserInput</legacyBold> routine, which builds a dialog box that asks the user to select a database. The user selects empdata and the application calls <legacyBold>SQLBrowseConnect</legacyBold> a final time with this string:</para>
      <code>"DATABASE=SalesOrders"</code>
      <para>This is the final piece of information the driver needs to connect to the data source; <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_SUCCESS, and *<legacyItalic>OutConnectionString</legacyItalic> contains the completed connection string:</para>
      <code>// SQLBrowseConnect_Function.cpp
// compile with: odbc32.lib
#include &lt;windows.h&gt;
#include &lt;sqltypes.h&gt;
#include &lt;sqlext.h&gt;

#define BRWS_LEN 100
SQLHENV henv;
SQLHDBC hdbc;
SQLHSTMT hstmt;
SQLRETURN retcode;
SQLCHAR szConnStrIn[BRWS_LEN], szConnStrOut[BRWS_LEN];
SQLSMALLINT cbConnStrOut;

void GetUserInput(SQLCHAR * szConnStrOut, SQLCHAR * szConnStrIn) {}

int main() {
   // Allocate the environment handle.
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv);      
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {

      // Set the version environment attribute.
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {

         // Allocate the connection handle.
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &amp;hdbc);
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
            // Call SQLBrowseConnect until it returns a value other than SQL_NEED_DATA 
            // (pass data source name the first time).  If SQL_NEED_DATA is returned, call GetUserInput 
            // (not shown) to build a dialog from the values in szConnStrOut.  The user-supplied values 
            // are returned in szConnStrIn, which is passed in the next call to SQLBrowseConnect.

            strcpy_s((char*)szConnStrIn, _countof(szConnStrIn), "DSN=Sales");
            do {
               retcode = SQLBrowseConnect(hdbc, szConnStrIn, SQL_NTS,
                  szConnStrOut, BRWS_LEN, &amp;cbConnStrOut);
               if (retcode == SQL_NEED_DATA)
                  GetUserInput(szConnStrOut, szConnStrIn);
            } while (retcode == SQL_NEED_DATA);

            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){

               // Allocate the statement handle.
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &amp;hstmt);

               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)
                  // Process data after successful connection
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);
               SQLDisconnect(hdbc);
            }
         }
         SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
      }
   }
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
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
              <para>Allocating a connection handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink>
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
              <para>Freeing a connection handle</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</legacyLink>
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