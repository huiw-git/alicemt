---
title: SQLPostInstallerError Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLPostInstallerError
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
translation.priority.ht: 
  - en-gb
---
# SQLPostInstallerError Function
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
          <legacyBold>SQLPostInstallerError</legacyBold> provides a mechanism for a driver or translator setup library to report errors for the <legacyBold>ConfigDriver</legacyBold>, <legacyBold>ConfigDSN</legacyBold>, and <legacyBold>ConfigTranslator</legacyBold> functions to the installer error queue. Applications do not use this API; they use <legacyBold>SQLInstallerError</legacyBold> to retrieve the error.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
RETCODE <legacyBold>SQLPostInstallerError</legacyBold>(
     DWORD    <parameterReference>fErrorCode</parameterReference>,
     LPSTR    <parameterReference>szErrorMsg</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>fErrorCode</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Installer error code.</para>
        </definition>
        <definedTerm>
          <legacyItalic>szErrorMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Error message text.</para>
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
        <legacyBold>SQLPostInstallerError</legacyBold> does not post error values for itself. If the error was successfully posted to the installer error queue (retrievable using <legacyBold>SQLInstallerError</legacyBold>), SQL_SUCCESS is returned. SQL_ERROR will be returned if the value in the <legacyItalic>dwErrorCode</legacyItalic> argument is not one of the specified installer error codes.</para>
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
              <para>Adding, modifying, or removing a driver</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9473f48f-bcae-4784-89c1-7839bad4ed13">ConfigDriver</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Adding, modifying, or removing data sources</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a translation option</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7c22f07e-36de-425b-aa67-e32a84afae92">ConfigTranslator</legacyLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>