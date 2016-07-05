---
title: SQLGetInstalledDrivers Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetInstalledDrivers
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
translation.priority.ht: 
  - en-gb
---
# SQLGetInstalledDrivers Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLGetInstalledDrivers</legacyBold> reads the [ODBC Drivers] section of the system information and returns a list of descriptions of the installed drivers.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLGetInstalledDrivers</legacyBold>(
     LPSTR   <parameterReference>lpszBuf</parameterReference>,
     WORD    <parameterReference>cbBufMax</parameterReference>,
     WORD *  <parameterReference>pcbBufOut</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszBuf</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] List of descriptions of the installed drivers. For information about the list structure, see "Comments."</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbBufMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszBuf</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbBufOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes (excluding the null-termination byte) returned in <legacyItalic>lpszBuf</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbBufMax</legacyItalic>, the list of driver descriptions in <legacyItalic>lpszBuf</legacyItalic> is truncated to <legacyItalic>cbBufMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbBufOut</legacyItalic> argument can be a null pointer.</para>
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
      <para>When <legacyBold>SQLGetInstalledDrivers</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The <legacyItalic>lpszBuf</legacyItalic> argument was NULL or invalid, or the <legacyItalic>cbBufMax</legacyItalic> argument was less than or equal to 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_COMPONENT_NOT_FOUND</para>
            </TD>
            <TD>
              <para>Component not found in registry</para>
            </TD>
            <TD>
              <para>The installer could not find the [ODBC Drivers] section in the registry.</para>
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
      <para>Each driver description is terminated with a null byte, and the entire list is terminated with a null byte. (That is, two null bytes mark the end of the list.) If the allocated buffer is not large enough to hold the entire list, the list is truncated without error. An error is returned if a null pointer is passed in as <legacyItalic>lpszBuf</legacyItalic>.</para>
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
              <para>Returning driver descriptions and attributes</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>