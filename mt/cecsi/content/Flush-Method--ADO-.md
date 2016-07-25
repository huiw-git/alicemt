---
title: "Flush Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 12
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
# Flush Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Forces the contents of the <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> remaining in the ADO buffer to the underlying object with which the <legacyBold>Stream</legacyBold> is associated.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.Flush</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>This method can be used to send the contents of the stream buffer to the underlying object: for example, the node or file represented by the URL that is the source of the <legacyBold>Stream</legacyBold> object. This method should be called when you want to ensure that all changes that were made to the contents of a <legacyBold>Stream</legacyBold> have been written. However, with ADO it is not usually necessary to call <legacyBold>Flush</legacyBold>, as ADO continuously flushes its buffer as much as possible in the background. Changes to the content of a <legacyBold>Stream</legacyBold> are made automatically, not cached until <legacyBold>Flush</legacyBold> is called.</para>
      <para>Closing a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method flushes the contents of a <legacyBold>Stream</legacyBold> automatically; there is no need to explicitly call <legacyBold>Flush</legacyBold> immediately before <legacyBold>Close</legacyBold>.</para>
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