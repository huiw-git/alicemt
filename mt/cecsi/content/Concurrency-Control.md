---
title: Concurrency Control
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
translation.priority.ht: 
  - en-gb
---
# Concurrency Control
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>Concurrency</legacyItalic> is the ability of two transactions to use the same data at the same time, and with increased transaction isolation usually comes reduced concurrency. This is because transaction isolation is usually implemented by locking rows, and as more rows are locked, fewer transactions can be completed without being blocked at least temporarily by a locked row. While reduced concurrency is generally accepted as a trade-off for the higher transaction isolation levels necessary to maintain database integrity, it can become a problem in interactive applications with high read/write activity that use cursors.</para>
    <para>For example, suppose an application executes the SQL statement <legacyBold>SELECT * FROM Orders</legacyBold>. It calls <legacyBold>SQLFetchScroll</legacyBold> to scroll around the result set and allows the user to update, delete, or insert orders. After the user updates, deletes, or inserts an order, the application commits the transaction.</para>
    <para>If the isolation level is Repeatable Read, the transaction might — depending on how it is implemented — lock each row returned by <legacyBold>SQLFetchScroll</legacyBold>. If the isolation level is Serializable, the transaction might lock the entire Orders table. In either case, the transaction releases its locks only when it is committed or rolled back. So if the user spends a lot of time reading orders and very little time updating, deleting, or inserting them, the transaction could easily lock a large number of rows, making them unavailable to other users.</para>
    <para>This is a problem even if the cursor is read-only and the application allows the user to read only existing orders. In this case, the application commits the transaction, and releases locks, when it calls <legacyBold>SQLCloseCursor</legacyBold> (in auto-commit mode) or <legacyBold>SQLEndTran</legacyBold> (in manual-commit mode).</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="46762ae5-17dd-4777-968e-58156f470fe1">Concurrency Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9d71e09e-bc68-4c1f-9229-ed2a7be7d324">Optimistic Concurrency</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>