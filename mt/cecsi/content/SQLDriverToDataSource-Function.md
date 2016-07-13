---
title: SQLDriverToDataSource Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLDriverToDataSource
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDriverToDataSource Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLDriverToDataSource</legacyBold> supports translations for ODBC drivers. This function is not called by ODBC-enabled applications; applications request translation through <legacyBold>SQLSetConnectAttr</legacyBold>. The driver associated with the <legacyItalic>ConnectionHandle </legacyItalic>specified in <legacyBold>SQLSetConnectAttr</legacyBold> calls the specified DLL to perform translations of all data flowing from the driver to the data source. A default translation DLL can be specified in the ODBC initialization file.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLDriverToDataSource</legacyBold>(
     UDWORD     <parameterReference>fOption</parameterReference>,
     SWORD      <parameterReference>fSqlType</parameterReference>,
     PTR        <parameterReference>rgbValueIn</parameterReference>,
     SDWORD     <parameterReference>cbValueIn</parameterReference>,
     PTR        <parameterReference>rgbValueOut</parameterReference>,
     SDWORD     <parameterReference>cbValueOutMax</parameterReference>,
     SDWORD *   <parameterReference>pcbValueOut</parameterReference>,
     UCHAR *    <parameterReference>szErrorMsg</parameterReference>,
     SWORD      <parameterReference>cbErrorMsgMax</parameterReference>,
     SWORD *    <parameterReference>pcbErrorMsg</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>fOption</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Option value.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fSqlType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The ODBC SQL data type. This argument tells the driver how to convert <legacyItalic>rgbValueIn</legacyItalic> into a form acceptable by the data source. For a list of valid SQL data types, see <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>rgbValueIn</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Value to translate.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbValueIn</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>rgbValueIn</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>rgbValueOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Result of the translation.</para>
          <alert class="note">
            <para>The translation DLL does not null-terminate this value.</para>
          </alert>
        </definition>
        <definedTerm>
          <legacyItalic>cbValueOutMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>rgbValueOut</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbValueOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The total number of bytes (excluding the null-termination byte) available to return in <legacyItalic>rgbValueOut</legacyItalic>.</para>
          <para>For character or binary data, if this is greater than or equal to <legacyItalic>cbValueOutMax</legacyItalic>, the data in <legacyItalic>rgbValueOut</legacyItalic> is truncated to <legacyItalic>cbValueOutMax</legacyItalic> bytes.   </para>
          <para>For all other data types, the value of <legacyItalic>cbValueOutMax</legacyItalic> is ignored and the translation DLL assumes that the size of <legacyItalic>rgbValueOut</legacyItalic> is the size of the default C data type of the SQL data type specified with <legacyItalic>fSqlType</legacyItalic>.   </para>
          <para>The <legacyItalic>pcbValueOut</legacyItalic> argument can be a null pointer. </para>
        </definition>
        <definedTerm>
          <legacyItalic>szErrorMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to storage for an error message. This is an empty string unless the translation failed.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbErrorMsgMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>szErrorMsg</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbErrorMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the total number of bytes (excluding the null-termination byte) available to return in <legacyItalic>szErrorMsg</legacyItalic>. If this is greater than or equal to <legacyItalic>cbErrorMsg</legacyItalic>, the data in <legacyItalic>szErrorMsg</legacyItalic> is truncated to <legacyItalic>cbErrorMsgMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbErrorMsg</legacyItalic> argument can be a null pointer.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>TRUE if the translation was successful, FALSE if the translation failed.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The driver calls <legacyBold>SQLDriverToDataSource</legacyBold> to translate all data (SQL statements, parameters, and so on) passing from the driver to the data source. The translation DLL might not translate some data, depending on the data's type and the purpose of the translation DLL. For example, a DLL that translates character data from one code page to another ignores all numeric and binary data.</para>
      <para>The value of <legacyItalic>fOption</legacyItalic> is set to the value of <legacyItalic>vParam</legacyItalic> specified by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRANSLATE_OPTION attribute. It is a 32-bit value that has a specific meaning for a given translation DLL. For example, it could specify a certain character set translation.</para>
      <para>If the same buffer is specified for <legacyItalic>rgbValueIn</legacyItalic> and <legacyItalic>rgbValueOut</legacyItalic>, the translation of data in the buffer will be performed in place.</para>
      <para>Although <legacyItalic>cbValueIn</legacyItalic>, <legacyItalic>cbValueOutMax</legacyItalic>, and <legacyItalic>pcbValueOut</legacyItalic> are of the type SDWORD, <legacyBold>SQLDriverToDataSource</legacyBold> does not necessarily support huge pointers.</para>
      <para>If <legacyBold>SQLDriverToDataSource</legacyBold> returns FALSE, data truncation might have occurred during translation. If <legacyItalic>pcbValueOut</legacyItalic> (the number of bytes available to return in the output buffer) is greater than <legacyItalic>cbValueOutMax</legacyItalic> (the length of the output buffer), then truncation occurred. The driver must determine whether or not the truncation was acceptable. If truncation did not occur, the <legacyBold>SQLDriverToDataSource</legacyBold> returned FALSE due to another error. In either case, a specific error message is returned in <legacyItalic>szErrorMsg</legacyItalic>.</para>
      <para>For more information about translating data, see <legacyLink xlink:href="38975059-b346-410f-bb27-326f3f7bbf39">Translation DLLs</legacyLink>.</para>
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
              <para>Translating data returned from the data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLDataSourceToDriver</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the setting of a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a connection attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>