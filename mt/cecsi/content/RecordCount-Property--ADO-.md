---
title: "RecordCount Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
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
# RecordCount Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the number of records in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <legacyBold>Long</legacyBold> value that indicates the number of records in the <legacyBold>Recordset</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>RecordCount</legacyBold> property to find out how many records are in a <legacyBold>Recordset</legacyBold> object. The property returns -1 when ADO cannot determine the number of records or if the provider or cursor type does not support <legacyBold>RecordCount</legacyBold>. Reading the <legacyBold>RecordCount</legacyBold> property on a closed <legacyBold>Recordset</legacyBold> causes an error.</para>
      <para>If the <legacyBold>Recordset</legacyBold> object supports approximate positioning or bookmarks — that is, <legacyBold>Supports (adApproxPosition)</legacyBold> or <legacyBold>Supports (adBookmark)</legacyBold>, respectively, return <legacyBold>True</legacyBold>— this value will be the exact number of records in the <legacyBold>Recordset</legacyBold>, regardless of whether it has been fully populated. If the <legacyBold>Recordset</legacyBold> object does not support approximate positioning, this property may be a significant drain on resources because all records will have to be retrieved and counted to return an accurate <legacyBold>RecordCount</legacyBold> value.</para>
      <alert class="note">
        <para>In ADO versions 2.8 and earlier, the SQLOLEDB provider fetches all records when a server-side cursor is used, despite the fact that it returns <legacyBold>True</legacyBold> for both <legacyBold>Supports (adApproxPosition)</legacyBold> and <legacyBold>Supports (adBookmark)</legacyBold>.</para>
      </alert>
      <para>The cursor type of the <legacyBold>Recordset</legacyBold> object affects whether the number of records can be determined. The <legacyBold>RecordCount</legacyBold> property will return -1 for a forward-only cursor; the actual count for a static or keyset cursor; and either -1 or the actual count for a dynamic cursor, depending on the data source.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e8bc63c7-8967-438a-9a49-512478a87a15">Visual Basic Example</link>
<link xlink:href="b71346cb-3b09-4b8c-a600-976171a1c336">Visual C++ Example</link>
<link xlink:href="16d5d896-9905-4f75-973b-e1e696cd169f">Visual J++ Example</link>
<link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>