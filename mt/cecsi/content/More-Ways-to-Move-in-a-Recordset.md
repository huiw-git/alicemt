---
title: "More Ways to Move in a Recordset"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
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
# More Ways to Move in a Recordset
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following four methods are used to move around, or scroll, in the <legacyBold>Recordset</legacyBold>: <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious</legacyLink>. (Some of these methods are unavailable on forward-only cursors.) </para>
    <para>         <legacyBold>MoveFirst</legacyBold> changes the current record position to the first record in the <legacyBold>Recordset</legacyBold>. <legacyBold>MoveLast</legacyBold> changes the current record position to the last record in the <legacyBold>Recordset</legacyBold>. To use <legacyBold>MoveFirst</legacyBold> or <legacyBold>MoveLast</legacyBold>, the <legacyBold>Recordset</legacyBold> object must support bookmarks or backward cursor movement; otherwise, the method call will generate an error.</para>
    <para>         <legacyBold>MoveNext</legacyBold> moves the current record position one place forward. If you are on the last record when you call <legacyBold>MoveNext</legacyBold>, <legacyBold>EOF</legacyBold> will be set to <legacyBold>True</legacyBold>. <legacyBold>MovePrevious</legacyBold> moves the current record position one place backward. If you are on the first record when you call <legacyBold>MovePrevious</legacyBold>, <legacyBold>BOF</legacyBold> will be set to <legacyBold>True</legacyBold>. It is wise to check the <legacyBold>EOF</legacyBold> and <legacyBold>BOF</legacyBold> properties when using these methods and to move the cursor back to a valid current record position if you move off either end of the <legacyBold>Recordset</legacyBold>, as shown here:</para>
    <code>. . .
oRs.MoveNext
If oRs.EOF Then oRs.MoveLast
. . . </code>
    <para>Or, in the case of the <legacyBold>MovePrevious</legacyBold> method:</para>
    <code>. . . 
oRs.MovePrevious
If oRs.BOF Then oRs.MoveFirst
. . .</code>
    <para>In cases where the <legacyBold>Recordset</legacyBold> has been filtered or sorted and the current record's data is changed, the position may also change. In such cases the <legacyBold>MoveNext</legacyBold> method works normally, but be aware that the position is moved one record forward from the new position, not the old position. For example, changing the data in the current record, such that the record is moved to the end of the sorted <legacyBold>Recordset</legacyBold>, would mean that calling <legacyBold>MoveNext</legacyBold> results in ADO setting the current record to the position after the last record in the <legacyBold>Recordset</legacyBold> (<legacyBold>EOF</legacyBold> = <legacyBold>True</legacyBold>).</para>
    <para>The behavior of the various Move methods of the <legacyBold>Recordset</legacyBold> object depends, to some extent, on the data within the <legacyBold>Recordset</legacyBold>. New records added to the <legacyBold>Recordset</legacyBold> are initially added in a particular order, which is defined by the data source and may be dependent implicitly or explicitly on the data in the new record. For example, if a sort or a join is done within the query that populates the <legacyBold>Recordset</legacyBold>, the new record will be inserted in the appropriate place within the <legacyBold>Recordset</legacyBold>. If ordering is not explicitly specified when creating the <legacyBold>Recordset</legacyBold>, changes in the data source implementation may cause the ordering of the returned rows to change inadvertently. In addition, the sorting, filtering, and editing functions of the <legacyBold>Recordset</legacyBold> can affect the order and possibly which rows in the recordset will be visible.</para>
    <para>Therefore, <legacyBold>MoveNext</legacyBold>, <legacyBold>MovePrevious</legacyBold>, <legacyBold>MoveFirst</legacyBold>, <legacyBold>MoveLast</legacyBold>, and <legacyBold>Move</legacyBold> are all sensitive to other operations performed on the same <legacyBold>Recordset</legacyBold>. ADO will always try to maintain your current position until you explicitly move it, but sometimes, intervening changes make it difficult to understand the effects of a subsequent move. For example, if you call <legacyBold>MoveFirst</legacyBold> to position on the first row of a sorted <legacyBold>Recordset</legacyBold> and you change the sort from ascending order to descending order, you are still on the same row — but now it is the last row in the <legacyBold>Recordset</legacyBold>. <legacyBold>MoveFirst</legacyBold> will take you to a different row (the new first row).</para>
    <para>As another example, if you are positioned on a particular row in the middle of a <legacyBold>Recordset</legacyBold> and you call <legacyBold>Delete</legacyBold> and then call <legacyBold>MoveNext</legacyBold>, you are now on the record immediately following the deleted record. But calling <legacyBold>MovePrevious</legacyBold> makes the record preceding the one you deleted the current record, because the deleted record is no longer counted in the active membership of the <legacyBold>Recordset</legacyBold>.</para>
    <para>It is particularly difficult to define consistent move semantics across all providers for methods that move relative to the current record — <legacyBold>MovePrevious</legacyBold>, <legacyBold>MoveNext</legacyBold>, and <legacyBold>Move</legacyBold> — in the face of changing data in the current record. For example, if you are working with a sorted, filtered <legacyBold>Recordset</legacyBold>, and you change the data in the current record so that it would precede all other records, but your changed data also no longer matches the filter, it is not clear where a <legacyBold>MoveNext</legacyBold> operation should take you. The safest conclusion is that relative movement within a <legacyBold>Recordset</legacyBold> is riskier than absolute movement (such as using <legacyBold>MoveFirst</legacyBold> or <legacyBold>MoveLast</legacyBold>) when the data is changing while records are being edited, added, or deleted. Sorting and filtering should be based on a primary key or ID, because this type of value should not change.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>