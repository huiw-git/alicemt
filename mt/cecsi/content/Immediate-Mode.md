---
title: "Immediate Mode"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
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
# Immediate Mode
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Immediate mode is in effect when the <legacyBold>LockType</legacyBold> property is set to <legacyBold>adLockOptimistic</legacyBold> or <legacyBold>adLockPessimistic</legacyBold>. In immediate mode, changes to a record are propagated to the data source as soon as you declare the work on a row complete by calling the <legacyBold>Update</legacyBold> method.</para>
  </introduction>
  <section>
    <title>Calling Update</title>
    <content>
      <para>If you move from the record you are adding or editing before calling the <legacyBold>Update</legacyBold> method, ADO will automatically call <legacyBold>Update</legacyBold> to save the changes. You must call the <legacyBold>CancelUpdate</legacyBold> method before navigation if you want to cancel any changes made to the current record or discard a newly added record.</para>
      <para>The current record remains current after you call the <legacyBold>Update</legacyBold> method.</para>
    </content>
  </section>
  <section>
    <title>CancelUpdate</title>
    <content>
      <para>Use the <legacyBold>CancelUpdate</legacyBold> method to cancel any changes made to the current row or to discard a newly added row. You cannot cancel changes to the current row or a new row after you call the <legacyBold>Update</legacyBold> method, unless the changes are either part of a transaction that you can roll back with the <legacyBold>RollbackTrans</legacyBold> method or part of a batch update. In the case of a batch update, you can cancel the <legacyBold>Update</legacyBold> with the <legacyBold>CancelUpdate</legacyBold> or <legacyBold>CancelBatch</legacyBold> method.</para>
      <para>If you are adding a new row when you call the <legacyBold>CancelUpdate</legacyBold> method, the current row becomes the row that was current before the <legacyBold>AddNew</legacyBold> call.</para>
      <para>If you have not changed the current row or added a new row, calling the <legacyBold>CancelUpdate</legacyBold> method generates an error.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>