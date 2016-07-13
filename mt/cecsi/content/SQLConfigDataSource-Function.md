---
title: SQLConfigDataSource Function
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
  - SQLConfigDataSource
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDataSource Function
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
          <legacyBold>SQLConfigDataSource</legacyBold> adds, modifies, or deletes data sources. </para>
        <para>The functionality of <legacyBold>SQLConfigDataSource</legacyBold> can also be accessed with <link xlink:href="3bf2be83-61f9-4183-836b-85204ac7116a">ODBCCONF.EXE</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLConfigDataSource</legacyBold>(
     HWND     <parameterReference>hwndParent</parameterReference>,
     WORD     <parameterReference>fRequest</parameterReference>,
     LPCSTR   <parameterReference>lpszDriver</parameterReference>,
     LPCSTR   <parameterReference>lpszAttributes</parameterReference>);</legacySyntax>
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
          <legacyItalic>fRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of request. The <legacyItalic>fRequest</legacyItalic> argument must contain one of the following values:</para>
          <para>ODBC_ADD_DSN: Add a new user data source.   </para>
          <para>ODBC_CONFIG_DSN: Configure (modify) an existing user data source.   </para>
          <para>ODBC_REMOVE_DSN: Remove an existing user data source.   </para>
          <para>ODBC_ADD_SYS_DSN: Add a new system data source.   </para>
          <para>ODBC_CONFIG_SYS_DSN: Modify an existing system data source.   </para>
          <para>ODBC_REMOVE_SYS_DSN: Remove an existing system data source.   </para>
          <para>ODBC_REMOVE_DEFAULT_DSN: Remove the default data source specification section from the system information. (It also removes the default driver specification section from the Odbcinst.ini entry in the system information. This <legacyItalic>fRequest</legacyItalic> performs the same function as the deprecated <legacyBold>SQLRemoveDefaultDataSource</legacyBold> function.) When this option is specified, all of the other parameters in the call to <legacyBold>SQLConfigDataSource</legacyBold> should be NULLs; if they are not NULL, they will be ignored. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Driver description (usually the name of the associated DBMS) presented to users instead of the physical driver name.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszAttributes</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A doubly null-terminated list of attributes in the form of keyword-value pairs. For more information, see <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</legacyLink>.</para>
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
      <para>When <legacyBold>SQLConfigDataSource</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_INVALID_REQUEST_TYPE</para>
            </TD>
            <TD>
              <para>Invalid type of request</para>
            </TD>
            <TD>
              <para>The <legacyItalic>fRequest</legacyItalic> argument was not one of the following:</para>
              <para>ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN</para>
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
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument was invalid. It could not be found in the registry.</para>
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
              <para>The <legacyItalic>lpszAttributes</legacyItalic> argument contained a syntax error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Request</legacyItalic> failed</para>
            </TD>
            <TD>
              <para>The installer could not perform the operation requested by the <legacyItalic>fRequest</legacyItalic> argument. The call to <legacyBold>ConfigDSN</legacyBold> failed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_LOAD_LIBRARY_FAILED</para>
            </TD>
            <TD>
              <para>Could not load the driver or translator setup library</para>
            </TD>
            <TD>
              <para>The driver setup library could not be loaded.</para>
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
        <legacyBold>SQLConfigDataSource</legacyBold> uses the value of <legacyItalic>lpszDriver</legacyItalic> to read the full path of the setup DLL for the driver from the system information. It loads the DLL and calls <legacyBold>ConfigDSN</legacyBold> with the same arguments that were passed to it.</para>
      <para>
        <legacyBold>SQLConfigDataSource</legacyBold> returns FALSE if it is unable to find or load the setup DLL or if the user cancels the dialog box. Otherwise, it returns the status it received from <legacyBold>ConfigDSN</legacyBold>.</para>
      <para>
        <legacyBold>SQLConfigDataSource</legacyBold> maps the System DSN <legacyItalic>fRequest</legacyItalic>s to the User DSN <legacyItalic>fRequest</legacyItalic>s (ODBC_ADD_SYS_DSN to ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN to ODBC_CONFIG_DSN, and ODBC_REMOVE_SYS_DSN to ODBC_REMOVE_DSN). To distinguish user and System DSNs, <legacyBold>SQLConfigDataSource</legacyBold> sets the installer configuration mode according to the following table. Prior to returning, <legacyBold>SQLConfigDataSource</legacyBold> resets configuration mode to BOTHDSN. <legacyBold>ConfigDSN</legacyBold> (implemented by drivers) should call <legacyBold>SQLWriteDSNToIni</legacyBold> and <legacyBold>SQLWritePrivateProfileString</legacyBold> to support a system DSN. For more information, see <link xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</link>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>fRequest</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Configuration mode</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC_ADD_DSN</para>
            </TD>
            <TD>
              <para>USERDSN_ONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_CONFIG_DSN</para>
            </TD>
            <TD>
              <para>USERDSN_ONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_REMOVE_DSN</para>
            </TD>
            <TD>
              <para>USERDSN_ONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ADD_SYS_DSN</para>
            </TD>
            <TD>
              <para>SYSTEMDSN_ONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_CONFIG_SYS_DSN</para>
            </TD>
            <TD>
              <para>SYSTEMDSN_ONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_REMOVE_SYS_DSN</para>
            </TD>
            <TD>
              <para>SYSTEMDSN_ONLY</para>
            </TD>
          </tr>
        </tbody>
      </table>
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
              <para>Adding, modifying, or removing a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</legacyLink> (in the setup DLL)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing a data source name from the system information</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bb2e8273-7b61-4113-bfc8-f7ccc607c811">SQLRemoveDSNFromIni</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Adding a data source name to the system information</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="dc7018b2-18d4-4657-96d0-086479a47474">SQLWriteDSNToIni</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>