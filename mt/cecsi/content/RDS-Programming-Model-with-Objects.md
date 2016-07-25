---
title: "RDS Programming Model with Objects"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
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
# RDS Programming Model with Objects
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The goal of RDS is to gain access to and update data sources through an intermediary such as IIS. The programming model specifies the sequence of activities necessary to accomplish this goal. The object model specifies the objects whose methods and properties affect the programming model.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>RDS provides the means to perform the following sequence of actions:  </para>
    <list class="bullet">
      <listItem>
        <para>Specify the program to be invoked on the server, and obtain a way (proxy) to refer to it from the client (<legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink>).</para>
      </listItem>
      <listItem>
        <para>Invoke the server program. Pass parameters to the server program that identifies the data source and the command to issue (proxy or <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink>).</para>
      </listItem>
      <listItem>
        <para>The server program obtains a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object from the data source, typically by using ADO. Optionally, the <legacyBold>Recordset</legacyBold> object is processed on the server (<legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>).</para>
      </listItem>
      <listItem>
        <para>The server program returns the final <legacyBold>Recordset</legacyBold> object to the client application (proxy).</para>
      </listItem>
      <listItem>
        <para>On the client, the <legacyBold>Recordset</legacyBold> object is put into a form that can be easily used by visual controls (visual control and <legacyBold>RDS.DataControl</legacyBold>).</para>
      </listItem>
      <listItem>
        <para>Changes to the <legacyBold>Recordset</legacyBold> object are sent back to the server and used to update the data source (<legacyBold>RDS.DataControl</legacyBold> or <legacyBold>RDSServer.DataFactory</legacyBold>).</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="909f9af7-31db-4eec-ad52-650ce74dac2f">RDS Object Model Summary</link>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
<link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
<link xlink:href="a7dcad87-aaf0-4b02-9660-472f8469761c">RDS Scenario</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="b8ac3739-05d3-4818-8201-a763795fb8b4">Using RDS</link>
</relatedTopics>
</developerConceptualDocument>