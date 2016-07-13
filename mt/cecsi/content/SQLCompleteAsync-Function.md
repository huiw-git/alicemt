---
title: SQLCompleteAsync Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLCompleteAsync Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.8 </para>
        <para>Standards Compliance: None</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <languageKeyword>SQLCompleteAsync</languageKeyword> can be used to determine when an asynchronous function is complete using either notification- or polling-based processing. For more information about asynchronous operations, see <link xlink:href="f30f026c-7e8d-4ef2-a2ee-877ce19dd6a3">Asynchronous Execution</link>.</para>
        <para>
          <languageKeyword>SQLCompleteAsync</languageKeyword> is only implemented in the ODBC Driver Manager.</para>
        <para>In notification based asynchronous processing mode, <languageKeyword>SQLCompleteAsync</languageKeyword> must be called after the Driver Manager raises the event object used for notification. <languageKeyword>SQLCompleteAsync</languageKeyword> completes the asynchronous processing and the asynchronous function will generate a return code.</para>
        <para>In polling based asynchronous processing mode, <languageKeyword>SQLCompleteAsync</languageKeyword> is an alternative to calling the original asynchronous function, without needing to specify the arguments in the original asynchronous function call. <languageKeyword>SQLCompleteAsync</languageKeyword> can be used regardless whether the ODBC Cursor Library is enabled.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax language="vb">
SQLRETURN <legacyBold>SQLCompleteAsync</legacyBold>(
      SQLSMALLINT <parameterReference>HandleType</parameterReference>,
      SQLHANDLE   <parameterReference>Handle</parameterReference>,
      RETCODE *   <parameterReference>AsyncRetCodePtr</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>HandleType</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The type of the handle on which to complete asynchronous processing. Valid values are SQL_HANDLE_DBC or SQL_HANDLE_STMT.</para>
        </definition>
        <definedTerm>
          <legacyItalic>Handle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The handle on which to complete asynchronous processing. If <legacyItalic>Handle</legacyItalic> is not a valid handle of the type specified by <legacyItalic>HandleType</legacyItalic>, <languageKeyword>SQLCompleteAsync</languageKeyword> returns SQL_INVALID_HANDLE.</para>
          <para>If <parameterReference>Handle</parameterReference> is not a valid handle of the type specified by <parameterReference>HandleType</parameterReference>, <unmanagedCodeEntityReference>SQLCompleteAsync</unmanagedCodeEntityReference> returns SQL_INVALID_HANDLE.</para>
        </definition>
        <definedTerm>
          <legacyItalic>AsyncRetCodePtr</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to a buffer that will contain the return code of the asynchronous API. If <legacyItalic>AsyncRetCodePtr</legacyItalic> is NULL, <languageKeyword>SQLCompleteAsync</languageKeyword> returns SQL_ERROR.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA, or SQL_INVALID_HANDLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>If <languageKeyword>SQLCompleteAsync</languageKeyword> returns SQL_SUCCESS, an application should get the return code of the asynchronous function from the buffer pointed to by <legacyItalic>AsyncRetCodePtr</legacyItalic>. The associated SQLSTATE, if any, can be obtained by calling <languageKeyword>SQLGetDiagRec</languageKeyword> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a statement handle or a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC and a connection handle. Those diagnostic records are associated with the asynchronous function, not this <languageKeyword>SQLCompleteAsync</languageKeyword> function.</para>
      <para>
        <languageKeyword>SQLCompleteAsync</languageKeyword> returns a code other than SQL_SUCCESS to indicate that <languageKeyword>SQLCompleteAsync</languageKeyword> is not called correctly. <languageKeyword>SQLCompleteAsync</languageKeyword> will not post any diagnostic record in this case. Possible return codes are:</para>
      <list class="nobullet">
        <listItem>
          <para>SQL_INVALID_HANDLE: The handle indicated by <legacyItalic>HandleType</legacyItalic> and <legacyItalic>Handle</legacyItalic> is not a valid handle.</para>
        </listItem>
        <listItem>
          <para>SQL_ERROR: <legacyItalic>AsyncRetCodePtr</legacyItalic> is NULL or asynchronous processing is not enabled on the handle.</para>
        </listItem>
        <listItem>
          <para>SQL_NO_DATA: In notification mode, an asynchronous operation is not in progress or the Driver Manager has not notified the application. In polling mode, an asynchronous operation is not in progress.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>In polling based asynchronous processing mode, <legacyItalic>AsyncRetCodePtr</legacyItalic> might be SQL_STILL_EXECUTING when <languageKeyword>SQLCompleteAsync</languageKeyword> returns SQL_SUCCESS. Application should keep polling until <legacyItalic>AsyncRetCodePtr</legacyItalic> is not SQL_STILL_EXECUTING. In notification based asynchronous processing mode, <legacyItalic>AsyncRetCodePtr</legacyItalic> will never be SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>
  </relatedTopics>
</developerReferenceWithSyntaxDocument>