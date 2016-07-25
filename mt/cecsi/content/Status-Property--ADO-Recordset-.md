---
title: "Status Property (ADO Recordset)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
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
# Status Property (ADO Recordset)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the status of the current record with respect to batch updates or other bulk operations.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a sum of one or more <legacyLink xlink:href="506fdd70-4452-4e83-95d5-c94311988dfa">RecordStatusEnum</legacyLink> values.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Status</legacyBold> property to see what changes are pending for records modified during batch updating. You can also use the <legacyBold>Status</legacyBold> property to view the status of records that fail during bulk operations, such as when you call the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> methods on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, or set the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property on a <legacyBold>Recordset</legacyBold> object to an array of bookmarks. With this property, you can determine how a given record failed and resolve it accordingly.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e37b4d46-380d-4615-b4bb-e1a7b0851771">Visual Basic Example</link>
<link xlink:href="194ce221-49bd-4474-ba34-91453d329381">Visual C++ Example</link>
<link xlink:href="d35cb991-2c5b-4d91-bc07-62104242cae7">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>