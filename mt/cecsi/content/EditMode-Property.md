---
title: "EditMode Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
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
# EditMode Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the editing status of the current record.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns an <legacyLink xlink:href="45d54b6e-db2c-4553-9fd0-528147d6da2f">EditModeEnum</legacyLink> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>ADO maintains an editing buffer associated with the current record. This property indicates whether changes have been made to this buffer, or whether a new record has been created. Use the <legacyBold>EditMode</legacyBold> property to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> or <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method.</para>
      <para>In <legacyItalic>immediate update mode</legacyItalic> the <legacyBold>EditMode</legacyBold> property is reset to <legacyBold>adEditNone</legacyBold> after a successful call to the <legacyBold>Update</legacyBold> method is called. When a call to <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink> does not successfully delete the record or records in the data source (for example, because of referential integrity violations), the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> remains in edit mode (<legacyBold>EditMode</legacyBold> = <legacyBold>adEditInProgress</legacyBold>). Therefore, <legacyBold>CancelUpdate</legacyBold> must be called before moving off the current record (for example with <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>, or <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> ).</para>
      <para>In <legacyItalic>batch update mode</legacyItalic> (in which the provider caches multiple changes and writes them to the underlying data source only when you call the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method), the value of the <legacyBold>EditMode</legacyBold> property is changed when the first operation is performed and it is not reset by a call to the <legacyBold>Update</legacyBold> method. Subsequent operations do not change the value of the <legacyBold>EditMode</legacyBold> property, even if different operations are performed. For example, if the first operation is to add a new record, and the second makes changes to an existing record, the property of <legacyBold>EditMode</legacyBold> will still be <legacyBold>adEditAdd</legacyBold>. The <legacyBold>EditMode</legacyBold> property is not reset to <legacyBold>adEditNone</legacyBold> until after the call to <legacyBold>UpdateBatch</legacyBold>. To determine what operations have been performed, set the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property to <legacyLink xlink:href="b22e725e-84bd-4286-a070-290c278c3783">adFilterPending</legacyLink> so that only records with pending changes will be visible and examine the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property of each record to determine what changes have been made to the data.</para>
      <alert class="note">
        <para>  <legacyBold>EditMode</legacyBold> can return a valid value only if there is a current record. <legacyBold>EditMode</legacyBold> will return an error if <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF or EOF</legacyLink> is true, or if the current record has been deleted.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object (ADO)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2cb4a304-f40a-4897-8b93-82c2d8e93500">Visual Basic Example</link>
<link xlink:href="b2a80e44-03d8-426e-81b6-dd9dfc30e181">Visual C++ Example</link>
<link xlink:href="c222016e-415d-485e-86c5-e29feac4297a">Visual J++ Example</link>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method</link>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>