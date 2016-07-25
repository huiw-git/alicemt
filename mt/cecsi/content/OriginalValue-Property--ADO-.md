---
title: "OriginalValue Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
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
# OriginalValue Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the value of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> that existed in the record before any changes were made.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <legacyBold>Variant</legacyBold> value that represents the value of a field prior to any change.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>OriginalValue</legacyBold> property to return the original field value for a field from the current record.</para>
      <para>In <legacyItalic>immediate update mode</legacyItalic> (in which the provider writes changes to the underlying data source after you call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method), the <legacyBold>OriginalValue</legacyBold> property returns the field value that existed prior to any changes (that is, since the last <legacyBold>Update</legacyBold> method call). This is the same value that the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method uses to replace the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property.</para>
      <para>In <legacyItalic>batch update mode</legacyItalic> (in which the provider caches multiple changes and writes them to the underlying data source only when you call the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method), the <legacyBold>OriginalValue</legacyBold> property returns the field value that existed prior to any changes (that is, since the last <legacyBold>UpdateBatch</legacyBold> method call). This is the same value that the <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method uses to replace the <legacyBold>Value</legacyBold> property. When you use this property with the <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> property, you can resolve conflicts that arise from batch updates.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Record</title>
    <content>
      <para>For <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> objects, the <legacyBold>OriginalValue</legacyBold> property will be empty for fields added before <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> is called.</para>
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
<link xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>