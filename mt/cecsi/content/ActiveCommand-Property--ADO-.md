---
title: "ActiveCommand Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
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
# ActiveCommand Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object that created the associated <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>Variant</languageKeyword> that contains a <legacyBold>Command</legacyBold> object. Default is a null object reference.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>ActiveCommand</legacyBold> property is read-only.</para>
      <para>If a <legacyBold>Command</legacyBold> object was not used to create the current <legacyBold>Recordset</legacyBold>, then a <legacyBold>Null</legacyBold> object reference is returned.</para>
      <para>Use this property to find the associated <legacyBold>Command</legacyBold> object when you are given only the resulting <legacyBold>Recordset</legacyBold> object.</para>
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
<link xlink:href="23b06499-62df-4f46-88eb-6da392f9b456">Visual Basic Example</link>
<link xlink:href="be09e2af-ba31-4168-8ccd-2461bb24e49a">JScript Example</link>
<link xlink:href="8269ea29-912a-4d20-9360-f48b3746081f">VC++Example</link>
<link xlink:href="f28637c7-05ab-482d-b1ce-bbfc41228050">VJ++Example</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>