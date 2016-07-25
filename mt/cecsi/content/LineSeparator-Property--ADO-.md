---
title: "LineSeparator Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
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
# LineSeparator Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the binary character to be used as the line separator in text <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> objects.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="0440b793-99c7-49a2-b3e2-ec5b1a7e3e60">LineSeparatorsEnum</legacyLink> value that indicates the line separator character used in the <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>. The default value is <legacyBold>adCRLF</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <unmanagedCodeEntityReference>LineSeparator</unmanagedCodeEntityReference> is used to interpret lines when reading the content of a text <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>. Lines can be skipped with the <legacyLink xlink:href="0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329">SkipLine</legacyLink> method.</para>
      <para>
        <unmanagedCodeEntityReference>LineSeparator</unmanagedCodeEntityReference> is used only with text <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> objects (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeText</legacyBold>). This property is ignored if <unmanagedCodeEntityReference>Type</unmanagedCodeEntityReference> is <legacyBold>adTypeBinary</legacyBold>.</para>
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
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>