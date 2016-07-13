---
title: SQLReadFileDSN Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLReadFileDSN
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLReadFileDSN Function
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
          <legacyBold>SQLReadFileDSN</legacyBold> reads information from a File DSN.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLReadFileDSN</legacyBold>(
     LPCSTR   <parameterReference>lpszFileName,</parameterReference>
     LPCSTR   <parameterReference>lpszAppName,</parameterReference>
     LPCSTR   <parameterReference>lpszKeyName,</parameterReference>
     LPSTR    <parameterReference>lpszString,</parameterReference>
     WORD     <parameterReference>cbString,</parameterReference>
     WORD *   <parameterReference>pcbString</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszFileName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the data buffer containing the name of the .dsn file. A .dsn extension is appended to all file names that do not already have a .dsn extension. The value in <legacyItalic>*lpszFileName</legacyItalic> must be a null-terminated string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszAppName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the data buffer containing the name of the application. This is "ODBC" for the ODBC section. The value in <legacyItalic>*lpszAppName</legacyItalic> must be a null-terminated string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszKeyName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Pointer to the data buffer containing the name of the key to be read. See "Comments" for reserved keywords. The value in <legacyItalic>*lpszAppName</legacyItalic> must be a null-terminated string.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Pointer to the data buffer containing the string associated with the key to be read.</para>
          <para>If <legacyItalic>*lpszFileName</legacyItalic> is a valid .dsn file name but the <legacyItalic>lpszAppName</legacyItalic> argument is a null pointer and the <legacyItalic>lpszKeyName</legacyItalic> argument is a null pointer, then <legacyItalic>*lpszString</legacyItalic> contains a list of valid applications. If <legacyItalic>*lpszFileName</legacyItalic> is a valid .dsn file name and <legacyItalic>*lpszAppName</legacyItalic> is a valid application name, but the <legacyItalic>lpszKeyName</legacyItalic> argument is a null pointer, then <legacyItalic>*lpszString</legacyItalic> contains a list of valid reserved keywords in the appropriate section of the DSN file, delimited by semicolons. If <legacyItalic>*lpszFileName</legacyItalic> is a valid .dsn file name but <legacyItalic>*lpszAppName</legacyItalic> is a null pointer and the <legacyItalic>lpszKeyName</legacyItalic> argument is a null pointer, then <legacyItalic>*lpszString</legacyItalic> contains a list of the sections in the DSN file, delimited by semicolons. </para>
        </definition>
        <definedTerm>
          <legacyItalic>cbString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of the <legacyItalic>*lpszString</legacyItalic> buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbString</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes available to return in <legacyItalic>*lpszString</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbString</legacyItalic>, the output string in <legacyItalic>*lpszString</legacyItalic> is truncated to <legacyItalic>cbString</legacyItalic> minus the null-termination character. The <legacyItalic>pcbString</legacyItalic> argument can be a null pointer.</para>
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
      <para>When <legacyBold>SQLReadFileDSN</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_INVALID_BUFF_LEN</para>
            </TD>
            <TD>
              <para>Invalid buffer length</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszString</legacyItalic> argument was NULL.</para>
              <para>The <legacyItalic>cbString</legacyItalic> argument was less than or equal to 0. </para>
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
              <para>The <legacyItalic>lpszAppName</legacyItalic> argument was NULL, while the <legacyItalic>lpszKeyName</legacyItalic> argument was valid.</para>
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
          <tr>
            <TD>
              <para>ODBC_ERROR_OUTPUT_STRING_TRUNCATED</para>
            </TD>
            <TD>
              <para>Output string truncated</para>
            </TD>
            <TD>
              <para>The string returned in <legacyItalic>*lpszString</legacyItalic> was truncated because the value in <legacyItalic>cbString</legacyItalic> was less than or equal to the value in <legacyItalic>*pcbString</legacyItalic>.</para>
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
              <para>The keyword did not exist in the file DSN.</para>
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
      <para>Applications can use these reserved keywords to read the information in a File DSN. If an applications wants to find out the DSN-less connection string associated with a File DSN, it can call <legacyBold>SQLReadFileDSN</legacyBold> for any of the reserved connection string keywords in the [ODBC] section. The full connection string passed in a DSN-less connection is a combination of all of the keywords (reserved and driver-specific) in the [ODBC] section.</para>
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
              <para>Writing information to a File DSN</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9e18f56f-1061-416b-83d4-ffeec42ab5a9">SQLWriteFileDSN</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>