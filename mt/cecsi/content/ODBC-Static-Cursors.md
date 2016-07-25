---
title: "ODBC Static Cursors"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Static Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A static cursor is one in which the result set appears to be static. It does not usually detect changes that were made to the membership, order, or values of the result set after the cursor is opened. For example, suppose a static cursor fetches a row and another application then updates that row. If the static cursor refetches the row, the values it sees are unchanged, despite the changes that were made by the other application.</para>
    <para>Static cursors can detect their own updates, deletes, and inserts, although they are not required to do this. Whether a particular static cursor detects these changes is reported through the SQL_STATIC_SENSITIVITY option in <legacyBold>SQLGetInfo</legacyBold>. Static cursors never detect other updates, deletes, and inserts.</para>
    <para>The row status array specified by the SQL_ATTR_ROW_STATUS_PTR statement attribute can contain SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, or SQL_ROW_ERROR for any row. It returns SQL_ROW_UPDATED, SQL_ROW_DELETED, or SQL_ROW_ADDED for rows updated, deleted, or inserted by the cursor, assuming that the cursor can detect such changes.</para>
    <para>Static cursors are typically implemented by locking the rows in the result set or by making a copy, or snapshot, of the result set. Although locking rows is relatively easy to do, it has the drawback of significantly reducing concurrency. Making a copy allows for greater concurrency and allows the cursor to keep track of its own updates, deletes, and inserts by modifying the copy. However, a copy is more expensive to make and can diverge from the underlying data as that data is changed by others.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>