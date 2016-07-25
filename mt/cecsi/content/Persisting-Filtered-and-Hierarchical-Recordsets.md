---
title: "Persisting Filtered and Hierarchical Recordsets"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
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
# Persisting Filtered and Hierarchical Recordsets
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property is in effect for the <legacyBold>Recordset</legacyBold>, only the rows accessible under the filter are saved. If the <legacyBold>Recordset</legacyBold> is hierarchical, the current child <legacyBold>Recordset</legacyBold> and its children are saved, including the parent <legacyBold>Recordset</legacyBold>. If the <legacyBold>Save</legacyBold> method of a child <legacyBold>Recordset</legacyBold> is called, the child and all its children are saved, but the parent is not. For more information about hierarchical <legacyBold>Recordsets</legacyBold>, see <link xlink:href="62bd7dc9-45b5-4ca9-8b52-457325e0ce9e">Data Shaping</link>.</para>
    <alert class="note">
      <para>Some limitations apply when saving hierarchical <legacyBold>Recordsets</legacyBold> (data shapes) in XML format. For more information, see <link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>