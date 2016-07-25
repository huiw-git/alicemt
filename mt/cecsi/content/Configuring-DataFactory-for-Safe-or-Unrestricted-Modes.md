---
title: "Configuring DataFactory for Safe or Unrestricted Modes"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
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
# Configuring DataFactory for Safe or Unrestricted Modes
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>By default, ADO is installed with a "safe" <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> configuration. Safe mode for RDS Server components means that the following are true:  </para>
    <list class="ordered">
      <listItem>
        <para>Handler is required with the RDSServer.DataFactory (this is mandated by a registry key setting).</para>
      </listItem>
      <listItem>
        <para>The default handler, msdfmap.handler, is registered, present in the safe-handler list, and marked as the default handler.</para>
      </listItem>
      <listItem>
        <para>Msdfmap.ini file is installed in the Windows directory. You must configure this file according to your needs, before you use RDS in three-tier mode.</para>
      </listItem>
    </list>
    <para>Optionally, you can configure an unrestricted <legacyBold>DataFactory</legacyBold> installation. <legacyBold>DataFactory</legacyBold> can be used directly without the custom handler. Users can still use a custom handler by modifying the connection strings, but it is not required. For more information about the implications of using the <legacyBold>RDSServer.DataFactory</legacyBold> object, see <legacyLink xlink:href="82fb1330-d6c6-4c17-ad3e-d417ff822b25">Securing RDS Applications</legacyLink>.</para>
    <para>The registry file handsafe.reg has been provided to set up the handler registry entries for a safe configuration. To run in safe mode, run handsafe.reg. </para>
    <para>After running handsafe.reg, you must stop and restart the World Wide Web Publishing Service on the Web server by typing the following commands in a Command Prompt window: "NET STOP W3SVC" and "NET START W3SVC".</para>
  </introduction>
  <relatedTopics>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>