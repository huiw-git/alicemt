---
title: Block Cursors
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Block Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Many applications spend a significant amount of time bringing data across the network. Part of this time is spent actually bringing the data across the network, and part of it is spent on network overhead, such as the call made by the driver to request a row of data. The latter time can be reduced if the application makes efficient use of <legacyItalic>block,</legacyItalic> or <legacyItalic>fat,</legacyItalic> <legacyItalic>cursors,</legacyItalic> which can return more than one row at a time.</para>
    <para>An application always has the option of using a block cursor. On data sources from which only one row at a time can be fetched, block cursors must be simulated in the driver. This can be done by performing multiple single-row fetches. While this is unlikely to provide any performance gains, it opens opportunities for applications. Such applications will then experience performance increases as DBMSs implement block cursors natively and the drivers associated with those DBMSs expose them.</para>
    <para>The rows returned in a single fetch with a block cursor are called the <legacyItalic>rowset</legacyItalic>. It is important not to confuse the rowset with the result set. The result set is maintained at the data source, while the rowset is maintained in application buffers. While the result set is fixed, the rowset is not — it changes position and contents each time a new set of rows is fetched. Just as a single-row cursor such as the traditional SQL forward-only cursor points to a current row, a block cursor points to the rowset, which can be thought of as <legacyItalic>current rows</legacyItalic>.</para>
    <para>To perform operations that operate on a single row when multiple rows have been fetched, the application must first indicate which row is the current row. The current row is required by calls to <legacyBold>SQLGetData</legacyBold> and positioned update and delete statements. When a block cursor first returns a rowset, the current row is the first row of the rowset. To change the current row, the application calls <legacyBold>SQLSetPos</legacyBold> or <legacyBold>SQLBulkOperations </legacyBold>(to update by bookmark). The following illustration shows the relationship of the result set, rowset, current row, rowset cursor, and block cursor. For more information, see <legacyLink xlink:href="2aad7d6b-216e-47e7-b3cb-f95ad096f21a">Using Block Cursors</legacyLink>, later in this section, and <legacyLink xlink:href="0eafba50-02c7-46ca-a439-ef3307b935dc">Positioned Update and Delete Statements</legacyLink> and <legacyLink xlink:href="e9625b59-06a0-4883-b155-b932ba7528d9">Updating Data with SQLSetPos</legacyLink>.</para>
    <mediaLink>
      <image xlink:href="5603fad0-1a24-4402-a08e-e0a428e0f83a" />
    </mediaLink>
    <para>Whether a cursor is a block cursor is independent of whether it is scrollable. For example, most of the work in a report application is spent retrieving and printing rows. Because of this, it will work fastest with a forward-only, block cursor. It uses a forward-only cursor to avoid the expense of a scrollable cursor, and a block cursor to reduce the network traffic.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="231beede-cdfa-4e28-8b10-2760b983250f">Binding Columns for Use with Block Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2aad7d6b-216e-47e7-b3cb-f95ad096f21a">Using Block Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4b69f189-2722-4314-8a02-f4ffecd6dabd">Row Status Array</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>