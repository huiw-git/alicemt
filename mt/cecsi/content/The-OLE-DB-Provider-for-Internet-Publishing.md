---
title: "The OLE DB Provider for Internet Publishing"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 10
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
# The OLE DB Provider for Internet Publishing
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ADO <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> and <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> objects can be used with the Microsoft OLE DB Provider for Internet Publishing (Internet Publishing Provider) to access and manipulate resources, such as Web folders or files served by Microsoft FrontPage. With ADO, you can specify the source of a <legacyBold>Record</legacyBold>, <legacyBold>Stream</legacyBold>, or <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to be a URL. You can then upload, download, move, copy, and delete resources, or directly manipulate resource properties.</para>
    <para>For example code that uses <legacyBold>Records</legacyBold> and <legacyBold>Streams</legacyBold> with the Internet Publishing Provider, see the <legacyLink xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</legacyLink>.</para>
    <para>The Internet Publishing Provider is installed with Microsoft Windows 2000. Earlier versions of the Internet Publishing Provider are also available with Microsoft Office 2000 and Microsoft Internet Explorer 5.0.</para>
    <para>There are three ways to connect ADO to the Internet Publishing Provider:  </para>
    <list class="bullet">
      <listItem>
        <para>Specify "URL=" in the connection string. For example: </para>
        <code>objConn.Open "URL=http://servername"</code>
      </listItem>
      <listItem>
        <para>Specify Msdaipp.dso for the <legacyItalic>Provider</legacyItalic> keyword of the connection string. For example: </para>
        <code>objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"</code>
      </listItem>
      <listItem>
        <para>Specify Msdaipp.dso for the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. For example: </para>
        <code>objConn.Provider = "MSDAIPP.DSO"
objConn.Open "http://servername"</code>
      </listItem>
    </list>
    <alert class="note">
      <para>If Msdaipp.dso is explicitly specified as the value of the provider, either with the <legacyItalic>Provider</legacyItalic> connection string keyword or the <legacyBold>Provider</legacyBold> property, you cannot use "URL=" in the connection string. If you do, an error will occur. Instead, simply specify the URL as shown earlier.</para>
    </alert>
    <para>For more specific information about the Internet Publishing Provider, see <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>, or the provider documentation provided with the source application with which the OLE DB Provider for Internet Publishing was installed: Windows 2000, Office 2000, or Internet Explorer 5.0.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>