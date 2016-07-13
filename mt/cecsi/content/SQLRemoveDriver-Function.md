---
title: SQLRemoveDriver Function
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
  - SQLRemoveDriver
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRemoveDriver Function
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
          <legacyBold>SQLRemoveDriver</legacyBold> changes or removes information about the driver from the Odbcinst.ini entry in the system information. </para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLRemoveDriver</legacyBold>(
     LPCSTR   <parameterReference>lpszDriver</parameterReference>,
     BOOL     <parameterReference>fRemoveDSN</parameterReference>,
     LPDWORD  <parameterReference>lpdwUsageCount</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The name of the driver as registered in the Odbcinst.ini key of the system information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRemoveDSN</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The valid values are:</para>
          <para>TRUE: Remove DSNs associated with the driver specified in <legacyItalic>lpszDriver</legacyItalic>. FALSE: Do not remove DSNs associated with the driver specified in <legacyItalic>lpszDriver</legacyItalic>. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpdwUsageCount</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The usage count of the driver after this function has been called.</para>
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
      <para>When <legacyBold>SQLRemoveDriver</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The installer could not remove the driver information because it either did not exist in the registry or could not be found in the registry.</para>
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
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument was invalid.</para>
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
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>Request failed</para>
            </TD>
            <TD>
              <para>The <legacyItalic>fRemoveDSN</legacyItalic> argument was TRUE; however, one or more DSNs could not be removed. The call to <legacyBold>SQLConfigDriver</legacyBold> with the ODBC_REMOVE_DRIVER request failed.</para>
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
        <legacyBold>SQLRemoveDriver</legacyBold> complements the <legacyLink xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx</legacyLink> function and updates the component usage count in the system information. This function should be called only from a setup application.</para>
      <para>
        <legacyBold>SQLRemoveDriver</legacyBold> will decrement the component usage count value by 1. If the component usage count goes to 0, the following will occur:  </para>
      <list class="ordered">
        <listItem>
          <para>The<legacyBold> SQLConfigDriver</legacyBold> function with the ODBC_REMOVE_DRIVER option will be called. If the <legacyItalic>fRemoveDSN</legacyItalic> option is set to TRUE, the <legacyBold>ConfigDSN</legacyBold> function calls <legacyBold>SQLRemoveDSNFromIni </legacyBold>to remove all the data sources associated with the driver specified in <legacyItalic>lpszDriver.</legacyItalic> If the <legacyItalic>fRemoveDSN</legacyItalic> option is set to FALSE, the data sources will not be deleted.</para>
        </listItem>
        <listItem>
          <para>The driver entry in the system information will be removed. The driver entry is in the following system information location, under the driver name: </para>
          <para>
            <codeInline>HKEY_LOCAL_MACHINE</codeInline> </para>
          <para>
            <codeInline>   SOFTWARE</codeInline> </para>
          <para>
            <codeInline>      ODBC</codeInline>
          </para>
          <para>
            <codeInline>         Odbcinst.ini</codeInline>
          </para>
        </listItem>
      </list>
      <para>
        <legacyBold>SQLRemoveDriver</legacyBold> does not actually remove any files. The calling program is responsible for deleting files and maintaining the file usage count. Only after both the component usage count and the file usage count have reached zero is a file physically deleted. Some files in a component can be deleted, and others not deleted, depending on whether the files are used by other applications that have incremented the file usage count.</para>
      <para>
        <legacyBold>SQLRemoveDriver</legacyBold> is also called as part of an upgrade process. If an application detects that it has to perform an upgrade and it has previously installed the driver, the driver should be removed and then reinstalled. <legacyBold>SQLRemoveDriver</legacyBold> should first be called to decrement the component usage count, and then <legacyBold>SQLInstallDriverEx</legacyBold> should be called to increment the component usage count. The application setup program must replace the old files with the new files. The file usage count will remain the same, and other applications that use the older version files will now use the newer version.</para>
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
                <legacyLink xlink:href="9473f48f-bcae-4784-89c1-7839bad4ed13">ConfigDriver</legacyLink> (in the Setup DLL)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Adding, modifying, or removing a driver</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4f681961-ac9f-4d88-b065-5258ba112642">SQLConfigDriver</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Installing a driver</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx</legacyLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>