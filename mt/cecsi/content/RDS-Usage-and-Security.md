---
title: "RDS Usage and Security"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8ac3739-05d3-4818-8201-a763795fb8b4
caps.latest.revision: 13
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# RDS Usage and Security
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the information in this section to set up your server and use RDS quickly. This section includes specific configuration steps that you might need to take when implementing RDS, describes some of the key relationships between RDS and other technologies, and helps identify solutions to problems that you might encounter when setting up an RDS solution.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="5dd48483-858a-48c2-98ce-f2359abe1f59">Configuring RDS</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a98a7245-06a7-455c-82ef-950807b9f1e7">Using Related Technologies with RDS</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="92905044-579f-4c38-bca6-f8bd5b239c20">Troubleshooting RDS</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
<link xlink:href="a7dcad87-aaf0-4b02-9660-472f8469761c">RDS Scenario</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>