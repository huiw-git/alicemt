---
title: SQLGetEnvAttr Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetEnvAttr
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
translation.priority.ht: 
  - en-gb
---
# SQLGetEnvAttr Function
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
          <legacyBold>SQLGetEnvAttr</legacyBold> returns the current setting of an environment attribute.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLGetEnvAttr</legacyBold>(
     SQLHENV        <parameterReference>EnvironmentHandle</parameterReference>,
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
          <legacyItalic>EnvironmentHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Environment handle.</para>
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
          <para>[Output] Pointer to a buffer in which to return the current value of the attribute specified by <legacyItalic>Attribute</legacyItalic>.</para>
          <para>If <legacyItalic>ValuePtr</legacyItalic> is NULL, <legacyItalic>StringLengthPtr</legacyItalic> will still return the total number of bytes (excluding the null-termination character for character data) available to return in the buffer pointed to by <legacyItalic>ValuePtr</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>BufferLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>ValuePtr</legacyItalic> points to a character string, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. If *<legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>BufferLength</legacyItalic> is ignored. If <legacyItalic>*ValuePtr</legacyItalic> is a Unicode string (when calling <legacyBold>SQLGetEnvAttrW</legacyBold>), the <legacyItalic>BufferLength</legacyItalic> argument must be an even number. If the attribute value is not a character string, <legacyItalic>BufferLength</legacyItalic> is unused.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLengthPtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A pointer to a buffer in which to return the total number of bytes (excluding the null-termination character) available to return in <legacyItalic>*ValuePtr</legacyItalic>. If <legacyItalic>ValuePtr </legacyItalic>is a null pointer, no length is returned. If the attribute value is a character string and the number of bytes available to return is greater than or equal to <legacyItalic>BufferLength</legacyItalic>, the data in *<legacyItalic>ValuePtr</legacyItalic> is truncated to <legacyItalic>BufferLength</legacyItalic> minus the length of a null-termination character and is null-terminated by the driver.</para>
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
      <para>When <legacyBold>SQLGetEnvAttr</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>EnvironmentHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLGetEnvAttr</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
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
              <para>The data returned in *<legacyItalic>ValuePtr</legacyItalic> was truncated to be <legacyItalic>BufferLength</legacyItalic> minus the null-termination character. The length of the untruncated string value is returned in *<legacyItalic>StringLengthPtr</legacyItalic>. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
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
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) <system>SQL_ATTR_ODBC_VERSION</system> has not yet been set via <unmanagedCodeEntityReference>SQLSetEnvAttr</unmanagedCodeEntityReference>. You do not need to set <system>SQL_ATTR_ODBC_VERSION</system> explicitly if you are using <unmanagedCodeEntityReference>SQLAllocHandleStd</unmanagedCodeEntityReference>.</para>
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
              <para>The value specified for the argument <legacyItalic>Attribute</legacyItalic> was a valid ODBC environment attribute for the version of ODBC supported by the driver but was not supported by the driver.</para>
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
              <para>(DM) The driver corresponding to the <legacyItalic>EnvironmentHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>For a list of attributes, see <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</legacyLink>. There are no driver-specific environment attributes. If <legacyItalic>Attribute</legacyItalic> specifies an attribute that returns a string, <legacyItalic>ValuePtr</legacyItalic> must be a pointer to a buffer in which to return the string. The maximum length of the string, including the null-termination byte, will be <legacyItalic>BufferLength</legacyItalic> bytes.</para>
      <para>         <legacyBold>SQLGetEnvAttr</legacyBold> can be called at any time between the allocation and the freeing of an environment handle. All environment attributes successfully set by the application for the environment persist until <legacyBold>SQLFreeHandle</legacyBold> is called on the <legacyItalic>EnvironmentHandle</legacyItalic> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV. More than one environment handle can be allocated simultaneously in ODBC 3<legacyItalic>.x</legacyItalic>. An environment attribute on one environment is not affected when another environment has been allocated.</para>
      <alert class="note">
        <para>The SQL_ATTR_OUTPUT_NTS environment attribute is supported by standards-compliant applications. When <legacyBold>SQLGetEnvAttr</legacyBold> is called, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager always returns SQL_TRUE for this attribute. SQL_ATTR_OUTPUT_NTS can be set to SQL_TRUE only by a call to <legacyBold>SQLSetEnvAttr</legacyBold>.</para>
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
              <para>Returning the setting of a connection attribute</para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the setting of a statement attribute</para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a connection attribute</para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting an environment attribute</para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr Function</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>             </para>
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