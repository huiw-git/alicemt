---
title: "SQLRemoveDriverManager Function"
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
  - SQLRemoveDriverManager
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
caps.latest.revision: 12
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRemoveDriverManager Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para> </para>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 3.0: Deprecated in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1, and later operating systems.</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLRemoveDriverManager</legacyBold> changes or removes information about the ODBC core components from the Odbcinst.ini entry in the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLRemoveDriverManager</legacyBold>(
     LPDWORD     <parameterReference>pdwUsageCount</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>pdwUsageCount</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The usage count of the Driver Manager after this function has been called.</para>
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
      <para>When <legacyBold>SQLRemoveDriverManager</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The installer could not remove the Driver Manager information because it either did not exist in the registry or could not be found in the registry.</para>
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
              <para>The installer failed to decrement the usage count of the Driver Manager.</para>
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
        <legacyBold>SQLRemoveDriverManager</legacyBold> complements the <legacyBold>SQLInstallDriverManager</legacyBold> function, and updates the component usage count in the system information. This function should be called only from a setup application.</para>
      <para>
        <legacyBold>SQLRemoveDriverManager</legacyBold> will decrement the core component usage count by 1. If the component usage count goes to 0, the entry system information will be removed. The core component entry is in the following location in the system information, under the title "ODBC Core":</para>
      <para>
        <codeInline>HKEY_LOCAL_MACHINE</codeInline>
      </para>
      <para>           <codeInline>   SOFTWARE</codeInline></para>
      <para>           <codeInline>      ODBC</codeInline></para>
      <para>           <codeInline>         Odbcinst.ini</codeInline></para>
      <alert class="caution">
        <para>An application should not physically remove Driver Manager files when the component usage count and the file usage count reach zero.</para>
      </alert>
      <para>
        <legacyBold>SQLRemoveDriverManager</legacyBold> does not actually remove any files. The calling program is responsible for deleting files and maintaining the file usage counts. Driver Manager files should not, however, be removed when both the component usage count and the file usage count have reached zero, because these files may be used by other applications that have not incremented the file usage count.</para>
      <para>
        <legacyBold>SQLRemoveDriverManager</legacyBold> is called as part of the Uninstall process. ODBC core components (which include the Driver Manager, Cursor Library, Installer, Language Library, Administrator, thunking files, and so on) are uninstalled as a whole. The following files are not removed when <legacyBold>SQLRemoveDriverManager</legacyBold> is called as part of the Uninstall process:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>ODBC32DLL</para>
            </TD>
            <TD>
              <para>ODBCCP32.DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBCCR32.DLL</para>
            </TD>
            <TD>
              <para>ODBC16GT.DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBCCU32.DLL</para>
            </TD>
            <TD>
              <para>ODBC32GT.DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBCINT.DLL</para>
            </TD>
            <TD>
              <para>DS16GT.DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBCTRAC.DLL</para>
            </TD>
            <TD>
              <para>DS32GT.DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MSVCRT40.DLL</para>
            </TD>
            <TD>
              <para>ODBCAD32.EXE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBCCP32.CPL</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <legacyBold>SQLRemoveDriverManager</legacyBold> is also called as part of an upgrade process. If an application detects that it has to perform an upgrade and it has previously installed the driver, the driver should be removed and then reinstalled.</para>
      <para>
        <legacyBold>SQLRemoveDriverManager</legacyBold> should first be called to decrement the component usage count. <legacyBold>SQLInstallDriverEx</legacyBold> should then be called to increment the component usage count. The application setup program must replace the old core component files with the new files. The file usage counts will remain the same, and other applications that use the older version core component files will now use the newer version files.</para>
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
              <para>Installing a Driver Manager</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="aebc439b-fffd-4d98-907a-0163f79aee8d">SQLInstallDriverManager</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>