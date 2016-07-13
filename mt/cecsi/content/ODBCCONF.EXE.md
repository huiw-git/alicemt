---
title: ODBCCONF.EXE
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBCCONF.EXE
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBCCONF.exe is a command-line tool that allows you to configure ODBC drivers and data source names.</para>
    <alert class="note">
      <para>ODBCCONF.exe will be removed in a future version of Windows Data Access Components. Avoid using this feature, and plan to modify applications that currently use this feature. You can use PowerShell commands to manage drivers and data sources. For more information about these PowerShell commands, see <externalLink><linkText>Windows Data Access Components cmdlets</linkText><linkUri>https://technet.microsoft.com/library/hh771019.aspx</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
ODBCCONF [<parameterReference>switches</parameterReference>] <parameterReference>action</parameterReference></legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>switches</parameterReference>
        </definedTerm>
        <definition>
          <para>Zero or more switch options. For the list of available switches, see the Remarks section, later in this topic.</para>
        </definition>
        <definedTerm>
          <parameterReference>action</parameterReference>
        </definedTerm>
        <definition>
          <para>One action to perform. For the list of available options, see the Remarks section.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The following switches are available:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Switch</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>/A {<parameterReference>action</parameterReference>}</para>
            </TD>
            <TD>
              <para>Specify an action. </para>
              <para>/A is optional if only one action is specified.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/?</para>
            </TD>
            <TD>
              <para>Display usage for ODBCCONF.EXE.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/C</para>
            </TD>
            <TD>
              <para>Processing continues if an action fails.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/E</para>
            </TD>
            <TD>
              <para>Erase the response file specified with /F when processing is finished.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/F</para>
            </TD>
            <TD>
              <para>Use a response file, such as <codeInline>odbcconf /F my.rsp</codeInline>.</para>
              <para>my.rsp might look like this:</para>
              <code>REGSVR c:\my.dll</code>
              <para>/A is not used in a response file.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/H</para>
            </TD>
            <TD>
              <para>Display usage (Help). This switch is the same as /?.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/L[<parameterReference>mode</parameterReference>] <parameterReference>filename</parameterReference></para>
            </TD>
            <TD>
              <para>Send program output to a file in one of three modes: normal (n), verbose (v), and debug (d). Debug mode records the DLLs that are loaded by odbcconf.exe.</para>
              <para>If you specify /L without a mode, the log file will be empty.</para>
              <para>For example, <languageKeyword>/Lv log.txt</languageKeyword>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/R</para>
            </TD>
            <TD>
              <para>The action will be performed after a reboot.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>/S</para>
            </TD>
            <TD>
              <para>Silent mode. Do not display error messages.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following actions are available:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Action</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CONFIGDRIVER <parameterReference>driver_name</parameterReference> <parameterReference>driver-specific configuration params</parameterReference></para>
            </TD>
            <TD>
              <para>Loads the appropriate driver setup DLL and calls the <legacyBold>ConfigDriver</legacyBold> function.</para>
              <para>Equivalent to the <legacyLink xlink:href="4f681961-ac9f-4d88-b065-5258ba112642">SQLConfigDriver function</legacyLink>.</para>
              <para>For example:</para>
              <code>/A {CONFIGDRIVER " Driver Name" "CPTimeout=60"}
/A {CONFIGDRIVER " Driver Name" "DriverODBCVer=03.80"}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CONFIGDSN <parameterReference>driver_name</parameterReference> DSN=<parameterReference>name</parameterReference>|<parameterReference>attributes</parameterReference></para>
            </TD>
            <TD>
              <para>Adds or modifies a system data source.</para>
              <para>Equivalent to the <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource function</legacyLink>.</para>
              <para>For example:</para>
              <code>/A {CONFIGDSN "SQL Server" "DSN=name|Server=srv"}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CONFIGSYSDSN <parameterReference>driver_name</parameterReference> DSN=<parameterReference>name</parameterReference>|<parameterReference>attributes</parameterReference></para>
            </TD>
            <TD>
              <para>Adds or modifies a system data source.</para>
              <para>Equivalent to the <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource function</legacyLink>.</para>
              <para>For example:</para>
              <code>/A {CONFIGSYSDSN "SQL Server" "DSN=name|Server=srv"}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INSTALLDRIVER</para>
            </TD>
            <TD>
              <para>Equivalent to <link xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx</link>.</para>
              <para>For information about the keyword-value pairs syntax passed to INSTALLDRIVER, see <link xlink:href="b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80">Driver Specification Subkeys</link>.</para>
              <para>For example:</para>
              <code>/A {INSTALLDRIVER  "Your Driver|Driver=c:\your.dll|Setup=c:\your.dll|APILevel=2|ConnectFunctions=YYY|DriverODBCVer=03.50|FileUsage=0|SQLLevel=1"}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INSTALLTRANSLATOR <parameterReference>translator configuration</parameterReference> <parameterReference>driver path</parameterReference></para>
            </TD>
            <TD>
              <para>Adds information about a translator to the <system>HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.INI\ODBC Translators</system> registry key.</para>
              <para>Equivalent to <link xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx Function</link>.</para>
              <para>For information about the keyword-value pairs syntax passed to INSTALLDRIVER, see <link xlink:href="3c0edeee-d43a-4466-a177-bf2d2435707a">Translator Specification Subkeys</link>.</para>
              <para>For example:</para>
              <code>/A {INSTALLTRANSLATOR  "My Translator|Translator=c:\my.dll|Setup=c:\my.dll"}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REGSVR <parameterReference>dll</parameterReference></para>
            </TD>
            <TD>
              <para>Registers a DLL.</para>
              <para>Equivalent to regsvr32.exe.</para>
              <para>For example:</para>
              <code>/A {REGSVR c:\my.dll}</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SETFILEDSNDIR</para>
            </TD>
            <TD>
              <para>When HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC.INI\ODBC File DSN\DefaultDSNDir does not exist, the SETFILEDSNDIR action will create it and assign it the value at HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, appended with \ODBC\Data Sources.</para>
              <para>The value at HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC.INI\ODBC File DSN\DefaultDSNDir specifies the default location used by the ODBC Data Source Administrator when creating a file-based data source.</para>
              <para>For example:</para>
              <code>/A {SETFILEDSNDIR}</code>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="278cf36e-9817-4ee3-842e-dbd149f15273">Microsoft Open Database Connectivity (ODBC)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>