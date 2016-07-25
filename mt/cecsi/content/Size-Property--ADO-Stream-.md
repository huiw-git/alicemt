---
title: "Size Property (ADO Stream)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
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
# Size Property (ADO Stream)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the size of the stream in number of bytes.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> value that specifies the size of the stream in number of bytes. The default value is the size of the stream, or -1 if the size of the stream is not known.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>Size</legacyBold> can be used only with open <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> objects.</para>
      <alert class="note">
        <para>Any number of bits can be stored in a <legacyBold>Stream</legacyBold> object, limited only by system resources. If the <legacyBold>Stream</legacyBold> contains more bits than can be represented by a <legacyBold>Long</legacyBold> value, <legacyBold>Size</legacyBold> is truncated and therefore does not accurately represent the length of the <legacyBold>Stream</legacyBold>.</para>
      </alert>
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
<link xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>