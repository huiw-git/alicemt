---
title: SQLAsyncNotificationCallback Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLAsyncNotificationCallback Function
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
          <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> allows a driver to call back to the Driver Manager when there is some progress for the current asynchronous operation after the driver returns SQL_STILL_EXECUTING. <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> can only called by the driver.</para>
        <para>Drivers do not call <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> with function name <languageKeyword>SQLAsyncNotificationCallback</languageKeyword>. Instead, the Driver Manager passes a function pointer to a driver as the value for the SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK or SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK attribute of the corresponding connection handle or statement handle, respectively. Different handles may be assigned different function pointer values. The type of the function pointer is defined as SQL_ASYNC_NOTIFICATION_CALLBACK.</para>
        <para>
          <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> is thread-safe. A driver can choose to use multiple threads calling <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> on different handles simultaneously.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(
   SQLPOINTER <parameterReference>pContex</parameterReference>, 
   BOOL <parameterReference>fLast</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>pContex</legacyItalic>
        </definedTerm>
        <definition>
          <para>Pointer to a data structure defined by the Driver Manager. The value is passed to the driver via SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) or SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  The driver does not have access to the value.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fLast</legacyItalic>
        </definedTerm>
        <definition>
          <para>Used by a driver to indicates that this callback function invocation is the last one for the current asynchronous operation. The driver will return a return code other than SQL_STILL_EXECUTING when the Driver Manager calls the function again. The Driver Manager may use this information, for example, to inform the application in advance that the asynchronous operation will complete.</para>
          <para>If <parameterReference>Handle</parameterReference> is not a valid handle of the type specified by <parameterReference>HandleType</parameterReference>, <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> returns SQL_INVALID_HANDLE.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS or SQL_ERROR.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>
        <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> can return SQL_ERROR for the following two situations (these indicate an implementation problem in the driver or Driver Manager.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
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
              <para>Connection or statement did not request notification.</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Invalid <parameterReference>handle</parameterReference></para>
            </TD>
            <TD>
              <para>The driver passed in an invalid handle, which failed the internal Driver Manager validation tests.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>
  </relatedTopics>
</developerReferenceWithSyntaxDocument>