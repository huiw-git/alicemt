---
title: SQLManageDataSources
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
  - SQLManageDataSources
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLManageDataSources
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
          <legacyBold>SQLManageDataSources</legacyBold> displays a dialog box with which users can set up, add, and delete data sources in the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLManageDataSources</legacyBold>(
     HWND     <parameterReference>hwnd</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwnd</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>
        <legacyBold>SQLManageDataSources</legacyBold> returns FALSE if <legacyItalic>hwnd</legacyItalic> is not a valid window handle. Otherwise, it returns TRUE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLManageDataSources</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Request</legacyItalic> failed</para>
            </TD>
            <TD>
              <para>The call to <legacyBold>ConfigDSN</legacyBold> failed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID__HWND</para>
            </TD>
            <TD>
              <para>Invalid window handle</para>
            </TD>
            <TD>
              <para>The <legacyItalic>hwnd</legacyItalic> argument was invalid or NULL.</para>
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
    <title>Managing Data Sources</title>
    <content>
      <para>
        <legacyBold>SQLManageDataSources</legacyBold> initially displays the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="de55dfc0-6e2f-40d8-9622-ce9cbc4a94e6" />
      </mediaLink>
      <para>The dialog box displays the data sources listed in the system information under three tabs: <legacyBold>User DSN</legacyBold>, <legacyBold>System DSN</legacyBold>, and <legacyBold>File DSN</legacyBold>. If the user double-clicks a data source or selects a data source and clicks <legacyBold>Configure</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> calls <legacyBold>ConfigDSN</legacyBold> in the setup DLL with the ODBC_CONFIG_DSN option.</para>
      <para>If the user clicks <legacyBold>Add</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> displays the <legacyBold>Create New Data Source</legacyBold> dialog box, shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="6dc1fad7-a692-42ba-b868-a0117eeeaea2" />
      </mediaLink>
      <para>The dialog box displays a list of installed drivers. If the user double-clicks a driver or selects a driver and clicks <legacyBold>OK</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> calls <legacyBold>ConfigDSN</legacyBold> in the setup DLL and passes it the ODBC_ADD_DSN option.</para>
      <para>If the user selects a data source and clicks <legacyBold>Remove</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> asks whether the user wants to delete the data source. If the user clicks <legacyBold>Yes</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> calls <legacyBold>ConfigDSN</legacyBold> in the setup DLL with the ODBC_REMOVE_DSN option.</para>
      <para>The <legacyBold>Create New Data Source</legacyBold> dialog box is used to add or delete a user data source, a system data source, or a file data source.</para>
    </content>
  </section>
  <section>
    <title>User DSNs</title>
    <content>
      <para>DSNs created for individual users will be called User DSNs, to distinguish them from System DSNs. User DSNs are registered as follows in the system information:</para>
      <para>
        <codeInline>HKEY_CURRENT_USERS</codeInline> </para>
      <para>
        <codeInline>   SOFTWARE</codeInline> </para>
      <para>
        <codeInline>      ODBC</codeInline>
      </para>
      <para>
        <codeInline>         Odbc.ini</codeInline>
      </para>
    </content>
  </section>
  <section>
    <title>System DSNs</title>
    <content>
      <para>The <legacyBold>Create New Data Source</legacyBold> dialog box allows you to add a system data source to your local computer or delete one, or to set the configuration for a system data source.</para>
      <para>A data source set up with a system data source name (DSN) can be used by more than one user on the same machine. It can also be used by a systemwide service, which can then gain access to the data source even if no user is logged on to the machine.</para>
      <para>A System DSN is registered in the HKEY_LOCAL_MACHINE entry in the system information rather than in the HKEY_CURRENT_USER entry. It is not tied to one user who logs on with his or her particular user name and password but can be used by any user of that machine or by an automatic systemwide service. The System DSN is, however, tied to one machine. It does not support the capability of using remote DSNs between machines. System DSNs are registered as follows in the system information:</para>
      <para> HKEY_LOCAL_MACHINE    SOFTWARE       ODBC          Odbc.ini</para>
    </content>
  </section>
  <section>
    <title>File DSNs</title>
    <content>
      <para>A file data source does not have a data source name, as does a machine data source, and is not registered to any one user or machine. The connection information for that data source is contained in a .dsn file that can be copied to any machine. A file data source can be shareable, in which case the .dsn file resides on a network and can be used simultaneously by multiple users on the network as long as the user has the appropriate driver installed. A file data source can also be unshareable, in which case it can be used only on a single machine.</para>
      <para>For more information on file data sources, see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>, or see <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Managing Drivers</title>
    <content>
      <para>If the user clicks the <legacyBold>Drivers</legacyBold> tab in the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box, <legacyBold>SQLManageDataSources</legacyBold> displays a list of ODBC drivers installed on the system, as well as information about the drivers. The date displayed is the creation date of the driver, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="93b4afca-9ebe-4439-909b-b09e3034e834" />
      </mediaLink>
    </content>
  </section>
  <section>
    <title>Tracing Options</title>
    <content>
      <para>If the user clicks the <legacyBold>Tracing</legacyBold> tab in the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box, <legacyBold>SQLManageDataSources</legacyBold> displays tracing options, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="3c698745-d4c8-4763-8df3-8a6937053e8a" />
      </mediaLink>
      <para>If the user clicks <legacyBold>Start Tracing Now</legacyBold> and then clicks <legacyBold>OK</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> enables tracing manually for all applications currently running on the machine.</para>
      <para>If the user specifies the name of a trace file in the <legacyBold>Log file Path</legacyBold> text box and then clicks <legacyBold>OK</legacyBold>, <legacyBold>SQLManageDataSources</legacyBold> sets the <legacyBold>TraceFile</legacyBold> keyword in the [ODBC] section of the system information to the specified name.</para>
      <alert class="important">
        <para>Support for Visual Studio Analyzer was removed beginning in Windows 8 (Visual Studio Analyzer was only included in older versions of Visual Studio.). For an alternative troubleshooting mechanism, use BID tracing.</para>
      </alert>
      <para>If the user clicks <legacyBold>Start Visual Studio Analyzer</legacyBold> and then clicks <legacyBold>OK</legacyBold>, Visual Studio Analyzer is enabled. It remains enabled until <legacyBold>Stop Visual Studio Analyzer</legacyBold> is clicked.</para>
      <para>For more information on tracing, see <legacyLink xlink:href="77ed4c6c-d976-4eb2-8526-a12697b0ef83">Tracing</legacyLink>. For more information about the <legacyBold>Trace</legacyBold> and <legacyBold>TraceFile</legacyBold> keywords, see <legacyLink xlink:href="f9534144-8f42-4946-b0fb-638e9dcde9c8">ODBC Subkey</legacyLink>.</para>
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
              <para>Creating data sources</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="76ee851a-dca9-40cc-8e9e-eb3f74e560ee">SQLCreateDataSource</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>