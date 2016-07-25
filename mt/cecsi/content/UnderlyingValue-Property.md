---
title: "UnderlyingValue Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
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
# UnderlyingValue Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the current value of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object in the database.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>Variant</languageKeyword> value that indicates the value of the <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>UnderlyingValue</unmanagedCodeEntityReference> property to return the current field value from the database. The field value in the <unmanagedCodeEntityReference>UnderlyingValue</unmanagedCodeEntityReference> property is the value that is visible to your transaction and may be the result of a recent update by another transaction. This may differ from the <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> property, which reflects the value that was originally returned to the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
      <para>This is similar to using the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method, but the <unmanagedCodeEntityReference>UnderlyingValue</unmanagedCodeEntityReference> property returns only the value for a specific field from the current record. This is the same value that the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method uses to replace the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property.</para>
      <para>When you use this property with the <unmanagedCodeEntityReference>OriginalValue</unmanagedCodeEntityReference> property, you can resolve conflicts that arise from batch updates.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Record</title>
    <content>
      <para>For <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> objects, this property will be empty for fields added before <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> is called.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="1750804b-d7ef-47d6-8d73-1f51fa1cbe4a">Visual Basic Example</link>
<link xlink:href="c5762ad2-f43b-453d-b44a-9c70210eb00f">Visual C++ Example</link>
<link xlink:href="cfe62974-f768-437f-87c5-8106c4e23ad0">Visual J++ Example</link>
<link xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue Property</link>
<link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>