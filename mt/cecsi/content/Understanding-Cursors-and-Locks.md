---
title: "Understanding Cursors and Locks"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b7d7e6-1707-4ce2-863f-0c6dea967df6
caps.latest.revision: 9
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
# Understanding Cursors and Locks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>It is important to understand how cursors operate so you can select the best and most efficient cursor type for an application's data-access requirements. A less-than-optimal cursor configuration can make data-access operations painfully slow.</para>
    <para>Many capabilities of the ADO <legacyBold>Recordset</legacyBold> object are determined by the type and location of the cursor, as well as the lock type.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="596eb4b6-c22f-4cde-b23f-172dd66c3161">What is a Cursor?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="7cc01544-e814-403b-bbfe-a2750bf921bd">Types of Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="70ef5b1c-0459-41a1-b796-031f61a29a8a">The Significance of Cursor Location</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49">The Microsoft Cursor Service for OLE DB</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f8989555-28c6-4c17-9bf8-7f44a8a5c407">What is a Lock?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ca1c3422-b6a4-4ba6-af55-54f975b698b1">Using CacheSize</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="459c29cb-4230-42bf-8cc2-f3132ccc7aba">Cursor and Lock Characteristics</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>