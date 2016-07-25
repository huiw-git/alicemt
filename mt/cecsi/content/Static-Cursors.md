---
title: "Static Cursors"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 4
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
# Static Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The static cursor always displays the result set as it was when the cursor was first opened. Depending on implementation, static cursors are either read-only or read/write and provide forward and backward scrolling. The static cursor does not usually detect changes made to the membership, order, or values of the result set after the cursor is opened. Static cursors may detect their own updates, deletes, and inserts, although they are not required to do so.</para>
    <para>Static cursors never detect other updates, deletes, and inserts. For example, suppose a static cursor fetches a row, and another application then updates that row. If the application refetches the row from the static cursor, the values it sees are unchanged, despite the changes made by the other application. All types of scrolling are supported, but providers may or may not support bookmarks.</para>
    <para>If your application does not need to detect data changes and requires scrolling, the static cursor is the best choice. Use the <legacyBold>adOpenStatic</legacyBold> <legacyBold>CursorTypeEnum</legacyBold> to indicate that you want to use a static cursor in ADO.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="2b1e062f-3294-4a6f-8241-a17045c4df18">Forward-Only Cursors</link>
<link xlink:href="14b51b17-6fd9-4146-af45-ca4b0fe6d48a">Keyset Cursors</link>
<link xlink:href="00460f30-8cf7-494e-82df-41012f40ae51">Dynamic Cursors</link>
</relatedTopics>
</developerConceptualDocument>