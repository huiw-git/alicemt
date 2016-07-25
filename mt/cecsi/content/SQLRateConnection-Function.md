---
title: "SQLRateConnection Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
caps.latest.revision: 10
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRateConnection Function
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
          <legacyBold>SQLRateConnection</legacyBold> determines if a driver can reuse an existing connection in the connection pool.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>SQLRETURN  SQLRateConnection(
                SQLHDBC_INFO_TOKEN   <parameterReference>hRequest</parameterReference>,
                SQLHDBC              <parameterReference>hCandidateConnection</parameterReference>,
                BOOL                 <parameterReference>fRequiredTransactionEnlistment</parameterReference>,
                TRANSID              <parameterReference>transId</parameterReference>,
                DWORD *              <parameterReference>pRating</parameterReference> );</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A token handle representing the new application connection request.</para>
        </definition>
        <definedTerm>
          <legacyItalic>hCandidateConnection</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The existing connection in the connection pool. The connection must be in an opened state.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRequiredTransactionEnlistment</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If TRUE, reusing the existing connection's <parameterReference>hCandidateConnection</parameterReference> for the new connection request (<parameterReference>hRequest</parameterReference>) requires an additional enlistment.</para>
        </definition>
        <definedTerm>
          <legacyItalic>transId</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] If <parameterReference>fRequiredTransactionEnlistment</parameterReference> is TRUE, <parameterReference>transId</parameterReference> represents the DTC transaction that the request will enlist. If <parameterReference>fRequiredTransactionEnlistment</parameterReference> is FALSE, <parameterReference>transId</parameterReference> will be ignored.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pRating</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] <parameterReference>hCandidateConnection</parameterReference>’s reuse rating for the <parameterReference>hRequest</parameterReference>. This rating will be in between 0 and 100 (inclusive).</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_ERROR, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>The Driver Manager will not process diagnostic information returned from this function.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>SQLRateConnection</legacyBold> produces a score between 0 and 100 (inclusive) indicating how well an existing connection matches the request.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Score</para>
            </TD>
            <TD>
              <para>Meaning (when SQL_SUCCESS is returned)</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>
                <parameterReference>hCandidateConnection</parameterReference> must not be reused for the <parameterReference>hRequest</parameterReference>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Any values between 1 and 98 (inclusive)</para>
            </TD>
            <TD>
              <para>The higher the score, the closer that <parameterReference>hCandidateConnection</parameterReference> match with <parameterReference>hRequest</parameterReference>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>99</para>
            </TD>
            <TD>
              <para>There are only mismatches in insignificant attributes.  The Driver Manager should stop the rating loop.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>100</para>
            </TD>
            <TD>
              <para>Perfect match.  The Driver Manager should stop the rating loop.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Any other value greater than 100</para>
            </TD>
            <TD>
              <para>
                <parameterReference>hCandidateConnection</parameterReference> is marked as dead and it will not be reused even in an future connection request.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The Driver Manager will mark a connection as dead if the return code is anything other than SQL_SUCCESS (including SQL_SUCCESS_WITH_INFO) or the rating is greater than 100. That dead connection will not be reused (even in future connection requests) and will eventually be timed out after CPTimeout passes. The Driver Manager will continue to find another connection from the pool to rate.</para>
      <para>If the Driver Manager reused a connection whose score is strictly smaller than 100 (including 99), the Driver Manager will call SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) to reset the connection back into the state requested by the application. The driver should not reset the connection in this function call.</para>
      <para>If <parameterReference>fRequiredTransactionEnlistment</parameterReference> is TRUE, reusing <parameterReference>hCandidateConnection</parameterReference> needs an extra enlistment (<parameterReference>transId</parameterReference> != NULL) or unenlistment (<parameterReference>transId</parameterReference> == NULL). This indicates the cost of reusing a connection and whether the driver should enlist / unenlist the connection if it is going to reuse the connection. If <parameterReference>fRequireTransactionEnlistment</parameterReference> is FALSE, driver should ignore the value of <parameterReference>transId</parameterReference>.</para>
      <para>The Driver Manager guarantees that the parent HENV handle of <parameterReference>hRequest</parameterReference> and <parameterReference>hCandidateConnection</parameterReference> are the same. The Driver Manager guarantees that the pool ID associated with <parameterReference>hRequest</parameterReference> and <parameterReference>hCandidateConnection</parameterReference> are the same.</para>
      <para>Applications should not call this function directly. An ODBC driver that supports driver-aware connection pooling must implement this function.</para>
      <para>Include sqlspi.h for ODBC driver development.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link></relatedTopics>
</developerReferenceWithSyntaxDocument>