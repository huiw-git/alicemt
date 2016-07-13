---
title: SQLGetStmtAttr Function
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
  - SQLGetStmtAttr
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetStmtAttr Function
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
          <legacyBold>SQLGetStmtAttr</legacyBold> returns the current setting of a statement attribute.</para>
        <alert class="note">
          <para>For more information about what the Driver Manager maps this function to when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, see <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>.</para>
        </alert>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetStmtAttr</legacyBold>(
     SQLHSTMT        <parameterReference>StatementHandle</parameterReference>,
     SQLINTEGER      <parameterReference>Attribute</parameterReference>,
     SQLPOINTER      <parameterReference>ValuePtr</parameterReference>,
     SQLINTEGER      <parameterReference>BufferLength</parameterReference>,
     SQLINTEGER *    <parameterReference>StringLengthPtr</parameterReference>);</legacySyntax>
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
          <legacyItalic>Attribute</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Attribute to retrieve. </para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the value of the attribute specified in <legacyItalic>Attribute</legacyItalic>.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ValuePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and<legacyItalic> ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and *<legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored. If the value returned in <legacyItalic>*ValuePtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLGetStmtAttrW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is a driver-defined attribute, the application indicates the nature of the attribute to the Driver Manager by setting the <legacyItalic>BufferLength</legacyItalic> argument. <legacyItalic>BufferLength</legacyItalic> can have the following values: </para>
        </definition>
      </definitionTable>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a character string, then <legacyItalic>BufferLength</legacyItalic> is the length of the string or SQL_NTS.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a binary buffer, then the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in <legacyItalic>BufferLength</legacyItalic>. This places a negative value in <legacyItalic>BufferLength</legacyItalic>.</para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is a pointer to a value other than a character string or binary string, then <legacyItalic>BufferLength</legacyItalic> should have the value SQL_IS_POINTER. </para>
        </listItem>
        <listItem>
          <para>If <legacyItalic>*ValuePtr</legacyItalic> is contains a fixed-length data type, then <legacyItalic>BufferLength</legacyItalic> is either SQL_IS_INTEGER or SQL_IS_UINTEGER, as appropriate.</para>
        </listItem>
      </list>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the total number of bytes (excluding the null-termination character) available to return in <legacyItalic>*ValuePtr</legacyItalic>. If <legacyItalic>ValuePtr</legacyItalic> is a null pointer, no length is returned. If the attribute value is a character string, and the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the data in <legacyItalic>*ValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character and is null-terminated by the driver.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLGetStmtAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value may be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetStmtAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The data returned in <legacyItalic>*ValuePtr</legacyItalic> was truncated to be <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character. The length of the untruncated string value is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>The argument <legacyItalic>Attribute</legacyItalic> was SQL_ATTR_ROW_NUMBER and the cursor was not open, or the cursor was positioned before the start of the result set or after the end of the result set.</para>
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
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the argument <legacyItalic>MessageText</legacyItalic> describes the error and its cause.</para>
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
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLGetStmtAttr</unmanagedCodeEntityReference> function was called.</para>
              <para> (DM) An asynchronously executing function was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
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
              <para>
                <legacyItalic>(DM) *ValuePtr</legacyItalic> is a character string, and BufferLength was less than zero, but not equal to SQL_NTS.</para>
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
              <para>HY109</para>
            </TD>
            <TD>
              <para>Invalid cursor position</para>
            </TD>
            <TD>
              <para>The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ROW_NUMBER and the row had been deleted or could not be fetched.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC statement attribute for the version of ODBC supported by the driver, but was not supported by the driver.</para>
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
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>For general information about statement attributes, see <legacyLink xlink:href="4c59cd8e-a713-4095-9065-20d5bdeafe43">Statement Attributes</legacyLink>.</para>
      <para>A call to <legacyBold>SQLGetStmtAttr</legacyBold> returns in <legacyItalic>*ValuePtr</legacyItalic> the value of the statement attribute specified in <legacyItalic>Attribute</legacyItalic>. That value can either be a SQLULEN value or a null-terminated character string. If the value is a SQLULEN value, some drivers may only write the lower 32-bit or 16-bit of a buffer and leave the higher-order bit unchanged. Therefore, applications should use a buffer of SQLULEN and initialize the value to 0 before calling this function. Also, the <legacyItalic>BufferLength</legacyItalic> and <legacyItalic>StringLengthPtr</legacyItalic> arguments are not used. If the value is a null-terminated string, the application specifies the maximum length of that string in the <legacyItalic>BufferLength</legacyItalic> argument, and the driver returns the length of that string in the <legacyItalic>*StringLengthPtr</legacyItalic> buffer.</para>
      <para>To allow applications calling <legacyBold>SQLGetStmtAttr</legacyBold> to work with ODBC 2.<legacyItalic>x</legacyItalic> drivers, a call to <legacyBold>SQLGetStmtAttr</legacyBold> is mapped in the Driver Manager to <legacyBold>SQLGetStmtOption</legacyBold>.</para>
      <para>The following statement attributes are read-only, so can be retrieved by <legacyBold>SQLGetStmtAttr</legacyBold>, but not set by <legacyBold>SQLSetStmtAttr</legacyBold>:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_ATTR_IMP_PARAM_DESC</para>
        </listItem>
        <listItem>
          <para>SQL_ATTR_IMP_ROW_DESC</para>
        </listItem>
        <listItem>
          <para>SQL_ATTR_ROW_NUMBER</para>
        </listItem>
      </list>
      <para>For a list of attributes that can be set and retrieved, see <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>.</para>
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