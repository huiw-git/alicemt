---
title: "Update Resync Property-Dynamic (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
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
# Update Resync Property-Dynamic (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method is followed by an implicit <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method operation, and if so, the scope of that operation.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns one or more of the <legacyLink xlink:href="bc9e1a37-e969-47e9-8382-0bbfffa2034f">ADCPROP_UPDATERESYNC_ENUM</legacyLink> values.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The values of ADCPROP_UPDATERESYNC_ENUM may be combined, except for adResyncAll which already represents the combination of the rest of the values.</para>
      <para>The constant <legacyBold>adResyncConflicts</legacyBold> stores the resync values as underlying values, but does not override pending changes.</para>
      <para>
        <legacyBold>Update Resync</legacyBold> is a dynamic property appended to the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection when the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>