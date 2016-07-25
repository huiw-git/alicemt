---
title: "DrilledDown Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
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
# DrilledDown Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether children immediately follow the <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">member</legacyLink> on the axis.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>Boolean</languageKeyword> value and is read-only. <unmanagedCodeEntityReference>DrilledDown</unmanagedCodeEntityReference> returns <languageKeyword>True</languageKeyword> if there are no child members of the current member on the axis. <unmanagedCodeEntityReference>DrilledDown</unmanagedCodeEntityReference> returns <languageKeyword>False</languageKeyword> if the current member has one or more child members on the axis.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>DrilledDown</unmanagedCodeEntityReference> property to determine whether there is at least one child of this member on the axis immediately following this member. This information is useful when displaying the member.</para>
      <para>This property is only supported on <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects belonging to a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink> object. An error occurs when this property is referenced from <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> objects belonging to a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> object.</para>
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
<link xlink:href="510842e0-e8dc-4b33-9517-bd1c6df0cf3c">ParentSameAsPrev Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>