---
title: "DataFactory Customization"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
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
# DataFactory Customization
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Remote Data Service (RDS) provides a way to easily perform data access in a three-tier client/server system. A client data control specifies connection and command string parameters to perform a query on a remote data source, or connection string and <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object parameters to perform an update.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The parameters are passed to a server program, which performs the data-access operation on the remote data source. RDS provides a default server program called the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object. The <legacyBold>RDSServer.DataFactory</legacyBold> object returns any <legacyBold>Recordset</legacyBold> object produced by a query to the client.</para>
    <para>However, the <legacyBold>RDSServer.DataFactory</legacyBold> is limited to performing queries and updates. It cannot perform any validation or processing on the connection or command strings.</para>
    <para>With ADO, you can specify that the <legacyBold>DataFactory</legacyBold> work in conjunction with another type of server program called a <legacyItalic>handler</legacyItalic>. The handler can modify client connection and command strings before they are used to access the data source. In addition, the handler can enforce access rights, which govern the ability of the client to read and write data to the data source.</para>
    <para>The parameters the handler uses to modify client parameters and access rights are specified in sections of a customization file.</para>
    <para>The following topics provide more information about customizing the <legacyBold>DataFactory</legacyBold> object.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a368e264-865c-41ee-be00-d9097255c2ea">Customization File Logs Section</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>