---
title: SQLWritePrivateProfileString Function
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
  - SQLWritePrivateProfileString
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLWritePrivateProfileString Function
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
          <legacyBold>SQLWritePrivateProfileString</legacyBold> writes a value name and data to the Odbc.ini subkey of the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLWritePrivateProfileString</legacyBold>(
     LPCSTR     <parameterReference>lpszSection</parameterReference>,
     LPCSTR     <parameterReference>lpszEntry</parameterReference>,
     LPCSTR     <parameterReference>lpszString</parameterReference>,
     LPCSTR     <parameterReference>lpszFilename</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszSection</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string containing the name of the section to which the string will be copied. If the section does not exist, it is created. The name of the section is case-independent; the string can be any combination of uppercase and lowercase letters.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszEntry</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string containing the name of the key to be associated with a string. If the key does not exist in the specified section, it is created. If this argument is NULL, the entire section, including all entries within the section, is deleted.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Points to a null-terminated string to be written to the file. If this argument is NULL, the key pointed to by the <legacyItalic>lpszEntry </legacyItalic>argument is deleted.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszFilename</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Points to a null-terminated string that names the initialization file.</para>
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
      <para>When <legacyBold>SQLWritePrivateProfileString</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>Request failed</para>
            </TD>
            <TD>
              <para>The requested system information could not be written.</para>
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
        <legacyBold>SQLWritePrivateProfileString</legacyBold> is provided as a simple way to port drivers and driver setup DLLs from Microsoft® Windows® to Microsoft Windows NT®/Windows 2000. Calls to <legacyBold>WritePrivateProfileString</legacyBold> that write a profile string to the Odbc.ini file should be replaced with calls to <legacyBold>SQLWritePrivateProfileString</legacyBold>. <legacyBold>SQLWritePrivateProfileString</legacyBold> calls functions in the Win32® API to add the specified value name and data to the Odbc.ini subkey of the system information.</para>
      <para>A configuration mode indicates where the Odbc.ini entry listing DSN values is in the system information. If the DSN is a User DSN (the state variable is USERDSN_ONLY), the function writes to the Odbc.ini entry in HKEY_CURRENT_USER. If the DSN is a System DSN (SYSTEMDSN_ONLY), the function writes to the Odbc.ini entry in HKEY_LOCAL_MACHINE. If the state variable is BOTHDSN, HKEY_CURRENT_USER is tried, and if it fails, HKEY_LOCAL_MACHINE is used.</para>
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
              <para>Getting a value from the system information</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b72ca065-4d67-48df-baac-e18379a8320a">SQLGetPrivateProfileString</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>