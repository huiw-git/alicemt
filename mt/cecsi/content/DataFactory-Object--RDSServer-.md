---
title: "DataFactory Object (RDSServer)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
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
# DataFactory Object (RDSServer)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This default server-side business object implements methods that provide read/write data access to specified data sources for client-side applications.</para>
    <para>The <legacyBold>RDSServer.DataFactory</legacyBold> object is designed as a server-side Automation object that receives client requests. In an Internet implementation, it resides on a Web server and is instantiated by the ADISAPI component. The <legacyBold>RDSServer.DataFactory</legacyBold> object provides read and write access to specified data sources, but does not contain any validation or business rules logic.</para>
    <para>If you use a method that is available in both the <legacyBold>RDSServer.DataFactory</legacyBold> and <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> objects, Remote Data Service uses the <legacyBold>RDS.DataControl</legacyBold> version by default. The default assumes a basic programming scenario, where the <legacyBold>RDSServer.DataFactory</legacyBold> serves as a generic server-side business object.</para>
    <para>If you want your Web application to handle task-specific server-side processing, you can replace the <legacyBold>RDSServer.DataFactory</legacyBold> with a custom business object.</para>
    <para>You can create server-side business objects that call the <legacyBold>RDSServer.DataFactory</legacyBold> methods, such as <legacyLink xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query</legacyLink> and <legacyLink xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset</legacyLink>. This is helpful if you want to add functionality to your business objects, but take advantage of existing Remote Data Service technologies.</para>
    <para>The <unmanagedCodeEntityReference>DataFactory</unmanagedCodeEntityReference> object is not safe for scripts that run on the client side.</para>
    <para>The class ID for the <legacyBold>RDSServer.DataFactory</legacyBold> object is 9381D8F5-0288-11D0-9501-00AA00B911A5.</para>
    <para>This section contains the following topic.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="36a1f49b-91f4-44f4-b6e2-52fc7ed06d7e">DataFactory Object (RDSServer) Properties, Methods, and Events</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="b4e2844a-120a-4513-860b-f1b6e4b5dda4">VBScript Example</link>
</relatedTopics>
</developerConceptualDocument>