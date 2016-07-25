---
title: "SQLSetConnectAttr Function"
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
  - SQLSetConnectAttr
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
caps.latest.revision: 82
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectAttr Function
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
          <legacyBold>SQLSetConnectAttr</legacyBold> sets attributes that govern aspects of connections.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3<legacyItalic>.x</legacyItalic> application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLSetConnectAttr</legacyBold>(
     SQLHDBC       <parameterReference>ConnectionHandle</parameterReference>,
     SQLINTEGER    <parameterReference>Attribute</parameterReference>,
     SQLPOINTER    <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER    <parameterReference>StringLength</parameterReference>);</legacySyntax>
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
          <legacyItalic>Attribute</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Attribute to set, listed in "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the value to be associated with <legacyItalic>Attribute</legacyItalic>. Depending on the value of <legacyItalic>Attribute</legacyItalic>, <legacyItalic>ValuePtr</legacyItalic> will be an unsigned integer value or will point to a null-terminated character string. Note that the integral type of the <legacyItalic>Attribute</legacyItalic> argument may not be fixed length, see the Comments section for detail.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. For character string data, this argument should contain the number of bytes in the string.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>StringLength</legacyItalic> is ignored.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is a driver-defined attribute, the application indicates the nature of the attribute to the Driver Manager by setting the <legacyItalic>StringLength</legacyItalic> argument. <legacyItalic>StringLength</legacyItalic> can have the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a character string, then <legacyItalic>StringLength</legacyItalic> is the length of the string or SQL_NTS.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a binary buffer, then the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>StringLength</legacyItalic>. This places a negative value in <legacyItalic>StringLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is a pointer to a value other than a character string or a binary string, then <legacyItalic>StringLength</legacyItalic> should have the value SQL_IS_POINTER.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>ValuePtr</legacyItalic> contains a fixed-length value, then <legacyItalic>StringLength</legacyItalic> is either SQL_IS_INTEGER or SQL_IS_UINTEGER, as appropriate.</para>
            </listItem>
          </list>
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
      <para>When <legacyBold>SQLSetConnectAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLSetConnectAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
      <para>The driver can return SQL_SUCCESS_WITH_INFO to provide information about the result of setting an option.</para>
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
              <para>The driver did not support the value specified in <legacyItalic>ValuePtr</legacyItalic> and substituted a similar value. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ODBC_CURSORS, and the driver was already connected to the data source.</para>
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
              <para>(DM) An <legacyItalic>Attribute</legacyItalic> value was specified that required an open connection, but the <legacyItalic>ConnectionHandle</legacyItalic> was not in a connected state.</para>
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
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_CURRENT_CATALOG, and a result set was pending.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>25000</para>
            </TD>
            <TD>
              <para>Illegal operation while in a local transaction</para>
            </TD>
            <TD>
              <para>A connection was in a local transaction while attempting to enlist in a distributed transaction connection (DTC) by setting the connection attribute SQL_ATTR_ENLIST_IN_DTC.</para>
              <para>A connection is already enlisted in a DTC.</para>
              <para>A connection has been enlisted in a distributed transaction connection and a local transaction was started by setting SQL_ATTR_AUTOCOMMIT to SQL_AUTOCOMMIT_OFF.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3D000</para>
            </TD>
            <TD>
              <para>Invalid catalog name</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_CURRENT_CATALOG, and the specified catalog name was invalid.</para>
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
              <para>Asynchronous processing was enabled for the <parameterReference>ConnectionHandle</parameterReference>. The <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> function was called, and before it completed execution, the <legacyLink xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle function</legacyLink> was called on the <parameterReference>ConnectionHandle</parameterReference>, and then the <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference> function was called again on the <parameterReference>ConnectionHandle</parameterReference>.</para>
              <para>Or, the <unmanagedCodeEntityReference> SQLSetConnectAttr</unmanagedCodeEntityReference> function was called, and before it completed execution, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> was called on the <parameterReference>ConnectionHandle</parameterReference> from a different thread in a multithread application.</para>
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
              <para>The <legacyItalic>Attribute</legacyItalic> argument identified a connection attribute that required a string value, and the <legacyItalic>ValuePtr </legacyItalic>argument was a null pointer.</para>
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
              <para> (DM) An asynchronously executing function was called for a <legacyItalic>StatementHandle</legacyItalic> associated with the <legacyItalic>ConnectionHandle</legacyItalic> and was still executing when <legacyBold>SQLSetConnectAttr</legacyBold> was called.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <parameterReference>ConnectionHandle</parameterReference> and was still executing when this function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>,<unmanagedCodeEntityReference> SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for one of the statement handles associated with the <parameterReference>ConnectionHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for a <legacyItalic>StatementHandle</legacyItalic> associated with the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
              <para>(DM) <legacyBold>SQLBrowseConnect</legacyBold> was called for the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before <legacyBold>SQLBrowseConnect</legacyBold> returned SQL_SUCCESS_WITH_INFO or SQL_SUCCESS.</para>
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
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_TXN_ISOLATION, and a transaction was open.</para>
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
              <para>Given the specified <legacyItalic>Attribute</legacyItalic> value, an invalid value was specified in <legacyItalic>ValuePtr</legacyItalic>. (The Driver Manager returns this SQLSTATE only for connection and statement attributes that accept a discrete set of values, such as SQL_ATTR_ACCESS_MODE or SQL_ATTR_ASYNC_ENABLE. For all other connection and statement attributes, the driver must verify the value specified in <legacyItalic>ValuePtr</legacyItalic>.)</para>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_TRACEFILE or SQL_ATTR_TRANSLATE_LIB, and <legacyItalic>ValuePtr</legacyItalic> was an empty string.</para>
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
              <para> <legacyItalic>(DM) *ValuePtr </legacyItalic>is a character string, and the <legacyItalic>StringLength</legacyItalic> argument was less than 0 but was not SQL_NTS.</para>
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
              <para>HY114</para>
            </TD>
            <TD>
              <para>Driver does not support connection-level asynchronous function execution</para>
            </TD>
            <TD>
              <para>(DM) An application attempted to enable asynchronous function execution with SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE for a driver that does not support asynchronous connection operations.</para>
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
              <para>(DM) For more information about the suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY121</para>
            </TD>
            <TD>
              <para>Cursor Library and Driver-Aware Pooling cannot be enabled at the same time</para>
            </TD>
            <TD>
              <para>For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC connection or statement attribute for the version of ODBC supported by the driver but was not supported by the driver.</para>
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
              <para>(DM) The driver associated with the <legacyItalic>ConnectionHandle</legacyItalic> does not support the function.</para>
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
              <para>The driver was unable to load the translation DLL that was specified for the connection. This error can be returned only when <legacyItalic>Attribute</legacyItalic> is SQL_ATTR_TRANSLATE_LIB.</para>
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
              <para />
              <para> SQL_ATTR_ASYNC_DBC_EVENT was set (after the connection was made) but asynchronous notification is not supported by the driver.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>When <legacyItalic>Attribute</legacyItalic> is a statement attribute, <legacyBold>SQLSetConnectAttr</legacyBold> can return any SQLSTATEs returned by <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>For general information about connection attributes, see <legacyLink xlink:href="e6d03089-30a3-4627-a642-591ba0980894">Connection Attributes</legacyLink>.</para>
      <para>The currently defined attributes and the version of ODBC in which they were introduced are shown in the table later in this section; it is expected that more attributes will be defined to take advantage of different data sources. A range of attributes is reserved by ODBC; driver developers must reserve values for their own driver-specific use from Open Group.</para>
      <alert class="note">
        <para>The ability to set statement attributes at the connection level by calling <legacyBold>SQLSetConnectAttr</legacyBold> has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3<legacyItalic>.x</legacyItalic> applications should never set statement attributes at the connection level. ODBC 3<legacyItalic>.x</legacyItalic> statement attributes cannot be set at the connection level, with the exception of the SQL_ATTR_METADATA_ID and SQL_ATTR_ASYNC_ENABLE attributes, which are both connection attributes and statement attributes and can be set at either the connection level or the statement level. </para>
        <para>ODBC 3<legacyItalic>.x</legacyItalic> drivers need only support this functionality if they should work with ODBC 2<legacyItalic>.x</legacyItalic> applications that set ODBC 2<legacyItalic>.x</legacyItalic> statement options at the connection level. For more information, see <legacyLink xlink:href="a1b325cf-0c42-41c1-b141-b5a4fee7e708">SQLSetConnectOption Mapping</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
      </alert>
      <para>An application can call <legacyBold>SQLSetConnectAttr</legacyBold> at any time between the time the connection is allocated and freed. All connection and statement attributes successfully set by the application for the connection persist until <legacyBold>SQLFreeHandle</legacyBold> is called on the connection. For example, if an application calls <legacyBold>SQLSetConnectAttr</legacyBold> before connecting to a data source, the attribute persists even if <legacyBold>SQLSetConnectAttr</legacyBold> fails in the driver when the application connects to the data source; if an application sets a driver-specific attribute, the attribute persists even if the application connects to a different driver on the connection.</para>
      <para>Some connection attributes can be set only before a connection has been made; others can be set only after a connection has been made. The following table indicates those connection attributes that must be set either before or after a connection has been made. <legacyItalic>Either</legacyItalic> indicates that the attribute can be set either before or after connection.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Attribute</para>
            </TD>
            <TD>
              <para>Set before or after connection?</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_ACCESS_MODE</para>
            </TD>
            <TD>
              <para>Either[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_EVENT</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE</para>
            </TD>
            <TD>
              <para>Either[4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_PCALLBACK</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_PCONTEXT</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_ENABLE</para>
            </TD>
            <TD>
              <para>Either[2]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_AUTO_IPD</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_AUTOCOMMIT</para>
            </TD>
            <TD>
              <para>Either[5]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CONNECTION_DEAD</para>
            </TD>
            <TD>
              <para>After</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CONNECTION_TIMEOUT</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURRENT_CATALOG</para>
            </TD>
            <TD>
              <para>Either[1]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_DBC_INFO_TOKEN</para>
            </TD>
            <TD>
              <para>After</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ENLIST_IN_DTC</para>
            </TD>
            <TD>
              <para>After</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_LOGIN_TIMEOUT</para>
            </TD>
            <TD>
              <para>Before</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_METADATA_ID</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ODBC_CURSORS</para>
            </TD>
            <TD>
              <para>Before</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PACKET_SIZE</para>
            </TD>
            <TD>
              <para>Before</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_QUIET_MODE</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRACE</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRACEFILE</para>
            </TD>
            <TD>
              <para>Either</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRANSLATE_LIB</para>
            </TD>
            <TD>
              <para>After</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRANSLATE_OPTION</para>
            </TD>
            <TD>
              <para>After</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TXN_ISOLATION</para>
            </TD>
            <TD>
              <para>Either[3]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   SQL_ATTR_ACCESS_MODE and SQL_ATTR_CURRENT_CATALOG can be set before or after connecting, depending on the driver. However, interoperable applications set them before connecting because some drivers do not support changing these after connecting.</para>
      <para>[2]   SQL_ATTR_ASYNC_ENABLE must be set before there is an active statement.</para>
      <para>[3]   SQL_ATTR_TXN_ISOLATION can be set only if there are no open transactions on the connection. Some connection attributes support substitution of a similar value if the data source does not support the value specified in *<legacyItalic>ValuePtr</legacyItalic>. In such cases, the driver returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value changed). For example, if <legacyItalic>Attribute</legacyItalic> is SQL_ATTR_PACKET_SIZE and *<legacyItalic>ValuePtr</legacyItalic> exceeds the maximum packet size, the driver substitutes the maximum size. To determine the substituted value, an application calls <legacyBold>SQLGetConnectAttr</legacyBold>.</para>
      <para>[4]    If SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is set before a connection is open, the Driver Manager will set the driver’s attribute when the driver is loaded during a call to <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference>. Before a call to <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference>, the Driver Manager does not know which driver to connect to and does not know whether the driver supports asynchronous connection operations. Therefore, the Driver Manager always returns SQL_SUCCESS. But, in case the driver does not support asynchronous connection operations, the call to <unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLConnect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLDriverConnect</unmanagedCodeEntityReference> will fail.</para>
      <para>[5]    When SQL_ATTR_AUTOCOMMIT is set to FALSE, applications should call SQLEndTran(SQL_ROLLBACK) if any API returns SQL_ERROR to ensure transactional consistency.</para>
      <para>The format of information set in the *<legacyItalic>ValuePtr</legacyItalic> buffer depends on the specified <legacyItalic>Attribute</legacyItalic>. <legacyBold>SQLSetConnectAttr</legacyBold> will accept attribute information in one of two different formats: a null-terminated character string or an integer value. The format of each is noted in the attribute's description. Character strings pointed to by the <legacyItalic>ValuePtr</legacyItalic> argument of <legacyBold>SQLSetConnectAttr</legacyBold> have a length of <legacyItalic>StringLength</legacyItalic> bytes.</para>
      <para>The <legacyItalic>StringLength</legacyItalic> argument is ignored if the length is defined by the attribute, as is the case for all attributes introduced in ODBC 2<legacyItalic>.x</legacyItalic> or earlier.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>Attribute</legacyItalic> </para>
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
              <para>SQL_ATTR_ACCESS_MODE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value. SQL_MODE_READ_ONLY is used by the driver or data source as an indicator that the connection is not required to support SQL statements that cause updates to occur. This mode can be used to optimize locking strategies, transaction management, or other areas as appropriate to the driver or data source. The driver is not required to prevent such statements from being submitted to the data source. The behavior of the driver and data source when asked to process SQL statements that are not read-only during a read-only connection is implementation-defined. SQL_MODE_READ_WRITE is the default.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value that is an event handle.</para>
              <para>Notification of the completion of asynchronous functions is enabled by calling <languageKeyword>SQLSetConnectAttr</languageKeyword> with the SQL_ATTR_ASYNC_STMT_EVENT attribute and specifying the event handle.</para>
              <alert class="note">
                <para>The notification method is not supported with cursor library. An application will receive error message if it attempts to enable cursor library via SQLSetConnectAttr, when the notification method is enabled.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLUINTEGER value that enables or disables asynchronous execution of selected functions on the connection handle. For more information, see <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>.</para>
              <para>SQL_ASYNC_DBC_ENABLE_ON = Enable asynchronous operation for specified connection-related functions.</para>
              <para>SQL_ASYNC_DBC_ENABLE_OFF = (Default) Disable asynchronous operation for specified connection-related functions. </para>
              <para>Setting SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is always synchronous (that is, it will never return SQL_STILL_EXECUTING).</para>
              <para>Asynchronous execution of statement operations are enabled with SQL_ATTR_ASYNC_ENABLE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value that points to context structure.</para>
              <para>Only the Driver Manager can call a driver’s <languageKeyword>SQLSetStmtAttr</languageKeyword> function with this attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value that points to the context structure.</para>
              <para>Only the Driver Manager can call a driver’s <languageKeyword>SQLSetStmtAttr</languageKeyword> function with this attribute.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A SQLULEN value that specifies whether a function called with a statement on the specified connection is executed asynchronously:</para>
              <para>SQL_ASYNC_ENABLE_OFF = Disable connection level asynchronous execution support for statement operations (the default).</para>
              <para> SQL_ASYNC_ENABLE_ON = Enable connection level asynchronous execution support for statement operations.</para>
              <para>This attribute can be set whether <legacyBold>SQLGetInfo</legacyBold> with the SQL_ASYNC_MODE information type returns SQL_AM_CONNECTION or SQL_AM_STATEMENT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_AUTO_IPD (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A read-only SQLUINTEGER value that specifies whether automatic population of the IPD after a call to <legacyBold>SQLPrepare </legacyBold>is supported:</para>
              <para>SQL_TRUE = Automatic population of the IPD after a call to <legacyBold>SQLPrepare </legacyBold>is supported by the driver.</para>
              <para>SQL_FALSE = Automatic population of the IPD after a call to <legacyBold>SQLPrepare </legacyBold>is not supported by the driver. Servers that do not support prepared statements will not be able to populate the IPD automatically. </para>
              <para>If SQL_TRUE is returned for the SQL_ATTR_AUTO_IPD connection attribute, the statement attribute SQL_ATTR_ENABLE_AUTO_IPD can be set to turn automatic population of the IPD on or off. If SQL_ATTR_AUTO_IPD is SQL_FALSE, SQL_ATTR_ENABLE_AUTO_IPD cannot be set to SQL_TRUE. The default value of SQL_ATTR_ENABLE_AUTO_IPD is equal to the value of SQL_ATTR_AUTO_IPD.</para>
              <para>This connection attribute can be returned by <legacyBold>SQLGetConnectAttr</legacyBold> but cannot be set by <legacyBold>SQLSetConnectAttr</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_AUTOCOMMIT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A SQLUINTEGER value that specifies whether to use autocommit or manual-commit mode:</para>
              <para>SQL_AUTOCOMMIT_OFF = The driver uses manual-commit mode, and the application must explicitly commit or roll back transactions with <legacyBold>SQLEndTran</legacyBold>.</para>
              <para>SQL_AUTOCOMMIT_ON = The driver uses autocommit mode. Each statement is committed immediately after it is executed. This is the default. Any open transactions on the connection are committed when SQL_ATTR_AUTOCOMMIT is set to SQL_AUTOCOMMIT_ON to change from manual-commit mode to autocommit mode.</para>
              <para>For more information, see <legacyLink xlink:href="963fe470-f7cb-4dbe-a779-05f98d7ff17d">Commit Mode</legacyLink>.</para>
              <alert class="important">
                <para>Some data sources delete the access plans and close the cursors for all statements on a connection each time a statement is committed; autocommit mode can cause this to happen after each nonquery statement is executed or when the cursor is closed for a query. For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR information types in <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> and <legacyLink xlink:href="523e22a2-7b53-4c25-97c1-ef0284aec76e">Effect of Transactions on Cursors and Prepared Statements</legacyLink>.</para>
              </alert>
              <para>When a batch is executed in autocommit mode, two things are possible. The entire batch can be treated as an autocommitable unit, or each statement in a batch is treated as an autocommitable unit. Certain data sources can support both these behaviors and may provide a way of choosing one or the other. It is driver-defined whether a batch is treated as an autocommitable unit or whether each individual statement within the batch is autocommitable.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CONNECTION_DEAD</para>
              <para>(ODBC 3.5)</para>
            </TD>
            <TD>
              <para>A read-only SQLUINTEGER value that indicates the state of the connection. If SQL_CD_TRUE, the connection has been lost. If SQL_CD_FALSE, the connection is still active.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value corresponding to the number of seconds to wait for any request on the connection to complete before returning to the application. The driver should return SQLSTATE HYT00 (Timeout expired) anytime that it is possible to time out in a situation not associated with query execution or login.</para>
              <para>If <legacyItalic>ValuePtr</legacyItalic> is equal to 0 (the default), there is no timeout.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>A character string containing the name of the catalog to be used by the data source. For example, in SQL Server, the catalog is a database, so the driver sends a <legacyBold>USE</legacyBold> <legacyItalic>database</legacyItalic> statement to the data source, where <legacyItalic>database</legacyItalic> is the database specified in *<legacyItalic>ValuePtr</legacyItalic>. For a single-tier driver, the catalog might be a directory, so the driver changes its current directory to the directory specified in *<legacyItalic>ValuePtr</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value used to set back the connection info token into the DBC handle when <legacyLink xlink:href="e8da2ffb-d6ef-4ca7-824f-57afd29585d8">SQLRateConnection</legacyLink>'s (*<parameterReference>pRating</parameterReference>) parameter is not equal to 100.</para>
              <para>SQL_ATTR_DBC_INFO_TOKEN is set-only. It is not possible to use <legacyBold>SQLGetConnectAttr</legacyBold> or <legacyBold>SQLGetConnectOption</legacyBold> to retrieve this value. The Driver Manager’s <legacyBold>SQLSetConnectAttr</legacyBold> will not accept SQL_ATTR_DBC_INFO_TOKEN, since an application should not set this attribute.</para>
              <para>If a driver returns SQL_ERROR after setting SQL_ATTR_DBC_INFO_TOKEN, the connection just obtained from the pool will be freed. The Driver Manager will then try to obtain another connection from the pool. See <link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link> for more information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>A SQLPOINTER value that specifies whether to use the ODBC driver in distributed transactions coordinated by Microsoft Component Services.</para>
              <para>Pass a DTC OLE transaction object that specifies the transaction to export to SQL Server, or SQL_DTC_DONE to end the connection's DTC association.</para>
              <para>The client calls the Microsoft Distributed Transaction Coordinator (MS DTC) OLE ITransactionDispenser::BeginTransaction method to begin an MS DTC transaction and create an MS DTC transaction object that represents the transaction. The application then calls SQLSetConnectAttr with the SQL_ATTR_ENLIST_IN_DTC option to associate the transaction object with the ODBC connection. All related database activity will be performed under the protection of the MS DTC transaction. The application calls SQLSetConnectAttr with SQL_DTC_DONE to end the connection's DTC association. For more information, see the MS DTC documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value corresponding to the number of seconds to wait for a login request to complete before returning to the application. The default is driver-dependent. If <legacyItalic>ValuePtr</legacyItalic> is 0, the timeout is disabled and a connection attempt will wait indefinitely.</para>
              <para>If the specified timeout exceeds the maximum login timeout in the data source, the driver substitutes that value and returns SQLSTATE 01S02 (Option value changed).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_METADATA_ID (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value that determines how the string arguments of catalog functions are treated.</para>
              <para>If SQL_TRUE, the string argument of catalog functions are treated as identifiers. The case is not significant. For nondelimited strings, the driver removes any trailing spaces and the string is folded to uppercase. For delimited strings, the driver removes any leading or trailing spaces and takes literally whatever is between the delimiters. If one of these arguments is set to a null pointer, the function returns SQL_ERROR and SQLSTATE HY009 (Invalid use of null pointer). </para>
              <para>If SQL_FALSE, the string arguments of catalog functions are not treated as identifiers. The case is significant. They can either contain a string search pattern or not, depending on the argument.</para>
              <para>The default value is SQL_FALSE.</para>
              <para>The <legacyItalic>TableType</legacyItalic> argument of <legacyBold>SQLTables</legacyBold>, which takes a list of values, is not affected by this attribute.</para>
              <para>SQL_ATTR_METADATA_ID can also be set on the statement level. (It is the only connection attribute that is also a statement attribute.)</para>
              <para>For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_ODBC_CURSORS (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLULEN  value specifying how the Driver Manager uses the ODBC cursor library:</para>
              <para>SQL_CUR_USE_IF_NEEDED = The Driver Manager uses the ODBC cursor library only if it is needed. If the driver supports the SQL_FETCH_PRIOR option in <legacyBold>SQLFetchScroll</legacyBold>, the Driver Manager uses the scrolling capabilities of the driver. Otherwise, it uses the ODBC cursor library.</para>
              <para>SQL_CUR_USE_ODBC = The Driver Manager uses the ODBC cursor library.</para>
              <para>SQL_CUR_USE_DRIVER = The Driver Manager uses the scrolling capabilities of the driver. This is the default setting.</para>
              <para>For more information about the ODBC cursor library, see <legacyLink xlink:href="a03084df-4e48-48ef-917d-4a3fae48a605">Appendix F: ODBC Cursor Library</legacyLink>.</para>
              <alert class="warning">
                <para>The cursor library will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PACKET_SIZE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value specifying the network packet size in bytes.</para>
              <alert class="note">
                <para>Many data sources either do not support this option or only can return but not set the network packet size.</para>
              </alert>
              <para>If the specified size exceeds the maximum packet size or is smaller than the minimum packet size, the driver substitutes that value and returns SQLSTATE 01S02 (Option value changed).</para>
              <para>If the application sets packet size after a connection has already been made, the driver will return SQLSTATE HY011 (Attribute cannot be set now).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_QUIET_MODE (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>A window handle (HWND).</para>
              <para>If the window handle is a null pointer, the driver does not display any dialog boxes.</para>
              <para>If the window handle is not a null pointer, it should be the parent window handle of the application. This is the default. The driver uses this handle to display dialog boxes.</para>
              <alert class="note">
                <para>The SQL_ATTR_QUIET_MODE connection attribute does not apply to dialog boxes displayed by <legacyBold>SQLDriverConnect</legacyBold>.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRACE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>An SQLUINTEGER value telling the Driver Manager whether to perform tracing:</para>
              <para>SQL_OPT_TRACE_OFF = Tracing off (the default)</para>
              <para>SQL_OPT_TRACE_ON = Tracing on</para>
              <para>When tracing is on, the Driver Manager writes each ODBC function call to the trace file.</para>
              <alert class="note">
                <para>When tracing is on, the Driver Manager can return SQLSTATE IM013 (Trace file error) from any function.</para>
              </alert>
              <para>An application specifies a trace file with the SQL_ATTR_TRACEFILE option. If the file already exists, the Driver Manager appends to the file. Otherwise, it creates the file. If tracing is on and no trace file has been specified, the Driver Manager writes to the file SQL.LOG in the root directory. </para>
              <para>An application can set the variable <legacyBold>ODBCSharedTraceFlag</legacyBold> to enable tracing dynamically. Tracing is then enabled for all ODBC applications currently running. If an application turns tracing off, it is turned off only for that application.</para>
              <para>If the <legacyBold>Trace</legacyBold> keyword in the system information is set to 1 when an application calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV, tracing is enabled for all handles. It is enabled only for the application that called <legacyBold>SQLAllocHandle</legacyBold>.</para>
              <para>Calling <legacyBold>SQLSetConnectAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_TRACE does not require that the <legacyItalic>ConnectionHandle</legacyItalic> argument be valid and will not return SQL_ERROR if <legacyItalic>ConnectionHandle</legacyItalic> is NULL. This attribute applies to all connections.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRACEFILE (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A null-terminated character string containing the name of the trace file.</para>
              <para>The default value of the SQL_ATTR_TRACEFILE attribute is specified with the <legacyBold>TraceFile</legacyBold> keyword in the system information. For more information, see <legacyLink xlink:href="f9534144-8f42-4946-b0fb-638e9dcde9c8">ODBC Subkey</legacyLink>.</para>
              <para>Calling <legacyBold>SQLSetConnectAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_ TRACEFILE does not require the <legacyItalic>ConnectionHandle</legacyItalic> argument to be valid and will not return SQL_ERROR if <legacyItalic>ConnectionHandle</legacyItalic> is invalid. This attribute applies to all connections.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A null-terminated character string containing the name of a library containing the functions <legacyBold>SQLDriverToDataSource</legacyBold> and <legacyBold>SQLDataSourceToDriver</legacyBold> that the driver accesses to perform tasks such as character set translation. This option may be specified only if the driver has connected to the data source. The setting of this attribute will persist across connections. For more information about translating data, see <legacyLink xlink:href="38975059-b346-410f-bb27-326f3f7bbf39">Translation DLLs</legacyLink> and <legacyLink xlink:href="69033376-c315-4f52-8ee5-f23f07694bf8">Translation DLL Function Reference</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A 32-bit flag value that is passed to the translation DLL. This attribute can be specified only if the driver has connected to the data source. For information about translating data, see <legacyLink xlink:href="38975059-b346-410f-bb27-326f3f7bbf39">Translation DLLs</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_TXN_ISOLATION (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>A 32-bit bitmask that sets the transaction isolation level for the current connection. An application must call <legacyBold>SQLEndTran</legacyBold> to commit or roll back all open transactions on a connection, before calling <legacyBold>SQLSetConnectAttr</legacyBold> with this option.</para>
              <para>The valid values for <legacyItalic>ValuePtr</legacyItalic> can be determined by calling <legacyBold>SQLGetInfo</legacyBold> with <legacyItalic>InfoType</legacyItalic> equal to SQL_TXN_ISOLATION_OPTIONS.</para>
              <para>For a description of transaction isolation levels, see the description of the SQL_DEFAULT_TXN_ISOLATION information type in <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> and <legacyLink xlink:href="0d638d55-ffd0-48fb-834b-406f466214d4">Transaction Isolation Levels</legacyLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   These functions can be called asynchronously only if the descriptor is an implementation descriptor, not an application descriptor.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>.</para>
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
              <para>Returning the setting of a connection  attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</legacyLink> </para>
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