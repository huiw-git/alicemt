---
title: "Type Property (ADO Stream)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
caps.latest.revision: 11
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
# Type Property (ADO Stream)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the type of data contained in the <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> (binary or text).</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="220fe51d-4889-4020-a099-2ec9c7485503">StreamTypeEnum</legacyLink> value that specifies the type of data contained in the <legacyBold>Stream</legacyBold> object. The default value is <legacyBold>adTypeText</legacyBold>. However, if binary data is initially written to a new, empty <legacyBold>Stream</legacyBold>, the <legacyBold>Type</legacyBold> will be changed to <legacyBold>adTypeBinary</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Type</legacyBold> property is read/write only when the current position is at the beginning of the <legacyBold>Stream </legacyBold>(<legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> is 0), and read-only at any other position.</para>
      <?Comment JT: Deleted bad link to Visual Basic Example mdhowstep4populatedetailstextbox| 2006-02-02T20:02:00Z  Id='0?>
      <para>The<?CommentEnd Id='0'
    ?> <legacyBold>Type</legacyBold> property determines which methods should be used for reading and writing the <legacyBold>Stream</legacyBold>. For text <legacyBold>Streams</legacyBold>, use <legacyLink xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText</legacyLink> and <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink>. For binary <legacyBold>Streams</legacyBold>, use <legacyLink xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read</legacyLink> and <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType Property</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>