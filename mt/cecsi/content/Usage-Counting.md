---
title: Usage Counting
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Usage Counting
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>Two types of usage counts are maintained in the registry for each component: a component usage count and one or more optional file usage counts. The component usage count helps the installer DLL maintain registry entries. It is stored in the UsageCount value under the ODBC Core, driver, and translator subkeys. For the format of the UsageCount value and more information about these subkeys, see <legacyLink xlink:href="c90aa8a4-6ece-48de-901c-17d23739a9ff">Registry Entries for ODBC Components</legacyLink>.</para>
    <para>When a component is first installed, the installer DLL creates a subkey for it and sets the data for the UsageCount value in that subkey to 1. When the component is installed again, the installer DLL increments the usage count. When the component is removed, the installer DLL decrements the usage count. If the usage count falls to 0, the installer DLL removes the subkey for the component.</para>
    <alert class="caution">
      <para>An application should not physically remove Driver Manager files when the component usage count and the file usage count reach zero.</para>
    </alert>
    <para>File usage counts help determine when a file must actually be copied or deleted as opposed to incrementing or decrementing the usage count. This is important because ODBC components, and therefore the files in ODBC components, are shared and can be installed or removed by a variety of applications. The application can delete driver and translator files if the component usage count and the file usage count reach zero. Driver Manager files should not, however, be deleted when both the component usage count and the file usage count have reached zero, because these files can be used by other applications that have not incremented the file usage count.</para>
    <alert class="note">
      <para>File usage counts are optional in Microsoft® WindowsNT®/Windows2000.</para>
    </alert>
    <para>File usage counts are maintained by the setup program after it calls <legacyBold>SQLInstallDriverManager</legacyBold>, <legacyBold>SQLInstallDriverEx</legacyBold>, <legacyBold>SQLInstallTranslatorEx</legacyBold>, <legacyBold>SQLRemoveDriverManager</legacyBold>, <legacyBold>SQLRemoveDriver</legacyBold>, or <legacyBold>SQLRemoveTranslator</legacyBold>.</para>
    <para>When a component is first installed, the setup program or installer DLL creates a value under the following key for each file in that component that is not already on the system:</para>
    <alert class="note">
      <para>HKEY_LOCAL_MACHINE</para>
      <para>     SOFTWARE</para>
      <para>          Microsoft</para>
      <para>               Windows</para>
      <para>                    CurrentVersion</para>
      <para>                         SharedDlls</para>
    </alert>
    <para>It sets the data for those values to 1 and copies the file to the system. When the component is installed again, the setup program or installer DLL increments the usage counts. When the component is removed, the setup program or installer DLL decrements the usage counts. If any usage count falls to 0, the setup program or installer DLL removes the value for the file and, if the component is a driver or a translator, deletes the file. Driver Manager files should not be deleted.</para>
    <para>The format of the file usage count value is shown in the following table.</para>
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
            <para>
              <legacyItalic>full-path</legacyItalic>
            </para>
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
    <para>For example, suppose a driver for Informix uses the Infrmx32.dll and Infrmx32.hlp files, and suppose that this driver has been installed twice. The values under the SharedDlls subkey for the Informix driver would be as follows:</para>
    <code>C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>