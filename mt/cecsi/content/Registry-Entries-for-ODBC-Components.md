---
title: "Registry Entries for ODBC Components"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
caps.latest.revision: 8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Registry Entries for ODBC Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The installer DLL maintains information in the registry about each installed ODBC component. On computers running Microsoft Windows NT and Microsoft Windows 95/98, this information is stored in subkeys under the following key in the registry:</para>
    <para>HKEY_LOCAL_MACHINE</para>
    <para>     SOFTWARE</para>
    <para>          ODBC</para>
    <para>               Odbcinst.ini</para>
    <para>Because Odbcinst.ini is a subkey of the HKEY_LOCAL_MACHINE tree, the information about ODBC components is available to all users of the machine. </para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="055b31fc-f96c-450b-a596-d4570079fbf2">ODBC Core Subkey</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8edbf68f-d05d-4d77-92f6-e9500008f520">ODBC Drivers Subkey</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80">Driver Specification Subkeys</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9e58b24f-ebfc-4286-a272-0843b4d6f2d5">Default Driver Subkey</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="6b170f1f-e263-4aac-9d49-8d0ca0470ca2">ODBC Translators Subkey</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3c0edeee-d43a-4466-a177-bf2d2435707a">Translator Specification Subkeys</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>