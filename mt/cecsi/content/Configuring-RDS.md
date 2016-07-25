---
title: "Configuring RDS"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dd48483-858a-48c2-98ce-f2359abe1f59
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
# Configuring RDS
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>To implement RDS efficiently, be sure you are familiar with the various configurations available to you. This section includes important information about security and scalability in your implementation of RDS. See the following topics for information about configuring your computers to use RDS.  </para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="e851a22d-01bc-4eb0-bc42-92b8f65d1c63">Granting Guest Privileges to a Web Server Computer</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="e9032ad8-d14c-42e3-ba13-cb5f00084a79">Registering a Custom Business Object</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="0be98d1a-ab3d-4dce-a166-dacda10d154a">Marking Business Objects as Safe for Scripting</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="75a21910-607f-463a-ae18-a17130dafb7e">Registering Business Objects on the Client for Use with DCOM</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="46664ac5-d6e6-4457-8bae-3a98300f2a41">Setting DCOM Stream Marshaling Format</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="5f1c2205-191c-4fb4-9bd9-84c878ea46ed">Enabling a DLL to Run on DCOM</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="2b4786c6-40c4-4ce1-9ad4-03df436e0aff">Configuring Virtual Servers on IIS</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="82fb1330-d6c6-4c17-ad3e-d417ff822b25">Securing RDS Applications</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="8ff24805-dc7a-42ae-b600-5bad0e3f51b8">Configuring DataFactory for Safe or Unrestricted Modes</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a98a7245-06a7-455c-82ef-950807b9f1e7">Using Related Technologies with RDS</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="92905044-579f-4c38-bca6-f8bd5b239c20">Troubleshooting RDS</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>