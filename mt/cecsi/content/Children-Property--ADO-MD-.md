---
title: "Children Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
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
# Children Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns a <legacyLink xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members</legacyLink> collection for which the current <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> is the parent in the hierarchy.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <legacyBold>Members</legacyBold> collection and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Children</legacyBold> property contains a <legacyBold>Members</legacyBold> collection for which the current <legacyBold>Member</legacyBold> is the hierarchical parent. Leaf level <legacyBold>Member</legacyBold> objects have no child members in the <legacyBold>Members</legacyBold> collection. This property is only supported on <legacyBold>Member</legacyBold> objects belonging to a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> object. An error occurs when this property is referenced from <legacyBold>Member</legacyBold> objects belonging to a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="5463be22-ca50-43ea-9c92-468fc8eda280">ChildCount Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>