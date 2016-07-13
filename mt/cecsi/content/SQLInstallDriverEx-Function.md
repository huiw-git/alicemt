---
title: SQLInstallDriverEx Function
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
  - SQLInstallDriverEx
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallDriverEx Function
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
          <legacyBold>SQLInstallDriverEx</legacyBold> adds information about the driver to the Odbcinst.ini entry in the system information and increments the driver's <legacyItalic>UsageCount</legacyItalic> by 1. However, if a version of the driver already exists but the <legacyItalic>UsageCount</legacyItalic> value for the driver does not exist, the new <legacyItalic>UsageCount</legacyItalic> value is set to 2.</para>
        <para>This function does not actually copy any files. It is the responsibility of the calling program to copy the driver's files to the target directory properly.</para>
        <para>The functionality of <legacyBold>SQLInstallDriverEx</legacyBold> can also be accessed with <link xlink:href="3bf2be83-61f9-4183-836b-85204ac7116a">ODBCCONF.EXE</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLInstallDriverEx</legacyBold>(
     LPCSTR    <parameterReference>lpszDriver</parameterReference>,
     LPCSTR    <parameterReference>lpszPathIn</parameterReference>,
     LPSTR     <parameterReference>lpszPathOut</parameterReference>,
     WORD      <parameterReference>cbPathOutMax</parameterReference>,
     WORD *    <parameterReference>pcbPathOut,</parameterReference>
     WORD      <parameterReference>fRequest,</parameterReference>
     LPDWORD   <parameterReference>lpdwUsageCount</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The driver description (usually the name of the associated DBMS) presented to users instead of the physical driver name. The <legacyItalic>lpszDriver</legacyItalic> argument must contain a doubly null-terminated list of keyword-value pairs describing the driver. For more information about keyword-value pairs, see <link xlink:href="b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80">Driver Specification Subkeys</link>. For more information about the doubly null-terminated string, see <link xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</link>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszPathIn</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Full path of the target directory of the installation, or a null pointer. If <legacyItalic>lpszPathIn</legacyItalic> is a null pointer, the drivers will be installed in the system directory.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Path of the target directory where the driver should be installed. If the driver has not previously been installed, <legacyItalic>lpszPathOut</legacyItalic> should be the same as <legacyItalic>lpszPathIn</legacyItalic>. If the driver was previously installed, <legacyItalic>lpszPathOut</legacyItalic> is the path of the previous installation.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbPathOutMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszPathOut</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbPathOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes (excluding the null-termination character) available to return in <legacyItalic>lpszPathOut</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbPathOutMax</legacyItalic>, the output path in <legacyItalic>lpszPathOut</legacyItalic> is truncated to <legacyItalic>cbPathOutMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbPathOut</legacyItalic> argument can be a null pointer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of request. The <legacyItalic>fRequest</legacyItalic> argument must contain one of the following values:</para>
          <para>ODBC_INSTALL_INQUIRY: Inquire about where a driver can be installed.   </para>
          <para>ODBC_INSTALL_COMPLETE: Complete the installation request. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpdwUsageCount</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] The usage count of the driver after this function has been called.</para>
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
      <para>When <legacyBold>SQLInstallDriverEx</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The <legacyItalic>cbPathOutMax</legacyItalic> argument was 0, and <legacyItalic>fRequest</legacyItalic> was ODBC_INSTALL_COMPLETE.</para>
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
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument contained a syntax error.</para>
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
              <para>ODBC_ERROR_LOAD_LIBRARY_FAILED</para>
            </TD>
            <TD>
              <para>Could not load the driver or translator  setup library</para>
            </TD>
            <TD>
              <para>The driver setup library could not be loaded.</para>
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
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument did not contain a list of keyword-value pairs.</para>
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
              <para>The installer failed to increment the driver's usage count.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The <legacyItalic>lpszDriver</legacyItalic> argument is a list of attributes in the form of keyword-value pairs. Each pair is terminated with a null byte, and the entire list is terminated with a null byte. (That is, two null bytes mark the end of the list.) The format of this list is as follows:</para>
      <para>
        <legacyItalic>driver-desc</legacyItalic>
        <legacyBold>\</legacyBold>0Driver<legacyBold>=</legacyBold><legacyItalic>driver-DLL-filename</legacyItalic><legacyBold>\</legacyBold>0[Setup<legacyBold>=</legacyBold><legacyItalic>setup-DLL-filename</legacyItalic><legacyBold>\</legacyBold>0]</para>
      <para>[<legacyItalic>driver-attr-keyword1</legacyItalic><legacyBold>=</legacyBold><legacyItalic>value1</legacyItalic><legacyBold>\</legacyBold>0][<legacyItalic>driver-attr-keyword2</legacyItalic><legacyBold>=</legacyBold><legacyItalic>value2</legacyItalic><legacyBold>\</legacyBold>0]...<legacyBold>\</legacyBold>0</para>
      <para>where \0 is a null byte and <legacyItalic>driver-attr-keywordn</legacyItalic> is any driver attribute keyword. The keywords must appear in the specified order. For example, suppose a driver for formatted text files has separate driver and setup DLLs and can use files with the .txt and .csv extensions. The <legacyItalic>lpszDriver</legacyItalic> argument for this driver might be as follows:</para>
      <code>Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0
FileExtns=*.txt,*.csv\0\0</code>
      <para>Suppose that a driver for SQL Server does not have a separate setup DLL and does not have any driver attribute keywords. The <legacyItalic>lpszDriver</legacyItalic> argument for this driver might be as follows:</para>
      <code>SQL Server\0Driver=SQLSRVR.DLL\0\0</code>
      <para>After <legacyBold>SQLInstallDriverEx</legacyBold> retrieves information about the driver from the <legacyItalic>lpszDriver</legacyItalic> argument, it adds the driver description to the [ODBC Drivers] section of the Odbcinst.ini entry in the system information. It then creates a section titled with the driver's description and adds the full paths of the driver DLL and the setup DLL. Finally, it returns the path of the target directory of the installation but does not copy the driver files to it. The calling program must actually copy the driver files to the target directory.</para>
      <para>
        <legacyBold>SQLInstallDriverEx</legacyBold> increments the component usage count for the installed driver by 1. If a version of the driver already exists but the component usage count for the driver does not exist, the new component usage count value is set to 2.</para>
      <para>The application setup program is responsible for physically copying the driver file and maintaining the file usage count. If the driver file has not previously been installed, the application setup program must copy the file in the <legacyItalic>lpszPathIn</legacyItalic> path and create the file usage count. If the file has previously been installed, the setup program merely increments the file usage count and returns the path of the prior installation in the <legacyItalic>lpszPathOut</legacyItalic> argument.</para>
      <alert class="note">
        <para>For more information about component usage counts and file usage counts, see <legacyLink xlink:href="0678aee9-8256-463c-89dd-77b1a0dfdd60">Usage Counting</legacyLink>.</para>
      </alert>
      <para>If an older version of the driver file was previously installed by the application, the driver should be uninstalled and then reinstalled, so that the driver component usage count is valid. <legacyBold>SQLConfigDriver</legacyBold> (with an <legacyItalic>fRequest</legacyItalic> of ODBC_REMOVE_DRIVER) should first be called, and then <legacyBold>SQLRemoveDriver</legacyBold> should be called to decrement the component usage count. <legacyBold>SQLInstallDriverEx</legacyBold> should then be called to reinstall the driver, incrementing the component usage count. The application setup program must replace the old file with the new file. The file usage count will remain the same, and any other application that used the older version file will now use the newer version.</para>
      <alert class="note">
        <para>If the driver was previously installed and <legacyBold>SQLInstallDriverEx</legacyBold> is called to install the driver in a different directory, the function will return TRUE, but <legacyItalic>lpszPathOut</legacyItalic> will include the directory where the driver was already installed. It will not include the directory entered in the <legacyItalic>lpszDriver</legacyItalic> argument.</para>
      </alert>
      <para>The length of the path in <legacyItalic>lpszPathOut</legacyItalic> in <legacyBold>SQLInstallDriverEx</legacyBold> allows for a two-phase install process, so an application can determine what <legacyItalic>cbPathOutMax</legacyItalic> should be by calling <legacyBold>SQLInstallDriverEx</legacyBold> with an <legacyItalic>fRequest</legacyItalic> of ODBC_INSTALL_INQUIRY mode. This will return the total number of bytes available in the <legacyItalic>pcbPathOut</legacyItalic> buffer. <legacyBold>SQLInstallDriverEx</legacyBold> can then be called with an <legacyItalic>fRequest</legacyItalic> of ODBC_INSTALL_COMPLETE and the <legacyItalic>cbPathOutMax</legacyItalic> argument set to the value in the <legacyItalic>pcbPathOut</legacyItalic> buffer, plus the null-termination character.</para>
      <para>If you choose not to use the two-phase model for <legacyBold>SQLInstallDriverEx</legacyBold>, you must set <legacyItalic>cbPathOutMax</legacyItalic>, which defines the size of the storage for the path of the target directory, to the value _MAX_PATH, as defined in Stdlib.h, to prevent truncation.</para>
      <para>When <legacyItalic>fRequest</legacyItalic> is ODBC_INSTALL_COMPLETE, <legacyBold>SQLInstallDriverEx</legacyBold> does not allow <legacyItalic>lpszPathOut</legacyItalic> to be NULL (or <legacyItalic>cbPathOutMax</legacyItalic> to be 0). If <legacyItalic>fRequest</legacyItalic> is ODBC_INSTALL_COMPLETE, FALSE is returned when the number of bytes available to return is greater than or equal to <legacyItalic>cbPathOutMax</legacyItalic>, with the result that truncation occurs.</para>
      <para>After <legacyBold>SQLInstallDriverEx</legacyBold> has been called and the application setup program has copied the driver file (if necessary), the driver setup DLL must call <legacyBold>SQLConfigDriver</legacyBold> to set the configuration for the driver.</para>
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
              <para>Installing the Driver Manager</para>
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