---
title: Registry Entries for Data Sources
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
translation.priority.ht: 
  - en-gb
---
# Registry Entries for Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The installer DLL maintains information in the registry about each data source. In Microsoft Windows NT/Windows 2000 and Microsoft Windows 95/98, this information is stored in subkeys under one of the following two keys in the registry:</para>
    <para>HKEY_LOCAL_MACHINE</para>
    <para>     SOFTWARE</para>
    <para>          ODBC</para>
    <para>               Odbc.ini</para>
    <para>HKEY_CURRENT_USER</para>
    <para>     SOFTWARE</para>
    <para>          ODBC</para>
    <para>               Odbc.ini</para>
    <para>Which key is used depends on whether the data source is a <legacyItalic>system data source,</legacyItalic> which is available to all users, or a <legacyItalic>user data source,</legacyItalic> which is available only to the current user. System data sources are stored on the HKEY_LOCAL_MACHINE tree, and user data sources are stored on the HKEY_CURRENT_USER tree. In all other respects, system data sources and user data sources are identical. </para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="0a8ccb80-c573-4418-84e5-f04a2b0e2ac1">ODBC Data Sources Subkey</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d7e88a07-e6ab-4258-a45d-1ca21234fbec">Data Source Specification Subkeys</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="a2259db8-feb7-4f0a-afc8-88e235d86be7">Default Subkey</legacyLink> </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="f9534144-8f42-4946-b0fb-638e9dcde9c8">ODBC Subkey</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>