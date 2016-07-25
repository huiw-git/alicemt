---
title: "SetEOS Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
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
# SetEOS Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Sets the position that is the end of the stream.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
Stream.SetEOS</legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>SetEOS</legacyBold> updates the value of the <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> property, by making the current <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> the end of the stream. Any bytes or characters following the current position are truncated.</para>
      <para>Because <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink>, <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink>, and <legacyLink xlink:href="b4aa5714-916b-48b8-8b09-cc2708379602">CopyTo</legacyLink> do not truncate any extra values in existing <legacyBold>Stream</legacyBold> objects, you can truncate these bytes or characters by setting the new end-of-stream position with <legacyBold>SetEOS</legacyBold>.</para>
      <alert class="caution">
        <para>If you set <legacyBold>EOS</legacyBold> to a position before the actual end of the stream, you will lose all data after the new <legacyBold>EOS</legacyBold> position.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>