---
title: SQLInstallDriverManager Function
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
  - SQLInstallDriverManager
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallDriverManager Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0: Deprecated in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1, and later operating systems</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLInstallDriverManager</legacyBold> returns the path of the target directory for the installation of the ODBC core components. The calling program must actually copy the Driver Manager's files to the target directory.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLInstallDriverManager</legacyBold>(
     LPSTR    <parameterReference>lpszPath</parameterReference>,
     WORD     <parameterReference>cbPathMax</parameterReference>,
     WORD *   <parameterReference>pcbPathOut</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszPath</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Path of the target directory of the installation.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbPathMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszPath</legacyItalic>. This must be at least _MAX_PATH bytes.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes (excluding the null-termination byte) returned in <legacyItalic>lpszPath</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbPathMax</legacyItalic>, the path in <legacyItalic>lpszPath</legacyItalic> is truncated to <legacyItalic>cbPathMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbPathOut</legacyItalic> argument can be a null pointer.</para>
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
      <para>When <legacyBold>SQLInstallDriverManager</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The <legacyItalic>lpszPath</legacyItalic> argument was not large enough to contain the output path. The buffer contains the truncated path.</para>
              <para>The <legacyItalic>cbPathMax</legacyItalic> argument was less than _MAX_PATH.</para>
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
              <para>The installer failed to increment the ODBC core component usage count.</para>
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
        <legacyBold>SQLInstallDriverManager</legacyBold> is called to return the path for ODBC core components and increment the component usage count in the system information. If a version of the Driver Manager already exists but the component usage count for the driver does not exist, the new component usage count value is set to 2.</para>
      <para>The application setup program is responsible for physically copying the core component files and maintaining the file usage counts. If a core component file has not previously been installed, the application setup program must copy the file, and create the file usage count. If the file has previously been installed, the setup program merely increments the file usage count.</para>
      <para>If an older version of the Driver Manager was previously installed by the application setup program, the core components should be uninstalled and then reinstalled, so that the core component usage count is valid. <legacyBold>SQLRemoveDriverManager</legacyBold> should first be called to decrement the component usage count. <legacyBold>SQLInstallDriverManager</legacyBold> should then be called to increment the component usage count. The application setup program must replace the old core component files with the new files. The file usage counts will remain the same, and other applications that used the older version core component files will now use the newer version files.</para>
      <para>In a fresh install of the ODBC core components, drivers, and translators, the application setup program should call the following functions in sequence: <legacyBold>SQLInstallDriverManager</legacyBold>, <legacyBold>SQLInstallDriverEx</legacyBold>, <legacyBold>SQLConfigDriver</legacyBold> (with an <legacyItalic>fRequest</legacyItalic> of ODBC_INSTALL_DRIVER), and then <legacyBold>SQLInstallTranslatorEx</legacyBold>. In an uninstall of the core components, drivers, and translators, the application setup program should call the following functions in sequence: <legacyBold>SQLRemoveTranslator</legacyBold>, <legacyBold>SQLRemoveDriver</legacyBold>, and then <legacyBold>SQLRemoveDriverManager</legacyBold>. These functions must be called in this sequence. In an upgrade of all components, all the uninstall functions should be called in sequence and then all the install functions should be called in sequence.</para>
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
                <legacyLink xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx</legacyLink>
              </para>
            </TD>
          </tr>
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
          <tr>
            <TD>
              <para>Removing a driver</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a3b4f8b-982b-44b9-ade6-754ff026dc90">SQLRemoveDriver</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing the Driver Manager</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3a41511f-6603-4b81-a815-7883874023c4">SQLRemoveDriverManager</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing a translator</para>
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