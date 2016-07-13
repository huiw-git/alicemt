---
title: SQLInstallTranslatorEx Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLInstallTranslatorEx
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallTranslatorEx Function
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
          <legacyBold>SQLInstallTranslatorEx</legacyBold> adds information about a translator to the Odbcinst.ini section of the system information (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.INI\ODBC Translators registry key).</para>
        <para>The functionality of <legacyBold>SQLInstallTranslatorEx</legacyBold> can also be accessed with <link xlink:href="3bf2be83-61f9-4183-836b-85204ac7116a">ODBCCONF.EXE</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLInstallTranslatorEx</legacyBold>(
     LPCSTR    <parameterReference>lpszTranslator</parameterReference>,
     LPCSTR    <parameterReference>lpszPathIn</parameterReference>,
     LPSTR     <parameterReference>lpszPathOut</parameterReference>,
     WORD      <parameterReference>cbPathOutMax</parameterReference>,
     WORD *    <parameterReference>pcbPathOut</parameterReference>,
     WORD      <parameterReference>fRequest</parameterReference>,
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
          <para>[Input] This must contain a doubly null-terminated list of keyword-value pairs describing the translator. For more information about keyword-value pair syntax, see <link xlink:href="3c0edeee-d43a-4466-a177-bf2d2435707a">Translator Specification Subkeys</link>.</para>
          <para>The <legacyBold>Translator</legacyBold> and <legacyBold>Setup</legacyBold> keywords must be included in the <legacyItalic>lpszTranslator</legacyItalic> string. The translation DLL is listed with the <legacyBold>Translator</legacyBold> keyword, and the translator setup DLL is listed with the <legacyBold>Setup</legacyBold> keyword. Each pair is terminated with a NULL byte, and the entire list is terminated with a NULL byte. (That is, two NULL bytes mark the end of the list.) The format of <legacyItalic>lpszTranslator</legacyItalic> is as follows:</para>
          <para>\0Translator=<legacyItalic>translator-DLL-filename</legacyItalic>\0[Setup=<legacyItalic>setup-DLL-filename</legacyItalic>\0]\0</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszPathIn</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Full path of where the translator is to be installed or a null pointer. If <legacyItalic>lpszPath</legacyItalic> is a null pointer, the translators will be installed in the System directory.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The path of the target directory where the translator should be installed. If the translator has never been installed, <legacyItalic>lpszPathOut</legacyItalic> is the same as <legacyItalic>lpszPathIn</legacyItalic>. If there exists a prior installation of the translator, <legacyItalic>lpszPathOut</legacyItalic> is the path of the prior installation.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbPathOutMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszPathOut.</legacyItalic></para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes available to return in <legacyItalic>lpszPathOut</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbPathOutMax</legacyItalic>, the output path in <legacyItalic>lpszPathOut</legacyItalic> is truncated to <legacyItalic>pcbPathOutMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbPathOut</legacyItalic> argument can be a null pointer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of request. <legacyItalic>fRequest </legacyItalic>must contain one of the following values:</para>
          <para>ODBC_INSTALL_INQUIRY: Inquire about where a translator can be installed.   </para>
          <para>ODBC_INSTALL_COMPLETE: Complete the installation request. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpdwUsageCount</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The usage count of the translator after this function has been called.</para>
          <para>Applications should not set the usage count. ODBC will maintain this count.</para>
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
      <para>When <legacyBold>SQLInstallTranslatorEx</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The <legacyItalic>lpszPathOut</legacyItalic> argument was not large enough to contain the output path. The buffer contains the truncated path.</para>
              <para>The <legacyItalic>cbPathOutMax</legacyItalic> argument was 0, and the <legacyItalic>fRequest</legacyItalic> argument was ODBC_INSTALL_COMPLETE.</para>
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
              <para>The <legacyItalic>fRequest</legacyItalic> argument was not one of the following:</para>
              <para>ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_KEYWORD_VALUE</para>
            </TD>
            <TD>
              <para>Invalid keyword-value pairs</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszTranslator</legacyItalic> argument contained a syntax error.</para>
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
              <para>The <legacyItalic>lpszPathIn</legacyItalic> argument contained an invalid path.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_PARAM_SEQUENCE</para>
            </TD>
            <TD>
              <para>Invalid parameter sequence</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszTranslator</legacyItalic> argument did not contain a list of keyword-value pairs. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_USAGE_UPDATE_FAILED</para>
            </TD>
            <TD>
              <para>Could not increment or decrement the registry's component usage count</para>
            </TD>
            <TD>
              <para>The installer failed to increment the translator's usage count.</para>
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
        <legacyBold>SQLInstallTranslatorEx</legacyBold> provides a mechanism to install just the translator. This function does not actually copy any files. The calling program is responsible for copying the translator files.</para>
      <para>
        <legacyBold>SQLInstallTranslatorEx</legacyBold> increments the component usage count for the installed translator by 1. If a version of the translator already exists but the component usage count for the translator does not exist, the new component usage count value is set to 2.</para>
      <para>The application setup program is responsible for physically copying the translator file and maintaining the file usage count. If the translator file has not previously been installed, the application setup program must copy the file or files and create the file or files usage count. If the file has previously been installed, the setup program simply increments the file usage count.</para>
      <para>If an older version of the translator was previously installed by the application, the translator should be uninstalled and then reinstalled, so that the translator component usage count is valid. <legacyBold>SQLRemoveTranslator</legacyBold> should be called to decrement the component usage count, and then <legacyBold>SQLInstallTranslatorEx</legacyBold> should be called to increment the component usage count. The application setup program must replace the old file or files with the new file. The file usage count will remain the same, and other applications that used the older version file will now use the newer version.</para>
      <para>The length of the path in <legacyItalic>lpszPathOut</legacyItalic> in <legacyBold>SQLInstallTranslatorEx</legacyBold> allows for a two-phase install process, so an application can determine what <legacyItalic>cbPathOutMax</legacyItalic> should be by calling <legacyBold>SQLInstallTranslatorEx</legacyBold> with an <legacyItalic>fRequest</legacyItalic> of ODBC_INSTALL_INQUIRY mode. This will return the total number of bytes available in the <legacyItalic>pcbPathOut</legacyItalic> buffer. <legacyBold>SQLInstallTranslatorEx</legacyBold> can then be called with an <legacyItalic>fRequest</legacyItalic> of ODBC_INSTALL_COMPLETE and the <legacyItalic>cbPathOutMax</legacyItalic> argument set to the value in the <legacyItalic>pcbPathOut</legacyItalic> buffer, plus the null-termination character.</para>
      <para>If you choose not to use the two-phase model for <legacyBold>SQLInstallTranslatorEx</legacyBold>, you must set <legacyItalic>cbPathOutMax</legacyItalic>, which defines the size of the storage for the path of the target directory, to the value _MAX_PATH, as defined in Stdlib.h, to prevent truncation.</para>
      <para>When <legacyItalic>fRequest</legacyItalic> is ODBC_INSTALL_COMPLETE, <legacyBold>SQLInstallTranslatorEx</legacyBold> does not allow <legacyItalic>lpszPathOut</legacyItalic> to be NULL (or <legacyItalic>cbPathOutMax</legacyItalic> to be 0). If <legacyItalic>fRequest</legacyItalic> is ODBC_INSTALL_COMPLETE, FALSE is returned when the number of bytes available to return is greater than or equal to <legacyItalic>cbPathOutMax</legacyItalic>, with the result that truncation occurs.</para>
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
              <para>Returning a default translation option</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7c22f07e-36de-425b-aa67-e32a84afae92">ConfigTranslator</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Selecting translators</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="33879db3-5ef9-4585-9be5-69376157e017">SQLGetTranslator</legacyLink> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing translators</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c6feda49-0359-4224-8de9-77125cf2397b">SQLRemoveTranslator</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>