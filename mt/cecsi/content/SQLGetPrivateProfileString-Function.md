---
title: "SQLGetPrivateProfileString Function"
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
  - SQLGetPrivateProfileString
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetPrivateProfileString Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLGetPrivateProfileString</legacyBold> gets a list of names of values or data corresponding to a value of the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
int <legacyBold>SQLGetPrivateProfileString</legacyBold>(
     LPCSTR   <parameterReference>lpszSection</parameterReference>,
     LPCSTR   <parameterReference>lpszEntry</parameterReference>,
     LPCSTR   <parameterReference>lpszDefault</parameterReference>,
     LPCSTR   <parameterReference>RetBuffer,</parameterReference>
     INT      <parameterReference>cbRetBuffer,</parameterReference>
     LPCSTR   <parameterReference>lpszFilename</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszSection</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string that specifies the section containing the key name. If this argument is NULL, the function copies all section names in the file to the supplied buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszEntry</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to the null-terminated string containing the key name whose associated string is to be retrieved. If this argument is NULL, all key names in the section specified by the <legacyItalic>lpszSection</legacyItalic> argument are copied to the buffer specified by the <legacyItalic>RetBuffer</legacyItalic> argument.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDefault</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string that specifies the default value for the given key if the key cannot be found in the initialization file. This argument cannot be NULL.</para>
        </definition>
        <definedTerm>
          <legacyItalic>RetBuffer</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Points to the buffer that receives the retrieved string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbRetBuffer</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Specifies the size, in characters, of the buffer pointed to by the <legacyItalic>RetBuffer</legacyItalic> argument.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszFilename</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string that names the initialization file. If this argument does not contain a full path to the file, the default directory is searched.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>
        <legacyBold>SQLGetPrivateProfileString</legacyBold> returns an integer value that indicates the number of characters read.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When a call to <legacyBold>SQLGetPrivateProfileString</legacyBold> fails, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError</legacyBold> and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic> </para>
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
              <para>ODBC_ERROR_GENERAL_ERR</para>
            </TD>
            <TD>
              <para>General installer error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific installer error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_OUT_OF_MEM</para>
            </TD>
            <TD>
              <para>Out of memory</para>
            </TD>
            <TD>
              <para>The installer could not perform the function because of a lack of memory.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLGetPrivateProfileString</legacyBold> is provided as a simple way to port drivers and driver setup DLLs from Microsoft® Windows® to Microsoft Windows NT®/Windows 2000. Calls to <legacyBold>GetPrivateProfileString</legacyBold> that retrieve a profile string from the Odbc.ini file should be replaced with calls to <legacyBold>SQLGetPrivateProfileString</legacyBold>. <legacyBold>SQLGetPrivateProfileString</legacyBold> calls functions in the Win32® API to retrieve the requested names of values or data corresponding to a value of the Odbc.ini subkey of the system information.</para>
      <para>The configuration mode (as set by <legacyBold>SQLSetConfigMode</legacyBold>) indicates where the Odbc.ini entry listing DSN values is in the system information. If the DSN is a User DSN (the configuration mode is USERDSN_ONLY), the function reads from the Odbc.ini entry in HKEY_CURRENT_USER. If the DSN is a System DSN (SYSTEMDSN_ONLY), the function reads from the Odbc.ini entry in HKEY_LOCAL_MACHINE. If the configuration mode is BOTHDSN, HKEY_CURRENT_USER is tried, and if it fails, HKEY_LOCAL_MACHINE is used.</para>
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
              <para>Writing a value to the system information</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="526f36a4-92ed-4874-9725-82d27c0b86f9">SQLWritePrivateProfileString</legacyLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>