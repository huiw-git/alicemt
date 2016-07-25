---
title: "Installing ODBC Components"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
caps.latest.revision: 9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Installing ODBC Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>This section describes how ODBC components are installed and removed. Because driver developers always install an ODBC component (their driver), they need to read this section. Application developers need to read this section only if they will ship ODBC components with their applications. ODBC components include the Driver Manager, drivers, translators, the installer DLL, the cursor library, and any related files. For the purposes of this section, ODBC applications are not considered to be ODBC components.</para>
    <alert class="note">
      <para>This section is specific to Microsoft Windows platforms. How ODBC components are installed on other platforms is platform-specific.</para>
    </alert>
    <para>ODBC components are installed and removed on a component-by-component basis, not a file-by-file basis. For example, if a translator consists of the translator itself and a number of data files, these files are installed and removed as a group; they must not be installed and removed on a file-by-file basis. The reason for this is to make sure that only complete components exist on the system.</para>
    <para>For purposes of installing and removing components, the following are defined to be ODBC components:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Core components.</legacyBold> The Driver Manager, cursor library, installer DLL, and any other related files make up the core components and must be installed and removed as a group.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Drivers.</legacyBold> Each driver is a separate component.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Translators.</legacyBold> Each translator is a separate component.</para>
      </listItem>
    </list>
    <para>With the support of Unicode in ODBC 3.5 and later, some consideration must be given to using OLE DB components with ODBC. The 1.1 version of the OLE DB Provider for ODBC was written to specific Unicode specifications within ODBC 3.0. Because these specifications changed in ODBC 3.5, it is necessary to have version 1.5 or later of the provider when using ODBC 3.5 and later. This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="9de15ca0-fe6a-4634-8709-a928d3c9cc73">Installation Components</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0678aee9-8256-463c-89dd-77b1a0dfdd60">Usage Counting</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>