---
title: Configuration Components
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
translation.priority.ht: 
  - en-gb
---
# Configuration Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>Data sources are configured by the installer DLL, which in turn calls driver setup DLLs and translator setup DLLs as they are needed. The installer DLL is either invoked directly from Control Panel or loaded and called by another program, known as the <legacyItalic>administration program</legacyItalic>. The following illustration shows the relationship between the configuration components.</para>
    <mediaLink>
      <image xlink:href="3e82c148-ebd4-476d-aa3c-e4ed71b4d5b9" />
    </mediaLink>
    <para>For more information about these components, see the following topics at the end of this section.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="9cc5d75d-b293-41e5-927c-10f4af2e7af1">Setup Program</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e2b92afb-64ce-4ce0-84ad-6a4276646e68">Installer DLL</legacyLink> </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="49bab021-81fa-402e-b7a4-a5214f1fadc4">Driver Setup DLL</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="9de15ca0-fe6a-4634-8709-a928d3c9cc73">Installation Components</link>
</relatedTopics>
</developerConceptualDocument>