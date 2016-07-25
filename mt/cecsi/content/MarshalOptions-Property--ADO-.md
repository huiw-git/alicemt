---
title: "MarshalOptions Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
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
# MarshalOptions Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates which records of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are to be marshaled back to the server.</para>
  </introduction>
  <section>
    <title>Settings And Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="4013075d-dbea-4bbc-a6f4-c345a55c5633">MarshalOptionsEnum</legacyLink> value. The default value is <legacyBold>adMarshalAll</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>When using a client-side <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, records that have been modified on the client are written back to the middle tier or Web server through a technique called marshaling, the process of packaging and sending interface method parameters across thread or process boundaries. Setting the <legacyBold>MarshalOptions</legacyBold> property can improve performance when modified remote data is marshaled for updating back to the middle tier or Web server.</para>
      <alert class="note">
        <para> <legacyBold>Remote Data Service Usage</legacyBold>   This property is used only on a client-side <legacyBold>Recordset</legacyBold>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ae576b2c-65aa-4838-872a-85e618806dc8">Visual Basic Example</link>
<link xlink:href="a3b6fc09-ce21-450d-9063-bac505208d31">Visual C++ Example</link>
<link xlink:href="9475c5f9-3a63-42cb-818c-4268e938a25c">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>