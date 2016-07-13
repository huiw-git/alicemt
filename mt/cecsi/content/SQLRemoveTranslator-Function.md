---
title: SQLRemoveTranslator Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLRemoveTranslator
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRemoveTranslator Function
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
          <legacyBold>SQLRemoveTranslator</legacyBold> removes information about a translator from the Odbcinst.ini section of the system information and decrements the translator's component usage count by 1.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL<legacyBold> SQLRemoveTranslator</legacyBold>(
     LPCSTR    <parameterReference>lpszTranslator</parameterReference>,
     LPDWORD   <parameterReference>lpdwUsageCount</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszTranslator</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The name of the translator as registered in the Odbcinst.ini key of the system information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpdwUsageCount</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The usage count of the translator after this function has been called.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails. If no entry exists in the system information when this function is called, the function returns FALSE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLRemoveTranslator</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_COMPONENT_NOT_FOUND</para>
            </TD>
            <TD>
              <para>Component not found in registry</para>
            </TD>
            <TD>
              <para>The installer could not remove the translator information because it either did not exist in the registry or could not be found in the registry.</para>
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
              <para>The <legacyItalic>lpszTranslator</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_USAGE_UPDATE_FAILED</para>
            </TD>
            <TD>
              <para>Could not increment or decrement the component usage count</para>
            </TD>
            <TD>
              <para>The installer failed to decrement the usage count of the driver.</para>
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
        <legacyBold>SQLRemoveTranslator</legacyBold> complements the <legacyLink xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx</legacyLink> function and updates the component usage count in the system information. This function should be called only from a setup application.</para>
      <para>
        <legacyBold>SQLRemoveTranslator</legacyBold> will decrement the component usage count by 1. If the component usage count goes to 0, the translator entry in the system information will be removed. The translator entry is in the following location in the system information, under the translator name:</para>
      <para>
        <codeInline>HKEY_LOCAL_MACHINE</codeInline>
      </para>
      <para>         <codeInline>   SOFTWARE</codeInline></para>
      <para>         <codeInline>      ODBC</codeInline></para>
      <para>         <codeInline>         Odbcinst.ini</codeInline></para>
      <para>
        <legacyBold>SQLRemoveTranslator</legacyBold> does not actually remove any files. The calling program is responsible for deleting files, and maintaining the file usage count. Only after both the component usage count and the file usage count have reached zero is a file physically deleted. Some files in a component can be deleted, and others not deleted, depending on whether the files are used by other applications that have incremented the file usage count.</para>
      <para>
        <legacyBold>SQLRemoveTranslator</legacyBold> is also called as part of an upgrade process. If an application detects that it has to perform an upgrade and it has previously installed the driver, the driver should be removed and then reinstalled. <legacyBold>SQLRemoveTranslator</legacyBold> should first be called to decrement the component usage count, and then <legacyBold>SQLInstallTranslatorEx</legacyBold> should be called to increment the component usage count. The application setup program must physically replace the old files with the new files. The file usage count will remain the same, and other applications that use the older version files will now use the newer version.</para>
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
              <para>Installing a translator</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>