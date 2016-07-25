---
title: "SQLWriteFileDSN Function"
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
  - SQLWriteFileDSN
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLWriteFileDSN Function
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
          <legacyBold>SQLWriteFileDSN</legacyBold> writes information to a File DSN.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLWriteFileDSN</legacyBold>(
     LPCSTR     <parameterReference>lpszFileName,</parameterReference>
     LPCSTR     <parameterReference>lpszAppName,</parameterReference>
     LPCSTR     <parameterReference>lpszKeyName,</parameterReference>
     LPCSTR     <parameterReference>lpszString</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszFileName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the name of the File DSN. A DSN extension is appended to all file names that do not already have a DSN extension.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszAppName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the name of the application. This is "ODBC" for the ODBC section.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszKeyName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the name of the key to be read. See "Comments" for reserved keywords.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointed to the string associated with the key to be written. The maximum length of the string pointed to by this argument is 32,767 bytes.</para>
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
      <para>When <legacyBold>SQLWriteFileDSN</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_INVALID_PATH</para>
            </TD>
            <TD>
              <para>Invalid install path</para>
            </TD>
            <TD>
              <para>The path of the file name specified in the <legacyItalic>lpszFileName</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_REQUEST_TYPE</para>
            </TD>
            <TD>
              <para>Invalid type of request</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszAppName</legacyItalic>, <legacyItalic>lpszKeyName</legacyItalic>, or <legacyItalic>lpszString</legacyItalic> argument was NULL.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>ODBC reserves the section name [ODBC] in which to store the connection information. The reserved keywords for this section are the same as those reserved for a connect string in <legacyBold>SQLDriverConnect</legacyBold>. (For more information, see the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> function description.)</para>
      <para>Applications can use these reserved keywords to write information directly to a File DSN. If an application wants to create or modify the DSN-less connection string associated with a File DSN, it can call <legacyBold>SQLWriteFileDSN</legacyBold> for any of the reserved connection string keywords in the [ODBC] section.</para>
      <para>If the <legacyItalic>lpszString</legacyItalic> argument is a null pointer, the keyword pointed to by the <legacyItalic>lpszKeyName</legacyItalic> argument will be deleted from the .dsn file. If the <legacyItalic>lpszString</legacyItalic> and <legacyItalic>lpszKeyName</legacyItalic> arguments are both null pointers, the section pointed to by the <legacyItalic>lpszAppName</legacyItalic> argument will be deleted from the .dsn file.</para>
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
              <para>Reading information from File DSNs</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ead464aa-cdc3-47dd-a0c0-997711205d31">SQLReadFileDSN</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>