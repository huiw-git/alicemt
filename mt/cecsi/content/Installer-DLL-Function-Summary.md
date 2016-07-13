---
title: Installer DLL Function Summary
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Installer DLL Function Summary
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table describes the functions in the installer DLL. For more information about the syntax and semantics for each function, see <legacyLink xlink:href="47fcadc3-f102-4989-9ee7-a1c65233142a">Installer DLL API Reference</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Task</para>
          </TD>
          <TD>
            <para>Function name</para>
          </TD>
          <TD>
            <para>Purpose</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Installing ODBC</para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="4f681961-ac9f-4d88-b065-5258ba112642">SQLConfigDriver</legacyLink>             </para>
          </TD>
          <TD>
            <para>Loads the driver-specific setup DLL.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="a1983a2e-0edf-422e-bd1b-ec5db40a34bc">SQLGetInstalledDrivers</legacyLink>             </para>
          </TD>
          <TD>
            <para>Returns a list of installed drivers.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx</legacyLink>             </para>
          </TD>
          <TD>
            <para>Adds a driver to the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="aebc439b-fffd-4d98-907a-0163f79aee8d">SQLInstallDriverManager</legacyLink>             </para>
          </TD>
          <TD>
            <para>Returns the target directory for the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="e6474b79-4d55-458f-81ce-abfafe357f83">SQLInstallerError</legacyLink>             </para>
          </TD>
          <TD>
            <para>Returns error or status information for the installer functions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx</legacyLink>             </para>
          </TD>
          <TD>
            <para>Adds a translator to the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="4c60d827-b2d2-4f27-b220-daa9e1fcdd8d">SQLPostInstallerError</legacyLink>             </para>
          </TD>
          <TD>
            <para>Allows a driver or translator setup library to report errors.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="9a3b4f8b-982b-44b9-ade6-754ff026dc90">SQLRemoveDriver</legacyLink>             </para>
          </TD>
          <TD>
            <para>Removes a driver from the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="3a41511f-6603-4b81-a815-7883874023c4">SQLRemoveDriverManager</legacyLink>             </para>
          </TD>
          <TD>
            <para>Removes ODBC core components from the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c6feda49-0359-4224-8de9-77125cf2397b">SQLRemoveTranslator</legacyLink>             </para>
          </TD>
          <TD>
            <para>Removes the translator from the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Configuring data sources</para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource</legacyLink>             </para>
          </TD>
          <TD>
            <para>Calls the driver-specific setup DLL.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="76ee851a-dca9-40cc-8e9e-eb3f74e560ee">SQLCreateDataSource</legacyLink>             </para>
          </TD>
          <TD>
            <para>Displays a dialog box to add a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="b96ab3b8-08d5-4fea-9ffe-e03043efbf2d">SQLGetConfigMode</legacyLink>             </para>
          </TD>
          <TD>
            <para>Retrieves the configuration mode that indicates where the Odbc.ini entry listing DSN values is in the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="b72ca065-4d67-48df-baac-e18379a8320a">SQLGetPrivateProfileString</legacyLink>             </para>
          </TD>
          <TD>
            <para>Writes a value to the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="33879db3-5ef9-4585-9be5-69376157e017">SQLGetTranslator</legacyLink>             </para>
          </TD>
          <TD>
            <para>Displays a dialog box to select a translator.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="ac6d186f-b394-406c-94c4-c6331d1ca468">SQLManageDataSources</legacyLink>             </para>
          </TD>
          <TD>
            <para>Displays a dialog box to configure data sources and drivers.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="ead464aa-cdc3-47dd-a0c0-997711205d31">SQLReadFileDSN</legacyLink>             </para>
          </TD>
          <TD>
            <para>Reads information from file DSNs.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="db803266-57df-4864-a41b-901247549c1f">SQLRemoveDefaultDataSource</legacyLink>             </para>
          </TD>
          <TD>
            <para>Removes the default data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="bb2e8273-7b61-4113-bfc8-f7ccc607c811">SQLRemoveDSNFromIni</legacyLink>             </para>
          </TD>
          <TD>
            <para>Removes a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="09eb88ea-b6f6-4eca-b19d-0951cebc6c0a">SQLSetConfigMode</legacyLink>             </para>
          </TD>
          <TD>
            <para>Sets the configuration mode that indicates where the Odbc.ini entry listing DSN values is in the system information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="930d1d89-337a-4429-85a2-84ee10555ac9">SQLValidDSN</legacyLink>             </para>
          </TD>
          <TD>
            <para>Checks the length and validity of the data source name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="dc7018b2-18d4-4657-96d0-086479a47474">SQLWriteDSNToIni</legacyLink>             </para>
          </TD>
          <TD>
            <para>Adds a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="9e18f56f-1061-416b-83d4-ffeec42ab5a9">SQLWriteFileDSN</legacyLink>             </para>
          </TD>
          <TD>
            <para>Writes information to file DSNs.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="526f36a4-92ed-4874-9725-82d27c0b86f9">SQLWritePrivateProfileString</legacyLink>             </para>
          </TD>
          <TD>
            <para>Gets a value from the system information.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>