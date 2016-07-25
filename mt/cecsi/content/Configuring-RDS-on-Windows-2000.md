---
title: "Configuring RDS on Windows 2000"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
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
# Configuring RDS on Windows 2000
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you experience difficulties getting RDS to function correctly after you upgrade to Windows 2000, follow these steps to troubleshoot the issue:  </para>
    <list class="ordered">
      <listItem>
        <para>Make sure that the World Wide Web Publishing Service is running first by navigating to http:// server by using Internet Explorer. If you cannot access the Web server in this manner, open a command prompt and enter the following command, "NET START W3SVC".</para>
      </listItem>
      <listItem>
        <para>On the Start menu, select Run. Type msdfmap.ini and then click OK to open the msdfmap.ini file in Notepad. Check the [CONNECT DEFAULT] section, and if the ACCESS parameter is set to NOACCESS, change it to READONLY.</para>
      </listItem>
      <listItem>
        <para>Using the RegEdit utility, navigate to "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo" and make sure <legacyBold>HandlerRequired</legacyBold> is set to 0 and <legacyBold>DefaultHandler</legacyBold> is "" (Null string). </para>
        <para>             <legacyBold>Note</legacyBold>   If you make any changes to this section of the registry, you must stop and restart the World Wide Web Publishing Service by entering the following commands at a command prompt: "NET STOP W3SVC" and "NET START W3SVC".</para>
      </listItem>
      <listItem>
        <para>Using the RegEdit utility, navigate in the registry to "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch" and verify that there is a key named <legacyBold>RDSServer.Datafactory</legacyBold>. If not, create it.</para>
      </listItem>
      <listItem>
        <para>Using Internet Services Manager, locate the Default Web site and view the properties of the MSADC virtual root. Inspect the Directory Security/IP Address and Domain Name Restrictions. If the "Access is Denied" is checked then select "Granted".</para>
      </listItem>
    </list>
    <para>Be sure to try rebooting the server if the changes to do not appear to solve the problem at first.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system. Migrate applications that use RDS to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>