---
title: "Enabling a DLL to Run on DCOM"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
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
# Enabling a DLL to Run on DCOM
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following steps outline how to enable a business object .dll to use both DCOM and Microsoft Internet Information Services (HTTP) via Component Services.  </para>
    <list class="ordered">
      <listItem>
        <para>Create a new empty package in the Component Services MMC snap-in. </para>
        <para>You will use the Component Services MMC snap-in to create a package and add the DLL into this package. This makes the .dll accessible through DCOM, but it removes the accessibility through IIS. (If you check in the registry for the .dll, the <legacyBold>Inproc </legacyBold>key is now empty; setting the Activation attribute, explained later in this topic, adds a value in the <legacyBold>Inproc </legacyBold>key.) </para>
      </listItem>
      <listItem>
        <para>Install a business object into the package. </para>
        <para>-or-  </para>
        <para>Import the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object into the package. </para>
      </listItem>
      <listItem>
        <para>Set the Activation attribute for the package to <legacyBold>In the creator's process</legacyBold> (Library application). </para>
        <para>To make the .dll accessible through DCOM and IIS on the same computer, you must set the component's Activation attribute in the Component Services MMC snap-in. After you set the attribute to <legacyBold>In the creator's process</legacyBold>, you will notice that an <legacyBold>Inproc</legacyBold> server key in the registry has been added that points to a Component Services surrogate .dll. </para>
      </listItem>
    </list>
    <para>For more information about Component Services (or Microsoft Transaction Service, if you are using Windows NT) and how to perform these steps, visit the Microsoft Transaction Server Web site.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>