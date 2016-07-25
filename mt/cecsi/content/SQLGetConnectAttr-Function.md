---
title: "SQLGetConnectAttr Function"
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
  - SQLGetConnectOption
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
caps.latest.revision: 31
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetConnectAttr Function
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
          <legacyBold>SQLGetConnectAttr</legacyBold> returns the current setting of a connection attribute.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3<legacyItalic>.x</legacyItalic> application is working with an ODBC 2<legacyItalic>.x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetConnectAttr</legacyBold>(
     SQLHDBC        <parameterReference>ConnectionHandle</parameterReference>,
     SQLINTEGER     <parameterReference>Attribute</parameterReference>,
     SQLPOINTER     <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER     <parameterReference>BufferLength</parameterReference>,
     SQLINTEGER *   <parameterReference>StringLengthPtr</parameterReference>);</legacySyntax>
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
          <para>[Input] Attribute to retrieve. </para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to memory in which to return the current value of the attribute specified by <legacyItalic>Attribute</legacyItalic>. For integer-type attributes, some drivers may only write the lower 32-bit or 16-bit of a buffer and leave the higher-order bit unchanged. Therefore, applications should use a buffer of SQLULEN and initialize the value to 0 before calling this function.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ValuePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and<legacyItalic> ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and *<legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored. If the value in <legacyItalic>*ValuePtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLGetConnectAttrW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is a driver-defined attribute, the application indicates the nature of the attribute to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values:   </para>
          <list class="bullet">
            <listItem>
              <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a character string, <legacyItalic>BufferLength</legacyItalic> is the length of the string.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a binary buffer, the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a value other than a character string or binary string, <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
            </listItem>
            <listItem>
              <para>If <legacyItalic>*ValuePtr</legacyItalic> contains a fixed-length data type, <legacyItalic>BufferLength</legacyItalic> is either SQL_IS_INTEGER or SQL_IS_UINTEGER, as appropriate.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the total number of bytes (excluding the null-termination character) available to return in *<legacyItalic>ValuePtr</legacyItalic>. If *<legacyItalic>ValuePtr</legacyItalic> is a null pointer, no length is returned. If the attribute value is a character string and the number of bytes available to return is greater than <legacyItalic>BufferLength</legacyItalic> minus the length of the null-termination character, the data in <legacyItalic>*ValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of the null-termination character and is null-terminated by the driver.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLGetConnectAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained from the diagnostic data structure by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>ConnectionHandle</legacyItalic>. The following table lists the SQLSTATE values typically returned by <legacyBold>SQLGetConnectAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The data returned in *<legacyItalic>ValuePtr</legacyItalic> was truncated to be <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character. The length of the untruncated string value is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>(DM) An <legacyItalic>Attribute</legacyItalic> value that required an open connection was specified.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned from the diagnostic data structure by the argument <legacyItalic>MessageText</legacyItalic> in <legacyBold>SQLGetDiagField</legacyBold> describes the error and its cause.</para>
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
              <para>(DM) <legacyBold>SQLBrowseConnect</legacyBold> was called for the <legacyItalic>ConnectionHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before <legacyBold>SQLBrowseConnect</legacyBold> returned SQL_SUCCESS_WITH_INFO or SQL_SUCCESS.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or<unmanagedCodeEntityReference> SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>ConnectionHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
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
              <para>(DM)<legacyItalic> *ValuePtr</legacyItalic> is a character string, and BufferLength was less than zero but not equal to SQL_NTS.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was not valid for the version of ODBC supported by the driver.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC connection attribute for the version of ODBC supported by the driver, but was not supported by the driver.</para>
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
      <para>For general information about connection attributes, see <legacyLink xlink:href="e6d03089-30a3-4627-a642-591ba0980894">Connection Attributes</legacyLink>.</para>
      <para>For a list of attributes that can be set, see <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>. Notice that if <legacyItalic>Attribute</legacyItalic> specifies an attribute that returns a string, <legacyItalic>ValuePtr</legacyItalic> must be a pointer to a buffer for the string. The maximum length of the returned string, including the null-termination character, will be <legacyItalic>BufferLength</legacyItalic> bytes.</para>
      <para>Depending on the attribute, an application does not have to establish a connection before calling <legacyBold>SQLGetConnectAttr</legacyBold>. However, if <legacyBold>SQLGetConnectAttr</legacyBold> is called and the specified attribute does not have a default and has not been set by a prior call to <legacyBold>SQLSetConnectAttr</legacyBold>, <legacyBold>SQLGetConnectAttr</legacyBold> will return SQL_NO_DATA. </para>
      <para>If <legacyItalic>Attribute</legacyItalic> is SQL_ATTR_ TRACE or SQL_ATTR_ TRACEFILE, <legacyItalic>ConnectionHandle</legacyItalic> does not have to be valid, and <legacyBold>SQLGetConnectAttr</legacyBold> will not return SQL_ERROR or SQL_INVALID_HANDLE if <legacyItalic>ConnectionHandle</legacyItalic> is invalid. These attributes apply to all connections. <legacyBold>SQLGetConnectAttr</legacyBold> will return SQL_ERROR or SQL_INVALID_HANDLE if another argument is invalid.</para>
      <para>Although an application can set statement attributes by using <legacyBold>SQLSetConnectAttr</legacyBold>, an application cannot use <legacyBold>SQLGetConnectAttr</legacyBold> to retrieve statement attribute values; it must call <legacyBold>SQLGetStmtAttr</legacyBold> to retrieve the setting of statement attributes.</para>
      <para>Both SQL_ATTR_AUTO_IPD and SQL_ATTR_CONNECTION_DEAD connection attributes can be returned by a call to <legacyBold>SQLGetConnectAttr</legacyBold> but cannot be set by a call to <legacyBold>SQLSetConnectAttr</legacyBold>.</para>
      <alert class="note">
        <para>There is no asynchronous support for <unmanagedCodeEntityReference>SQLGetConnectAttr</unmanagedCodeEntityReference>. When implementing <unmanagedCodeEntityReference>SQLGetConnectAttr</unmanagedCodeEntityReference>, a driver can improve performance by minimizing the number of times that information is sent or requested from the server.</para>
      </alert>
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
              <para>Returning the setting of a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>
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
          <tr>
            <TD>
              <para>Setting an environment attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>
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