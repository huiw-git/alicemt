---
title: "Cursors"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application fetches data with a <legacyItalic>cursor</legacyItalic>. A cursor is different from a result set: A result set is the set of rows that matches particular search criteria, whereas a cursor is the software that returns those rows to the application. The name <legacyItalic>cursor,</legacyItalic> as it applies to databases, probably originated from the blinking cursor on a computer terminal. Just as that cursor indicates the current position on the screen and where the typed words will appear next, a cursor on a result set indicates the current position in the result set and what row will be returned next.</para>
    <para>The cursor model in ODBC is based on the cursor model in embedded SQL. One notable difference between these models is the way cursors are opened. In embedded SQL, a cursor must be explicitly declared and opened before it can be used. In ODBC, a cursor is implicitly opened when a statement that creates a result set is executed. When the cursor is opened, it is positioned before the first row of the result set. In both embedded SQL and ODBC, a cursor must be closed after the application has finished using it.</para>
    <para>Different cursors have different characteristics. The most common type of cursor, which is called a <legacyItalic>forward-only cursor,</legacyItalic> can only move forward through the result set. To return to a previous row, the application must close and reopen the cursor and then read rows from the beginning of the result set until it reaches the required row. Forward-only cursors provide a fast mechanism for making a single pass through a result set.</para>
    <para>Forward-only cursors are less useful for screen-based applications, in which the user scrolls backward and forward through the data. Such applications can use a forward-only cursor by reading the result set once, caching the data locally, and performing scrolling themselves. However, this works well only with small amounts of data. A better solution is to use a <legacyItalic>scrollable cursor,</legacyItalic> which provides random access to the result set. Such applications can also increase performance by fetching more than one row of data at a time, using what is called a <legacyItalic>block cursor. </legacyItalic>For more information about block cursors, see <legacyLink xlink:href="2aad7d6b-216e-47e7-b3cb-f95ad096f21a">Using Block Cursors</legacyLink>.</para>
    <para>The forward-only cursor is the default cursor type in ODBC and is discussed in the following sections. For more information about block cursors and scrollable cursors, see <legacyLink xlink:href="1a92b5d8-7c6e-4ce5-8c99-600a387026aa">Block Cursors</legacyLink> and <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>.</para>
    <alert class="important">
      <para>Committing or rolling back a transaction, either by explicitly calling <legacyBold>SQLEndTran</legacyBold> or by operating in auto-commit mode, causes some data sources to close all the cursors on all statements on a connection. For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR attributes in the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>