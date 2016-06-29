---
title: SQLSetDriverConnectInfo Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
translation.priority.ht: 
  - en-gb
---
# SQLSetDriverConnectInfo Function
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
          <legacyBold>SQLSetDriverConnectInfo</legacyBold> is used to set the connection string into the connection info token for an application’s <legacyBold>SQLDriverConnect</legacyBold> call.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN SQLSetDriverConnectInfo(
                SQLHDBC_INFO_TOKEN   <parameterReference>hDbcInfoToken</parameterReference>,
                WCHAR *              <parameterReference>InConnectionString</parameterReference>,
                SQLSMALLINT          <parameterReference>StringLength1</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>TokenHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Token handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>InConnectionString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A full connection string (see the syntax in "Comments" in <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>), a partial connection string, or an empty string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StringLength1</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<parameterReference>InConnectionString</parameterReference>, in characters if the string is Unicode, or bytes if string is ANSI or DBCS.</para>
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
      <para>Same as <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> related to any input validation error, except that the Driver Manager will use a <legacyBold>HandleType</legacyBold> of SQL_HANDLE_DBC_INFO_TOKEN and a <legacyBold>Handle</legacyBold> of <parameterReference>hDbcInfoToken</parameterReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
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