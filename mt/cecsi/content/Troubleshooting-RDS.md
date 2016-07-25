---
title: "Troubleshooting RDS"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92905044-579f-4c38-bca6-f8bd5b239c20
caps.latest.revision: 12
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
# Troubleshooting RDS
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Refer to this section for solutions to specific errors or issues with RDS. This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="ef37e858-c05f-4f52-a65f-3ce6037e0d03">Configuring RDS on Windows 2000</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e5b43cfa-da8d-430d-a2ab-5443dda47a16">"Internet Server Error: Access Denied"</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cb5a68f8-dba4-41da-bafd-04efe53706b7">RDS Returns "Stream Not Read" Error</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="29f3683f-12f3-4304-8a54-fe133c25a423">Deadlocks With Read Repeatable Isolation Level</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="09130db1-6248-4234-a1e5-a9c8e1622c06">Ensuring Sufficient TempDB Space</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="669662a0-e20f-483e-ab28-53f66c524c98">Minimizing Log File Space Usage</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>