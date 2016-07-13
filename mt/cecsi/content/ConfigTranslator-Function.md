---
title: ConfigTranslator Function
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
  - ConfigTranslator
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ConfigTranslator Function
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
          <legacyBold>ConfigTranslator</legacyBold> returns a default translation option for a translator. It can be in the translator DLL or a separate setup DLL.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>ConfigTranslator</legacyBold>(
     HWND     <parameterReference>hwndParent</parameterReference>,
     DWORD *  <parameterReference>pvOption</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwndParent</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle. The function will not display any dialog boxes if the handle is null.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pvOption</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A 32-bit translation option.</para>
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
      <para>When <legacyBold>ConfigTranslator</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value is posted to the installer error buffer by a call to <legacyBold>SQLPostInstallerError</legacyBold> and can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_DRIVER_SPECIFIC</para>
            </TD>
            <TD>
              <para>Driver- or translator-specific error</para>
            </TD>
            <TD>
              <para>A driver-specific error for which there is no defined ODBC installer error. The <legacyItalic>SzError</legacyItalic> argument in a call to the <legacyBold>SQLPostInstallerError</legacyBold> function should contain the driver-specific error message.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_OPTION</para>
            </TD>
            <TD>
              <para>Invalid translation option</para>
            </TD>
            <TD>
              <para>The <legacyItalic>pvOption</legacyItalic> argument contained an invalid value.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>If the translator supports only a single translation option, <legacyBold>ConfigTranslator</legacyBold> returns TRUE and sets <legacyItalic>pvOption</legacyItalic> to the 32-bit option. Otherwise, it determines the default translation option to use. <legacyBold>ConfigTranslator</legacyBold> can display a dialog box with which a user selects a default translation option.</para>
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
              <para>Getting a translation option</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Selecting a translator</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="33879db3-5ef9-4585-9be5-69376157e017">SQLGetTranslator</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a translation option</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>