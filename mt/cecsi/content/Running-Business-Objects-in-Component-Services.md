---
title: "Running Business Objects in Component Services"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
caps.latest.revision: 15
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
# Running Business Objects in Component Services
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Business objects can be executable files (.exe) or dynamic-link libraries (.dll). The configuration you use to run the business object depends on whether the object is a .dll or .exe file:  </para>
    <list class="bullet">
      <listItem>
        <para>Business objects created as .exe files can be called through DCOM. If these business objects are used through Internet Information Services (IIS), they are subject to additional marshaling of data, which will slow client performance.</para>
      </listItem>
      <listItem>
        <para>Business objects created as .dll files can be used through IIS, and therefore also by HTTP. They can also be used over DCOM only through Component Services, or through Microsoft Transaction Server, if you are using Windows NT. Business object DLLs will need to be registered on the IIS server computer to access them through  IIS. For information about how to configure a DLL to run on DCOM, see the section, <legacyLink xlink:href="5f1c2205-191c-4fb4-9bd9-84c878ea46ed">Enabling a DLL to Run on DCOM</legacyLink>.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>When business objects on the middle tier are implemented as Component Services components by using <legacyBold>GetObjectContext</legacyBold>, <legacyBold>SetComplete</legacyBold>, and <legacyBold>SetAbort</legacyBold>, the business objects can use Component Services (or MTS, if you are using Windows NT) context objects to maintain their state across multiple client calls. This scenario is possible with DCOM, which is typically implemented between trusted clients and servers in an intranet. In this case, the <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> object and <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink> method on the client side are replaced by the transaction context object and <legacyBold>CreateInstance</legacyBold> method, which are provided by the <legacyBold>ITransactionContext </legacyBold>interface and implemented by Component Services.</para>
    </alert>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>