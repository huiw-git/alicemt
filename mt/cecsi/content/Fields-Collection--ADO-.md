---
title: "Fields Collection (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
caps.latest.revision: 8
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
# Fields Collection (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> or <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Recordset</legacyBold> object has a <legacyBold>Fields</legacyBold> collection made up of <legacyBold>Field</legacyBold> objects. Each <legacyBold>Field</legacyBold> object corresponds to a column in the <legacyBold>Recordset</legacyBold>. You can populate the <legacyBold>Fields</legacyBold> collection before opening the <legacyBold>Recordset</legacyBold> by calling the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method on the collection.</para>
      <alert class="note">
        <para>See the <legacyBold>Field</legacyBold> object topic for a more detailed explanation of how to use <legacyBold>Field</legacyBold> objects.</para>
      </alert>
      <para>The <legacyBold>Fields</legacyBold> collection has an <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> method, which provisionally creates and adds a <legacyBold>Field</legacyBold> object to the collection, and an <legacyBold>Update</legacyBold> method, which finalizes any additions or deletions.</para>
      <para>A <legacyBold>Record</legacyBold> object has two special fields that can be indexed with <legacyLink xlink:href="be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2">FieldEnum</legacyLink> constants. One constant accesses a field containing the default stream for the <legacyBold>Record</legacyBold>, and the other accesses a field containing the absolute URL string for the <legacyBold>Record</legacyBold>.</para>
      <para>Certain providers (for example, the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>) may populate the <legacyBold>Fields</legacyBold> collection with a subset of available fields for the <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold>. Other fields will not be added to the collection until they are first referenced by name or indexed by your code.</para>
      <para>If you attempt to reference a nonexistent field by name, a new <legacyBold>Field</legacyBold> object will be appended to the <legacyBold>Fields</legacyBold> collection with a <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status</legacyLink> of <legacyBold>adFieldPendingInsert</legacyBold>. When you call <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>, ADO will create a new field in your data source if allowed by your provider.</para>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="8cc13e41-7ed8-40df-9a74-5bf846c14c06">Fields Collection Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>