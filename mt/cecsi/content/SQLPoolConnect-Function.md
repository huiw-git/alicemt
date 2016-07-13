---
title: SQLPoolConnect Function
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLPoolConnect Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.8 Standards Compliance: ODBC</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLPoolConnect</legacyBold> is used to create a new connection if no connection in the pool can be reused.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN  SQLPoolConnect(
                SQLHDBC              <parameterReference>hDbc</parameterReference>,
                SQLHDBC_INFO_TOKEN   <parameterReference>hDbcInfoToken</parameterReference>,
                WCHAR *              <parameterReference>wszOutConnectString</parameterReference>,
                SQLSMALLINT          <parameterReference>cchConnectStringBuffer</parameterReference>,
                SQLSMALLINT *        <parameterReference>cchConnectStringLen</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hDbc</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The connection handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>hDbcInfoToken</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The token handle for the new application connection request.</para>
        </definition>
        <definedTerm>
          <legacyItalic>wszOutConnectString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer for the completed connection string. Upon successful connection to the target data source, this buffer contains the completed connection string. Applications should allocate at least 1,024 characters for this buffer.</para>
          <para>If <parameterReference>wszOutConnectString</parameterReference> is NULL, <parameterReference>cchConnectStringLen</parameterReference> will still return the total number of characters (excluding the null-termination character for character data) available to return in the buffer pointed to by <parameterReference>wszOutConnectString</parameterReference>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cchConnectStringBuffer</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the *<parameterReference>wszOutConnectString</parameterReference> buffer, in characters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cchConnectStringLen</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer in which to return the total number of characters (excluding the null-termination character) available to return in *<parameterReference>wszOutConnectString</parameterReference>. If the number of characters available to return is greater than or equal to <parameterReference>cchConnectStringBuffer</parameterReference>, the completed connection string in *<parameterReference>wszOutConnectString</parameterReference> is truncated to <parameterReference>cchConnectStringBuffer</parameterReference> minus the length of a null-termination character.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or, SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>Similar to <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> for any input validation error, except that the Driver Manager will use a <legacyBold>HandleType</legacyBold> of SQL_HANDLE_DBC_INFO_TOKEN and a <legacyBold>Handle</legacyBold> of <parameterReference>hDbcInfoToken</parameterReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The Driver Manager guarantees that the parent HENV handle of <parameterReference>hDbc</parameterReference> and <parameterReference>hDbcInfoToken</parameterReference> are the same.</para>
      <para>Unlike <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>, there is no <parameterReference>DriverCompletion</parameterReference> argument to prompt users to enter connection information. A prompting dialog is disallowed in the pooling scenario.</para>
      <para>Applications should not call this function directly. An ODBC driver that supports driver-aware connection pooling must implement this function.</para>
      <para>Whenever a driver returns SQL_ERROR or SQL_INVALID_HANDLE, the Driver Manager returns the error to the application (in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> or <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>).</para>
      <para>Whenever a driver returns SQL_SUCCESS_WITH_INFO, the Driver Manager will obtain the diagnostic information from <parameterReference>hDbcInfoToken</parameterReference>, and return SQL_SUCCESS_WITH_INFO to the application in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> and <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>.</para>
      <para>When an application uses <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>, <parameterReference>wszOutConnectString</parameterReference> will be a NULL buffer (the last three parameters will all be set to NULL, 0, NULL). Otherwise, the driver must return the output connection string, which will be returned to application’s <link xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</link> call.</para>
      <para>Include sqlspi.h for ODBC driver development.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link></relatedTopics>
</developerReferenceWithSyntaxDocument>