---
title: Driver Setup DLL
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Setup DLL
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The driver setup DLL contains the <legacyBold>ConfigDriver</legacyBold> and <legacyBold>ConfigDSN</legacyBold> functions. <legacyBold>ConfigDriver</legacyBold> performs driver-specific installation tasks, such as entering driver-specific information into the registry. <legacyBold>ConfigDSN</legacyBold> maintains driver-specific information about data sources in the registry. For a complete description of these functions, see <legacyLink xlink:href="f9d03f17-1c0d-4e7c-9c04-8c316e07ef25">Setup DLL API Reference</legacyLink>.</para>
    <para>
      <legacyBold>ConfigDSN</legacyBold> calls the following functions in the installer DLL to maintain data source information in the registry:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>SQLWriteDSNToIni</legacyBold>. Add a data source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLRemoveDSNFromIni</legacyBold>. Delete a data source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLWritePrivateProfileString</legacyBold>. Write a driver-specific value under a data source specification subkey.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLGetPrivateProfileString</legacyBold>. Read a driver-specific value from a data source specification subkey.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLGetTranslator</legacyBold>. Prompt the user for a translator name and option. This function calls <legacyBold>ConfigTranslator</legacyBold> in the translator setup DLL.</para>
      </listItem>
    </list>
    <para>The driver setup DLL is written by the driver developer. It can be part of the driver DLL or a separate DLL.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>