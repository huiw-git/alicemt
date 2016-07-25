---
title: "ChildCount Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
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
# ChildCount Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the number of members for which the current <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> object is the parent in a hierarchy.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> integer and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>ChildCount</unmanagedCodeEntityReference> property to return an estimate of how many children a <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> has. The actual children of a <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> can be returned by the <legacyLink xlink:href="61d36468-1ccd-467a-9cb5-17d0bfacc766">Children</legacyLink> property.</para>
      <para>For <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> objects from a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink> object, the maximum number returned is 65536. If the actual number of children exceeds 65536, the value returned will still be 65536. Therefore, the application should interpret a <unmanagedCodeEntityReference>ChildCount</unmanagedCodeEntityReference> of 65536 as equal to or greater than 65536 children.</para>
      <para>For <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> objects from a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> object, use the ADO collection <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property on the <unmanagedCodeEntityReference>Children</unmanagedCodeEntityReference> collection to determine the exact number of children. Determining the exact number of children may be slow if the number of children in the collection is large.</para>
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
<link xlink:href="61d36468-1ccd-467a-9cb5-17d0bfacc766">Children Property</link>
<link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property</link>
<link xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>