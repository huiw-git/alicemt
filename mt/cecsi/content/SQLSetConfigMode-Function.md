---
title: "SQLSetConfigMode Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLSetConfigMode
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConfigMode Function
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
          <legacyBold>SQLSetConfigMode</legacyBold> sets the configuration mode that indicates where the Odbc.ini entry listing DSN values is in the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLSetConfigMode</legacyBold>(
     UWORD     <parameterReference>wConfigMode</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>wConfigMode</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The installer configuration mode (see "Comments"). The value in <legacyItalic>wConfigMode</legacyItalic> can be:</para>
          <para>ODBC_USER_DSN</para>
          <para>ODBC_SYSTEM_DSN</para>
          <para>ODBC_BOTH_DSN </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLSetConfigMode</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic>
              </para>
            </TD>
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
              <para>ODBC_ERROR_INVALID_PARAM_SEQUENCE</para>
            </TD>
            <TD>
              <para>Invalid parameter sequence</para>
            </TD>
            <TD>
              <para>The <legacyItalic>wConfigMode</legacyItalic> argument did not contain ODBC_USER_DSN, ODBC_SYSTEM_DSN, or ODBC_BOTH_DSN.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>This function is used to set where the Odbc.ini entry listing DSN values is in the system information. If <legacyItalic>wConfigMode</legacyItalic> is ODBC_USER_DSN, the DSN is a User DSN and the function reads from the Odbc.ini entry in HKEY_CURRENT_USER. If it is ODBC_SYSTEM_DSN, the DSN is a System DSN and the function reads from the Odbc.ini entry in HKEY_LOCAL_MACHINE. If it is ODBC_BOTH_DSN, HKEY_CURRENT_USER is tried, and if it fails, then HKEY_LOCAL_MACHINE is used.</para>
      <para>This function does not affect <legacyBold>SQLCreateDataSource</legacyBold> and <legacyBold>SQLDriverConnect</legacyBold>. The configuration mode has to be set when a driver reads from the registry by calling <legacyBold>SQLGetPrivateProfileString</legacyBold> or writes to the registry by calling <legacyBold>SQLWritePrivateProfileString</legacyBold>. Calls to <legacyBold>SQLGetPrivateProfileString</legacyBold> and <legacyBold>SQLWritePrivateProfileString</legacyBold> use the configuration mode to know which part of the registry to operate on.</para>
      <alert class="caution">
        <para>
          <legacyBold>SQLSetConfigMode</legacyBold> should be called only when necessary; if the mode is improperly set, the ODBC Installer may fail to function properly.</para>
      </alert>
      <para>
        <legacyBold>SQLSetConfigMode</legacyBold> makes a direct registry modification of the configuration mode. This is apart from the process of modifying the configuration mode by a call to <legacyBold>SQLConfigDataSource</legacyBold>. A call to <legacyBold>SQLConfigDataSource</legacyBold> sets the configuration mode to distinguish user and System DSNs when modifying a DSN. Prior to returning, <legacyBold>SQLConfigDataSource</legacyBold> resets the configuration mode to BOTHDSN.</para>
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
              <para>Creating a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="76ee851a-dca9-40cc-8e9e-eb3f74e560ee">SQLCreateDataSource</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connecting to a data source using a connection string or dialog box</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Retrieving the configuration mode</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b96ab3b8-08d5-4fea-9ffe-e03043efbf2d">SQLGetConfigMode</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>