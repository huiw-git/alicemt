---
title: "DataSpace Object (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9194bffa-5bdf-4dff-af86-f7158c23bfa7
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
# DataSpace Object (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Creates client-side proxies to custom business objects located on the middle tier.</para>
    <para>Remote Data Service needs business object proxies so that client-side components can communicate with business objects located on the middle tier. Proxies facilitate the packaging, unpackaging, and transport (marshaling) of the application's <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> data across process or machine boundaries.</para>
    <para>Remote Data Service uses the <legacyBold>RDS.DataSpace</legacyBold> object's <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink> method to create business object proxies. The business object proxy is dynamically created whenever an instance of its middle-tier business object counterpart is created. Remote Data Service supports the following protocols: HTTP, HTTPS (HTTP Secure Sockets), DCOM, and in-process (client components and the business object reside on the same computer).</para>
    <alert class="note">
      <para>RDS behaves in a "stateless" manner when the <legacyBold>RDS.DataSpace</legacyBold> object uses the HTTP or HTTPS protocols. That is, any internal information about a client request is discarded after the server returns a response.</para>
    </alert>
    <alert class="note">
      <para>Although the business object appears to exist for the lifetime of the business object proxy, the business object actually exists only until a response is sent to a request. When a request is issued (that is, a method is invoked on the business object), the proxy opens a new connection to the server and the server creates a new instance of the business object. After the business object responds to the request, the server destroys the business object and closes the connection.</para>
    </alert>
    <alert class="note">
      <para>This behavior means you cannot pass data from one request to another using a business object property or variable. You must employ some other mechanism, such as a file or a method argument, to persist state data.</para>
    </alert>
    <para>The class ID for the <legacyBold>RDS.DataSpace</legacyBold> object is BD96C556-65A3-11D0-983A-00C04FC29E36.</para>
    <para>The <legacyBold>DataSpace</legacyBold> object is safe for scripting.</para>
    <para>This section contains the following topic.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="c4a1f2e7-19ff-465e-9d9a-275ac0f4dc6a">DataSpace Object (RDS) Properties, Methods, and Events</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="12b0e160-5e5c-441f-bed7-ac0bd061e003">VBScript Example</link>
</relatedTopics>
</developerConceptualDocument>