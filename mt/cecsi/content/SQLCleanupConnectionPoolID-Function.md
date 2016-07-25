---
title: "SQLCleanupConnectionPoolID Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
caps.latest.revision: 10
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLCleanupConnectionPoolID Function
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
          <legacyBold>SQLCleanupConnectionPoolID</legacyBold> informs a driver that a pool ID was timed out. A pool ID can timeout whenever all connections in a pool associated with that pool ID were timed out. See <externalLink><linkText>Pooling in the Microsoft Data Access Components</linkText><linkUri>http://msdn.microsoft.com/library/ms810829.aspx</linkUri></externalLink> for more information about connection timeout.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN  SQLCleanupConnectionPoolID (
                SQLHENV    <parameterReference>EnvironmentHandle</parameterReference>
                SQLPOOLID  <parameterReference>PoolID</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>EnvironmentHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The environment handle of the pool.</para>
        </definition>
        <definedTerm>
          <legacyItalic>PoolID</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The pool associated to the pool ID that was timed out.</para>
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
      <para>The Driver Manager will not process diagnostic information returned from <legacyBold>SQLCleanupConnectionPoolID</legacyBold>.</para>
      <para>An application cannot receive the error message returned by the driver.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>SQLCleanupConnectionPoolID</legacyBold> can be called at any time, but the Driver Manager guarantees that no other thread is simultaneously calling <legacyBold>SQLGetPoolID</legacyBold> and no other thread is simultaneously calling <system>SQLRateConnection</system> and <system>SQLPoolConnect</system> with a connection info token assigned with that pool ID. Therefore, the driver must make sure this function is thread safe.</para>
      <para>A driver can clean up the resources associated with the pool ID.</para>
      <para>Applications should not call this function directly. An ODBC driver that supports driver-aware connection pooling must implement this function.</para>
      <para>Include sqlspi.h for ODBC driver development.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link></relatedTopics>
</developerReferenceWithSyntaxDocument>