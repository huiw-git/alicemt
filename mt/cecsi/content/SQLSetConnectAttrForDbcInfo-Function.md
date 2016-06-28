---
title: SQLSetConnectAttrForDbcInfo Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectAttrForDbcInfo Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.81 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLSetConnectAttrForDbcInfo</legacyBold> is the same as <legacyBold>SQLSetConnectAttr</legacyBold>, but it sets the attribute on the connection information token instead of on the connection handle.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN  SQLSetConnectAttrForDbcInfo(
                SQLHDBC_INFO_TOKEN    <parameterReference>hDbcInfoToken</parameterReference>,
                SQLINTEGER            <parameterReference>Attribute</parameterReference>,
                SQLPOINTER            <parameterReference>ValuePtr</parameterReference>,
                SQLINTEGER            <parameterReference>StringLength</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hDbcInfoToken</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Token handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Attribute</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Attribute to set. The list of valid attributes is driver specific and the same as for <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ValuePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the value to be associated with <legacyItalic>Attribute</legacyItalic>. Depending on the value of <legacyItalic>Attribute</legacyItalic>, <legacyItalic>ValuePtr</legacyItalic> will be a 32-bit unsigned integer value or will point to a null-terminated character string. Note that if the <legacyItalic>Attribute</legacyItalic> argument is a driver-specific value, the value in <legacyItalic>ValuePtr</legacyItalic> may be a signed integer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> points to a character string or a binary buffer, this argument should be the length of *<legacyItalic>ValuePtr</legacyItalic>. For character string data, this argument should contain the number of bytes in the string.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is an ODBC-defined attribute and <legacyItalic>ValuePtr</legacyItalic> is an integer, <legacyItalic>StringLength</legacyItalic> is ignored.</para>
          <para>If <legacyItalic>Attribute</legacyItalic> is a driver-defined attribute, the application indicates the nature of the attribute to the Driver Manager by setting the <legacyItalic>StringLength</legacyItalic> argument. <legacyItalic>StringLength</legacyItalic> can have the following values:</para>
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
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>Same as <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>, except that the Driver Manager will use a <legacyBold>HandleType</legacyBold> of SQL_HANDLE_DBC_INFO_TOKEN and a <legacyBold>Handle</legacyBold> of <parameterReference>hDbcInfoToken</parameterReference>.</para>
    </content>
  </section>
  <section>
    <title>Remarks</title>
    <content>
      <para>
        <legacyBold>SQLSetConnectAttrForDbcInfo</legacyBold> is the same as <legacyBold>SQLSetConnectAttr</legacyBold>, but it sets the attribute on the connection information token, instead of on the connection handle. For example, if <legacyBold>SQLSetConnectAttr</legacyBold> does not recognize an attribute, <legacyBold>SQLSetConnectAttrForDbcInfo</legacyBold> should also return SQL_ERROR for that attribute.</para>
      <para>Whenever driver returns SQL_ERROR or SQL_INVALID_HANDLE, the driver should ignore this attribute to compute the pool ID. Also, the Driver Manager will obtain the diagnostic information from <parameterReference>hDbcInfoToken</parameterReference>, and return SQL_SUCCESS_WITH_INFO to the application in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> and <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>. Therefore, an application can retrieve details about why some attributes cannot be set.</para>
      <para>Applications should not call this function directly. An ODBC driver that supports driver-aware connection pooling must implement this function.</para>
      <para>Include sqlspi.h for ODBC driver development.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link></relatedTopics>
</developerReferenceWithSyntaxDocument>