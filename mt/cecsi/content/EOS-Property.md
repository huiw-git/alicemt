---
title: "EOS Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
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
# EOS Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether the current position is at the end of the <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">stream</legacyLink>.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Boolean</languageKeyword> value that indicates whether the current position is at the end of the stream. <legacyBold>EOS</legacyBold> returns <legacyBold>True</legacyBold> if there are no more bytes in the stream; it returns <legacyBold>False</legacyBold> if there are more bytes following the current position.</para>
      <para>To set the end of stream position, use the <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink> method. To determine the current position, use the <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> property.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">stream</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="77ce3042-9ebc-44ba-a4ff-0f1b1fd4a9c4">Visual Basic Example</link>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>