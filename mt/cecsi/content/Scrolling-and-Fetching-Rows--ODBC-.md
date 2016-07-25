---
title: "Scrolling and Fetching Rows (ODBC)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Scrolling and Fetching Rows (ODBC)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When using a scrollable cursor, applications call <legacyBold>SQLFetchScroll</legacyBold> to position the cursor and fetch rows. <legacyBold>SQLFetchScroll</legacyBold> supports relative scrolling (next, prior, and relative <legacyItalic>n</legacyItalic> rows), absolute scrolling (first, last, and row <legacyItalic>n</legacyItalic>), and positioning by bookmark. The <legacyItalic>FetchOrientation</legacyItalic> and <legacyItalic>FetchOffset</legacyItalic> arguments in <legacyBold>SQLFetchScroll</legacyBold> specify which rowset to fetch, as shown in the following diagrams.</para>
    <mediaLink>
      <image xlink:href="5603fad0-1a24-4402-a08e-e0a428e0f83a" />
    </mediaLink>
    <para>
      <embeddedLabel>Fetching Next, Prior, First, and Last Rowsets</embeddedLabel>
    </para>
    <mediaLink>
      <image xlink:href="e9a38387-036a-4d94-8875-14d33bbb2b9e" />
    </mediaLink>
    <para>
      <embeddedLabel>Fetching Absolute, Relative, and Bookmarked Rowsets</embeddedLabel>
    </para>
    <para>
      <legacyBold>SQLFetchScroll</legacyBold> positions the cursor to the specified row and returns the rows in the rowset starting with that row. If the specified rowset overlaps the end of the result set, a partial rowset is returned. If the specified rowset overlaps the start of the result set, the first rowset in the result set is usually returned; for complete details, see the <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink> function description.</para>
    <para>In some cases, the application might want to position the cursor without retrieving any data. For example, it might want to test whether a row exists or just get the bookmark for the row without bringing other data across the network. To do this, it sets the SQL_ATTR_RETRIEVE_DATA statement attribute to SQL_RD_OFF. The variable bound to the bookmark column (if any) is always updated, regardless of the setting of this statement attribute.</para>
    <para>After the rowset has been retrieved, the application can call <legacyBold>SQLSetPos</legacyBold> to position to a particular row in the rowset or refresh rows in the rowset. For more information on using <legacyBold>SQLSetPos</legacyBold>, see <legacyLink xlink:href="e9625b59-06a0-4883-b155-b932ba7528d9">Updating Data with SQLSetPos</legacyLink>.</para>
    <alert class="note">
      <para>Scrolling is supported in ODBC 2.<legacyItalic>x</legacyItalic> drivers by <legacyBold>SQLExtendedFetch</legacyBold>. For more information, see <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink>in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>