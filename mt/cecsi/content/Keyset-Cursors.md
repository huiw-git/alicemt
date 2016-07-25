---
title: "Keyset Cursors"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14b51b17-6fd9-4146-af45-ca4b0fe6d48a
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
# Keyset Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The keyset cursor provides functionality between a static and a dynamic cursor in its ability to detect changes. Like a static cursor, it does not always detect changes to the membership and order of the result set. Like a dynamic cursor, it does detect changes to the values of rows in the result set.</para>
    <para>Keyset-driven cursors are controlled by a set of unique identifiers (keys) known as the keyset. The keys are built from a set of columns that uniquely identify the rows in the result set. The keyset is the set of key values from all the rows returned by the query statement.</para>
    <para>With keyset-driven cursors, a key is built and saved for each row in the cursor and stored either on the client workstation or on the server. When you access each row, the stored key is used to fetch the current data values from the data source. In a keyset-driven cursor, result set membership is frozen when the keyset is fully populated. Thereafter, additions or updates that affect membership are not a part of the result set until it is reopened.</para>
    <para>Changes to data values (made either by the keyset owner or other processes) are visible as the user scrolls through the result set. Inserts made outside the cursor (by other processes) are visible only if the cursor is closed and reopened. Inserts made from inside the cursor are visible at the end of the result set.</para>
    <para>When a keyset-driven cursor attempts to retrieve a row that has been deleted, the row appears as a "hole" in the result set. The key for the row exists in the keyset, but the row no longer exists in the result set. If the key values in a row are updated, the row is considered to have been deleted and then inserted, so such rows also appear as holes in the result set. While a keyset-driven cursor can always detect rows deleted by other processes, it can optionally remove the keys for rows it deletes itself. Keyset-driven cursors that do this cannot detect their own deletes because the evidence has been removed.</para>
    <para>An update to a key column operates like a delete of the old key followed by an insert of the new key. The new key value is not visible if the update was not made through the cursor. If the update was made through the cursor, the new key value is visible at the end of the result set.</para>
    <para>There is a variation on keyset-driven cursors called keyset-driven standard cursors. In a keyset-driven standard cursor, the membership of rows in the result set and the order of the rows are fixed at cursor open time, but changes to values that are made by the cursor owner and committed changes made by other processes are visible. If a change disqualifies a row for membership or affects the order of a row, the row does not disappear or move unless the cursor is closed and reopened. Inserted data does not appear, but changes to existing data do appear as the rows are fetched.</para>
    <para>The keyset-driven cursor is difficult to use correctly because the sensitivity to data changes depends on many differing circumstances, as described above. However, if your application is not concerned with concurrent updates, can programmatically handle bad keys, and must directly access certain keyed rows, the keyset-driven cursor might work for you. Use the <legacyBold>adOpenKeyset</legacyBold> <legacyBold>CursorTypeEnum</legacyBold> to indicate that you want to use a keyset cursor in ADO.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="2b1e062f-3294-4a6f-8241-a17045c4df18">Forward-Only Cursors</link>
<link xlink:href="cce93ace-c4ed-4c6c-940c-28a50ff2fd12">Static Cursors</link>
<link xlink:href="00460f30-8cf7-494e-82df-41012f40ae51">Dynamic Cursors</link>
</relatedTopics>
</developerConceptualDocument>