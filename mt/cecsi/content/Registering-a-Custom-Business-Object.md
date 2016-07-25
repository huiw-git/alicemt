---
title: "Registering a Custom Business Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
caps.latest.revision: 17
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
# Registering a Custom Business Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To successfully launch a custom business object (.dll or .exe) through the Web server, the business object's ProgID must be entered into the registry as explained in this procedure. This RDS feature protects the security of your Web server by running only sanctioned executables.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <alert class="note">
      <para>For MDAC 2.0 and later and Windows DAC, the default business object, <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>, is not registered by default during the MDAC/Windows DAC installation. However, if <legacyBold>RDSServer.DataFactory</legacyBold> was registered as safe for execution on the computer prior to the installation, the registry entry is maintained for the new installation.</para>
    </alert>
    <procedure>
      <title>To register a custom business object:</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Click <ui>Start</ui> and then click <ui>Run</ui>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Type <ui>RegEdit</ui> and click <ui>OK</ui>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Registry Editor, navigate to the <legacyBold>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch </legacyBold>registry key.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select the <ui>ADCLaunch</ui> key, and then from the <ui>Edit</ui><legacyBold> </legacyBold>menu, point to <ui>New</ui> and click <ui>Key</ui>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Type the ProgID of your custom business object and click <ui>Enter</ui>. Leave the <ui>Value</ui> entry blank.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>