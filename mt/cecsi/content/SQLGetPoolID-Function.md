---
title: SQLGetPoolID Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetPoolID Function
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
          <legacyBold>SQLGetPoolID</legacyBold> retrieves the pool ID.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN  SQLGetPoolID (
                SQLHDBC_INFO_TOKEN    <parameterReference>hDbcInfoToken</parameterReference>,
                POOLID *              <parameterReference>pPoolID</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hDbcInfoToken</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Token handle that contains all connection information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pPoolID</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The pool ID, which is used to identify a set of connections that can be used interchangeably (possibly requiring an additional reset).</para>
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
      <para>When <legacyBold>SQLGetPoolID</legacyBold> returns SQL_ERROR or SQL_SUCCESS_WITH_INFO, the Driver Manager will use a <legacyBold>HandleType</legacyBold> of SQL_HANDLE_DBC_INFO_TOKEN and a <legacyBold>Handle</legacyBold> of <parameterReference>hDbcInfoToken</parameterReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>SQLGetPoolID</legacyBold> is used to obtain the pool ID given a set of connection information (from <legacyBold>SQLSetConnectAttrForDbcInfo</legacyBold>, <legacyBold>SQLSetDriverConnectInfo</legacyBold>, and <legacyBold>SQLSetConnectInfo</legacyBold>). This pool ID is used to identify a set of connections that can be used interchangeably (possibly requiring an additional reset). The pool ID will be used to identify the connection pool for that group of connections.</para>
      <para>Whenever a driver returns SQL_ERROR or SQL_INVALID_HANDLE, the Driver Manager returns the error to the application (in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> or <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>).</para>
      <para>Whenever a driver returns SQL_SUCCESS_WITH_INFO, the Driver Manager will obtain the diagnostic information from <parameterReference>hDbcInfoToken</parameterReference>, and return SQL_SUCCESS_WITH_INFO to the application in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> and <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>.</para>
      <para>Applications should not call this function directly. An ODBC driver that supports driver-aware connection pooling must implement this function.</para>
      <para>Include sqlspi.h for ODBC driver development.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link></relatedTopics>
</developerReferenceWithSyntaxDocument>