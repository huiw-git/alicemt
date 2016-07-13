---
title: Driver Specification Subkeys
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Specification Subkeys
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each driver listed in the ODBC Drivers subkey has a subkey of its own. This subkey has the same name as the corresponding value under the ODBC Drivers subkey. The values under this subkey list the full paths of the driver and driver setup DLLs, the values of the driver keywords returned by <legacyBold>SQLDrivers</legacyBold>, and the usage count. The formats of the values are as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>APILevel</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyBold>0 </legacyBold>|<legacyBold> 1 </legacyBold>|<legacyBold> 2</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ConnectFunctions</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>{<legacyBold>Y</legacyBold>|<legacyBold>N</legacyBold>}{<legacyBold>Y</legacyBold>|<legacyBold>N</legacyBold>}{<legacyBold>Y</legacyBold>|<legacyBold>N</legacyBold>}</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CreateDSN</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>driver-description</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Driver</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>driver-DLL-path</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DriverODBCVer</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>nn.nn</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FileExtns</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyBold>*.</legacyBold> <legacyItalic>file-extension1</legacyItalic>[<legacyBold>,*.</legacyBold> <legacyItalic>file-extension2</legacyItalic>]...</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FileUsage</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyBold>0 </legacyBold>|<legacyBold> 1 </legacyBold>|<legacyBold> 2</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Setup</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>setup-DLL-path</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQLLevel</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyBold>0 </legacyBold>|<legacyBold> 1 </legacyBold>|<legacyBold> 2</legacyBold></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UsageCount</para>
          </TD>
          <TD>
            <para>REG_DWORD</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>count</legacyItalic>
            </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The use of each keyword is shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Keyword</para>
          </TD>
          <TD>
            <para>Usage</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>APILevel</legacyBold>
            </para>
          </TD>
          <TD>
            <para>A number indicating the ODBC interface conformance level supported by the driver:</para>
            <para>0 = None</para>
            <para>1 = Level 1 supported</para>
            <para>2 = Level 2 supported</para>
            <para>This must be the same as the value returned for the SQL_ODBC_INTERFACE_CONFORMANCE option in <legacyBold>SQLGetInfo</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>CreateDSN</legacyBold>
            </para>
          </TD>
          <TD>
            <para>The name of one or more data sources to be created when the driver is installed. The system information must include one data source specification section for each data source listed with the <legacyBold>CreateDSN</legacyBold> keyword. These sections should not include the <legacyBold>Driver</legacyBold> keyword, because this is specified in the driver specification section, but must include enough information for the <legacyBold>ConfigDSN</legacyBold> function in the driver setup DLL to create a data source specification without displaying any dialog boxes. For the format of a data source specification section, see <legacyLink xlink:href="d7e88a07-e6ab-4258-a45d-1ca21234fbec">Data Source Specification Subkeys</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>ConnectFunctions</legacyBold>
            </para>
          </TD>
          <TD>
            <para>A three-character string indicating whether the driver supports <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, and <legacyBold>SQLBrowseConnect</legacyBold>. If the driver supports <legacyBold>SQLConnect</legacyBold>, the first character is "Y"; otherwise, it is "N". If the driver supports <legacyBold>SQLDriverConnect</legacyBold>, the second character is "Y"; otherwise, it is "N". If the driver supports <legacyBold>SQLBrowseConnect</legacyBold>, the third character is "Y"; otherwise, it is "N". For example, if a driver supports <legacyBold>SQLConnect</legacyBold> and <legacyBold>SQLDriverConnect</legacyBold> but not <legacyBold>SQLBrowseConnect</legacyBold>, the three-character string is "YYN".</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>DriverODBCVer</legacyBold>
            </para>
          </TD>
          <TD>
            <para>A character string with the version of ODBC that the driver supports. The version is of the form <legacyItalic>nn.nn</legacyItalic>, where the first two digits are the major version and the next two digits are the minor version. For the version of ODBC described in this manual, the driver must return "03.00".</para>
            <para>This must be the same as the value returned for the SQL_DRIVER_ODBC_VER option in <legacyBold>SQLGetInfo</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>FileExtns</legacyBold>
            </para>
          </TD>
          <TD>
            <para>For file-based drivers, a comma-separated list of extensions of the files the driver can use. For example, a dBASE driver might specify *.dbf and a formatted text file driver might specify *.txt,*.csv. For an example of how an application might use this information, see the <legacyBold>FileUsage</legacyBold> keyword.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>FileUsage</legacyBold>
            </para>
          </TD>
          <TD>
            <para>A number indicating how a file-based driver directly treats files in a data source.</para>
            <para>0 = The driver is not a file-based driver. For example, an ORACLE driver is a DBMS-based driver.</para>
            <para>1 = A file-based driver treats files in a data source as tables. For example, an Xbase driver treats each Xbase file as a table.</para>
            <para>2 = A file-based driver treats files in a data source as a catalog. For example, a Microsoft® Access driver treats each Microsoft Access file as a complete database.</para>
            <para>An application might use this to determine how users will select data. For example, Xbase and Paradox users often think of data as stored in files, while ORACLE and Microsoft Access users generally think of data as stored in tables.</para>
            <para>When a user selects <legacyBold>Open Data File</legacyBold> from the <legacyBold>File </legacyBold>menu, an application could display the <legacyBold>Windows File Open</legacyBold> common dialog box. The list of file types would use the file extensions specified with the <legacyBold>FileExtns</legacyBold> keyword for drivers that specify a <legacyBold>FileUsage</legacyBold> value of 1 and "Y" as the second character of the value of the <legacyBold>ConnectFunctions</legacyBold> keyword. After the user selects a file, the application would call <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>DRIVER</legacyBold> keyword and then execute a <legacyBold>SELECT * FROM</legacyBold> <legacyBold><legacyItalic>table-name</legacyItalic></legacyBold> statement.</para>
            <para>When the user selects <legacyBold>Import Data</legacyBold> from the <legacyBold>File </legacyBold>menu, an application could display a list of descriptions for drivers that specify a <legacyBold>FileUsage</legacyBold> value of 0 or 2, and "Y" as the second character of the value of the <legacyBold>ConnectFunctions</legacyBold> keyword. After the user selects a driver, the application would call <legacyBold>SQLDriverConnect</legacyBold> with the <legacyBold>DRIVER</legacyBold> keyword and then display a custom <legacyBold>Select Table</legacyBold> dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLLevel</legacyBold>
            </para>
          </TD>
          <TD>
            <para>A number indicating the SQL-92 grammar supported by the driver:</para>
            <para>0 = SQL-92 Entry</para>
            <para>1 = FIPS127-2 Transitional</para>
            <para>2 = SQL-92 Intermediate</para>
            <para>3 = SQL-92 Full</para>
            <para>This must be the same as the value returned for the SQL_SQL_CONFORMANCE option in <legacyBold>SQLGetInfo</legacyBold>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For information about usage counts, see <legacyLink xlink:href="0678aee9-8256-463c-89dd-77b1a0dfdd60">Usage Counting</legacyLink> earlier in this section.</para>
    <para>Applications should not set the usage count. ODBC will maintain this count.</para>
    <para>For example, suppose a driver for formatted text files has a driver DLL named Text.dll, a separate driver setup DLL named Txtsetup.dll, and has been installed three times. If the driver supports the Level 1 API conformance level, supports the Minimum SQL grammar conformance level, treats files as tables, and can use files with the .txt and .csv extensions, the values under the Text subkey might be as follows:</para>
    <code>APILevel : REG_SZ : 1
ConnectFunctions : REG_SZ : YYN
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\TEXT.DLL
DriverODBCVer : REG_SZ : 03.00.00
FileExtns : REG_SZ : *.txt,*.csv
FileUsage : REG_SZ : 1
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\TXTSETUP.DLL
SQLLevel : REG_SZ : 0
UsageCount : REG_DWORD : 0x3</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>