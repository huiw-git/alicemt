---
title: SQLInstallerError Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLInstallerError
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallerError Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLInstallerError</legacyBold> returns error or status information for the ODBC installer functions.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
RETCODE <legacyBold>SQLInstallerError</legacyBold>(
     WORD      <parameterReference>iError</parameterReference>,
     DWORD *   <parameterReference>pfErrorCode</parameterReference>,
     LPSTR     <parameterReference>lpszErrorMsg</parameterReference>,
     WORD      <parameterReference>cbErrorMsgMax</parameterReference>,
     WORD *    <parameterReference>pcbErrorMsg</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>iError</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Error record number. Valid numbers are from 1 through 8.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pfErrorCode</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Installer error code. (For more information, see "Comments.")</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszErrorMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to storage for the error message text.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbErrorMsgMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Maximum length of the <legacyItalic>szErrorMsg</legacyItalic> buffer. This must be less than or equal to SQL_MAX_MESSAGE_LENGTH minus the null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbErrorMsgMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Maximum length of the <legacyItalic>szErrorMsg</legacyItalic> buffer. This must be less than or equal to SQL_MAX_MESSAGE_LENGTH minus the null-termination character.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbErrorMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the total number of bytes (excluding the null-termination character) available to return in <legacyItalic>lpszErrorMsg</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbErrorMsgMax</legacyItalic>, the error message text in <legacyItalic>lpszErrorMsg</legacyItalic> is truncated to <legacyItalic>cbErrorMsgMax</legacyItalic> minus the null-termination character bytes. The <legacyItalic>pcbErrorMsg</legacyItalic> argument can be a null pointer.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, or SQL_ERROR.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>
        <legacyBold>SQLInstallerError</legacyBold> does not post error values for itself. <legacyBold>SQLInstallerError</legacyBold> returns SQL_NO_DATA when it is unable to retrieve any error information (in which case <legacyItalic>pfErrorCode</legacyItalic> is undefined). If <legacyBold>SQLInstallerError</legacyBold> cannot access error values for any reason that would normally return SQL_ERROR, <legacyBold>SQLInstallerError</legacyBold> returns SQL_ERROR but does not post any error values. If you do not know the length of the warning string (<legacyItalic>lpszErrorMsg</legacyItalic>), you can set <legacyItalic>lpszErrorMsg</legacyItalic> to NULL and call <legacyBold>SQLInstallerError</legacyBold>. <legacyBold>SQLInstallerError</legacyBold> will then return the length of the warning string in <legacyItalic>cbErrorMsgMax</legacyItalic>. If the buffer for the error message is too short, <legacyBold>SQLInstallerError</legacyBold> returns SQL_SUCCESS_WITH_INFO and returns the correct <legacyItalic>pfErrorCode</legacyItalic> value for <legacyBold>SQLInstallerError</legacyBold>.</para>
      <para>To determine whether a truncation occurred in the error message, an application can compare the value in the <legacyItalic>cbErrorMsgMax</legacyItalic> argument to the actual length of the message text written to the <legacyItalic>pcbErrorMsg</legacyItalic> argument. If truncation does occur, the correct buffer length should be allocated for <legacyItalic>lpszErrorMsg</legacyItalic> and <legacyBold>SQLInstallerError</legacyBold> should be called again with the corresponding <legacyItalic>iError</legacyItalic> record.</para>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>An application calls <legacyBold>SQLInstallerError</legacyBold> when a previous call to the ODBC installer function returns FALSE. ODBC installer and driver or translator setup functions post zero or more errors only when the function fails (returns FALSE); therefore, an application calls <legacyBold>SQLInstallerError</legacyBold> only after an ODBC installer function fails.</para>
      <para>The ODBC installer error queue is flushed each time a new installer function is called. Therefore, an application cannot expect to retrieve errors for functions other than from the last installer function call.</para>
      <para>To retrieve multiple errors for a function call, an application calls <legacyBold>SQLInstallerError</legacyBold> multiple times.</para>
      <para>When there is no additional information, <legacyBold>SQLInstallerError</legacyBold> returns SQL_NO_DATA, the <legacyItalic>pfErrorCode</legacyItalic> argument is undefined, the <legacyItalic>pcbErrorMsg</legacyItalic> argument equals 0, and the <legacyItalic>lpszErrorMsg</legacyItalic> argument contains a single null-termination character (unless the <legacyItalic>cbErrorMsgMax</legacyItalic> argument is equal to 0).</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>