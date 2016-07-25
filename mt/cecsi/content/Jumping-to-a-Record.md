---
title: "Jumping to a Record"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6caf6299-2eea-4d34-9b0e-b75aab07b740
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
# Jumping to a Record
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method allows you to move forward or backward in the <legacyBold>Recordset</legacyBold> a specified number of records by using the following syntax:</para>
    <code>oRs.Move NumRecords, Start</code>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Move</legacyBold> method is supported on all <legacyBold>Recordset</legacyBold> objects.</para>
      <para>If the <legacyItalic>NumRecords</legacyItalic> argument is greater than zero, the current record position moves forward (toward the end of the <legacyBold>Recordset</legacyBold>). If <legacyItalic>NumRecords</legacyItalic> is less than zero, the current record position moves backward (toward the beginning of the <legacyBold>Recordset</legacyBold>).</para>
      <para>If the <legacyBold>Move</legacyBold> call would move the current record position to a point before the first record, ADO sets the current record to the position before the first record in the <legacyBold>Recordset</legacyBold> (<legacyBold>BOF</legacyBold> is <legacyBold>True</legacyBold>). An attempt to move backward when the <legacyBold>BOF</legacyBold> property is already <legacyBold>True</legacyBold> generates an error.</para>
      <para>If the <legacyBold>Move</legacyBold> call would move the current record position to a point after the last record, ADO sets the current record to the position after the last record in the <legacyBold>Recordset</legacyBold> (<legacyBold>EOF</legacyBold> is <legacyBold>True</legacyBold>). An attempt to move forward when the <legacyBold>EOF</legacyBold> property is already <legacyBold>True</legacyBold> generates an error.</para>
      <para>Calling the <legacyBold>Move</legacyBold> method from an empty <legacyBold>Recordset</legacyBold> object generates an error.</para>
      <para>If you pass a bookmark in the <legacyItalic>Start</legacyItalic> argument, the move is relative to the record with this bookmark, assuming the <legacyBold>Recordset</legacyBold> object supports bookmarks. A bookmark is obtained by using the <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink> property. If not specified, the move is relative to the current record.</para>
      <para>If you are using the <legacyBold>CacheSize</legacyBold> property to locally cache records from the provider, passing a <legacyItalic>NumRecords</legacyItalic> argument that moves the current record position outside the current group of cached records forces ADO to retrieve a new group of records, starting from the destination record. The <legacyBold>CacheSize</legacyBold> property determines the size of the newly retrieved group, and the destination record is the first record retrieved.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>