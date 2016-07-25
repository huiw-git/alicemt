---
title: "Batch Mode"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 14
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
# Batch Mode
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Batch mode is in effect when the <legacyBold>LockType</legacyBold> property is set to <legacyBold>adLockBatchOptimistic</legacyBold> and batch updating is supported by the provider. Certain lock type settings are not available depending on cursor location. For instance, a pessimistic lock type is not available when the <legacyBold>CursorLocation</legacyBold> is set to <legacyBold>adUseClient</legacyBold>. Conversely, a provider cannot support a batch optimistic lock when the cursor location is on the server. You should use batch updating with either a keyset or static cursor only.</para>
    <para>The <legacyBold>UpdateBatch</legacyBold> method is used to send <legacyBold>Recordset</legacyBold> changes held in the copy buffer to the server to update the data source. In the following section, we will open a <legacyBold>Recordset</legacyBold> in batch mode, make changes to the copy buffer, and then send our changes to the data source using a call to <legacyBold>UpdateBatch</legacyBold>.</para>
    <para>This section contains the following topics:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="87123797-831f-48e0-94b5-f669f9ca194a">Sending the Updates: UpdateBatch Method</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="4a798921-d7bb-47c9-a252-550fd9463ec9">Filtering for Updated Records</link> </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="299c37bd-19ff-4261-8571-b9665687e075">Dealing with Failed Updates</link> </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="b28fdd26-c1a4-40ce-a700-2b0c9d201514">Detecting and Resolving Conflicts</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="c5134af7-81d6-4de4-9fd1-cfe29973545e">Disconnecting and Reconnecting the Recordset</link> </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="d52e6926-5c22-43dc-9f32-7b32c1a071e2">Updating JOINed Results: Unique Table</link> </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>