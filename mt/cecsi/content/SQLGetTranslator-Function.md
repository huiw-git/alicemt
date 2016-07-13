---
title: SQLGetTranslator Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLGetTranslator
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetTranslator Function
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
          <legacyBold>SQLGetTranslator</legacyBold> displays a dialog box from which a user can select a translator.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLGetTranslator</legacyBold>(
     HWND      <parameterReference>hwndParent</parameterReference>,
     LPSTR     <parameterReference>lpszName</parameterReference>,
     WORD      <parameterReference>cbNameMax</parameterReference>,
     WORD *    <parameterReference>pcbNameOut</parameterReference>,
     LPSTR     <parameterReference>lpszPath</parameterReference>,
     WORD      <parameterReference>cbPathMax</parameterReference>,
     WORD *    <parameterReference>pcbPathOut</parameterReference>,
     DWORD *   <parameterReference>pvOption</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwndParent</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszName</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input/Output] Name of the translator from the system information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbNameMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Maximum length of the <legacyItalic>lpszName</legacyItalic> buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbNameOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input/Output] Total number of bytes (excluding the null-termination byte) passed or returned in <legacyItalic>lpszName</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbNameMax</legacyItalic>, the translator name in <legacyItalic>lpszName</legacyItalic> is truncated to <legacyItalic>cbNameMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbNameOut</legacyItalic> argument can be a null pointer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszPath</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Full path of the translation DLL.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbPathMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Maximum length of the <legacyItalic>lpszPath</legacyItalic> buffer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes (excluding the null-termination byte) returned in <legacyItalic>lpszPath</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbPathMax</legacyItalic>, the translation DLL path in <legacyItalic>lpszPath</legacyItalic> is truncated to <legacyItalic>cbPathMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbPathOut</legacyItalic> argument can be a null pointer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pvOption</legacyItalic> </definedTerm>
        <definition>
          <para>[Output] 32-bit translation option.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails or if the user cancels the dialog box.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLGetTranslator</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The <legacyItalic>cbNameMax</legacyItalic> or <legacyItalic>cbPathMax</legacyItalic> argument was less than or equal to 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_HWND</para>
            </TD>
            <TD>
              <para>Invalid window handle</para>
            </TD>
            <TD>
              <para>The <legacyItalic>hwndParent</legacyItalic> argument was invalid or NULL.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_NAME</para>
            </TD>
            <TD>
              <para>Invalid driver or translator name</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszName</legacyItalic> argument was invalid. It could not be found in the registry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_LOAD_LIBRARY_FAILED</para>
            </TD>
            <TD>
              <para>Could not load the driver or translator  setup library</para>
            </TD>
            <TD>
              <para>The translator library could not be loaded.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_OPTION</para>
            </TD>
            <TD>
              <para>Invalid transaction option</para>
            </TD>
            <TD>
              <para>The <legacyItalic>pvOption</legacyItalic> argument contained an invalid value.</para>
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
      <para>If <legacyItalic>hwndParent</legacyItalic> is null or if <legacyItalic>lpszName</legacyItalic>, <legacyItalic>lpszPath</legacyItalic>, or <legacyItalic>pvOption</legacyItalic> is a null pointer, <legacyBold>SQLGetTranslator</legacyBold> returns FALSE. Otherwise, it displays the list of installed translators in the following dialog box.</para>
      <mediaLink>
        <image xlink:href="095ddaea-c8f2-4b91-a0d0-24c4eb05eb2d" />
      </mediaLink>
      <para>If <legacyItalic>lpszName</legacyItalic> contains a valid translator name, it is selected. Otherwise, &lt;No Translator&gt; is selected.</para>
      <para>If the user chooses &lt;No Translator&gt;, the contents of <legacyItalic>lpszName</legacyItalic>, <legacyItalic>lpszPath</legacyItalic>, and <legacyItalic>pvOption</legacyItalic> are not touched. <legacyBold>SQLGetTranslator</legacyBold> sets <legacyItalic>pcbNameOut</legacyItalic> and <legacyItalic>pcbPathOut</legacyItalic> to 0 and returns TRUE.</para>
      <para>If the user chooses a translator, <legacyBold>SQLGetTranslator</legacyBold> calls <legacyBold>ConfigTranslator</legacyBold> in the translator's setup DLL. If <legacyBold>ConfigTranslator</legacyBold> returns FALSE, <legacyBold>SQLGetTranslator</legacyBold> returns to its dialog box. If <legacyBold>ConfigTranslator</legacyBold> returns TRUE, <legacyBold>SQLGetTranslator</legacyBold> returns TRUE, along with the selected translator name, path, and translation option.</para>
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
              <para>Configuring a translator</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7c22f07e-36de-425b-aa67-e32a84afae92">ConfigTranslator</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting a translation attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a translation attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>