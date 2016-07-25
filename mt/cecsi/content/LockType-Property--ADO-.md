---
title: "LockType Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
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
# LockType Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the type of locks placed on records during editing.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</legacyLink> value. The default value is <legacyBold>adLockReadOnly</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Set the <legacyBold>LockType</legacyBold> property before opening a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to specify what type of locking the provider should use when opening it. Read the property to return the type of locking in use on an open <legacyBold>Recordset</legacyBold> object.</para>
      <para>Providers may not support all lock types. If a provider cannot support the requested <legacyBold>LockType</legacyBold> setting, it will substitute another type of locking. To determine the actual locking functionality available in a <legacyBold>Recordset</legacyBold> object, use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method with <legacyBold>adUpdate</legacyBold> and <legacyBold>adUpdateBatch</legacyBold>.</para>
      <para>The <legacyBold>adLockPessimistic</legacyBold> setting is not supported if the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>. If an unsupported value is set, then no error will result; the closest supported <legacyBold>LockType</legacyBold> will be used instead.</para>
      <para>The <legacyBold>LockType</legacyBold> property is read/write when the <legacyBold>Recordset</legacyBold> is closed and read-only when it is open.</para>
      <alert class="note">
        <para> <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Recordset</legacyBold> object, the <legacyBold>LockType</legacyBold> property can only be set to <legacyBold>adLockBatchOptimistic</legacyBold>.</para>
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
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>