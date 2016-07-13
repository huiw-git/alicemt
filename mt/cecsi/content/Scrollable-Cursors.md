---
title: Scrollable Cursors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Scrollable Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In modern screen-based applications, the user scrolls backward and forward through the data. For such applications, returning to a previously fetched row is a problem. One possibility is to close and reopen the cursor and then fetch rows until the cursor reaches the required row. Another possibility is to read the result set, cache it locally, and implement scrolling in the application. Both possibilities work well only with small result sets, and the latter possibility is difficult to implement. A better solution is to use a <legacyItalic>scrollable cursor,</legacyItalic> which can move backward and forward in the result set.</para>
    <para>A <legacyItalic>scrollable cursor</legacyItalic> is commonly used in modern screen-based applications in which the user scrolls back and forth through the data. However, applications should use scrollable cursors only when forward-only cursors will not do the job, as scrollable cursors are generally more expensive than forward-only cursors.</para>
    <para>The ability to move backward raises a question not applicable to forward-only cursors: Should a scrollable cursor detect changes made to rows previously fetched? That is, should it detect updated, deleted, and newly inserted rows?</para>
    <para>This question arises because the definition of a result set — the set of rows that matches certain criteria — does not state when rows are checked to see whether they match that criteria, nor does it state whether rows must contain the same data each time they are fetched. The former omission makes it possible for scrollable cursors to detect whether rows have been inserted or deleted, while the latter makes it possible for them to detect updated data.</para>
    <para>The ability to detect changes is sometimes useful, sometimes not. For example, an accounting application needs a cursor that ignores all changes; balancing books is impossible if the cursor shows the latest changes. On the other hand, an airline reservation system needs a cursor that shows the latest changes to the data; without such a cursor, it must continually requery the database to show the most up-to-date flight availability.</para>
    <para>To cover the needs of different applications, ODBC defines four different types of scrollable cursors. These cursors vary both in expense and in their ability to detect changes to the result set. Note that if a scrollable cursor can detect changes to rows, it can only detect them when it attempts to refetch those rows; there is no way for the data source to notify the cursor of changes to the currently fetched rows. Note as well that visibility of changes is also controlled by the transaction isolation level; for more information, see <legacyLink xlink:href="351bfe5c-3b26-4010-9b9c-22e796135f3b">Transaction Isolation</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="dbd32576-0453-4e90-ae45-1a81cee8259d">Scrollable Cursor Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c5d795ba-70b0-420f-a944-b1894061a755">Using Scrollable Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3d0ff48d-fef5-4c01-bb1d-a583e6269b66">Relative and Absolute Scrolling</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1d7cccc5-f847-4321-b240-28570854ee5c">Bookmarks</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>