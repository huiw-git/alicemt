---
title: Rowset Size
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Rowset Size
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Which rowset size to use depends on the application. Screen-based applications commonly follow one of two strategies. The first is to set the rowset size to the number of rows displayed on the screen; if the user resizes the screen, the application changes the rowset size accordingly. The second is to set the rowset size to a larger number, such as 100, which reduces the number of calls to the data source. The application scrolls locally within the rowset when possible and fetches new rows only when it scrolls outside the rowset.</para>
    <para>Other applications, such as reports, tend to set the rowset size to the largest number of rows the application can reasonably handle — with a larger rowset, the network overhead per row is sometimes reduced. Exactly how large a rowset can be depends on the size of each row and the amount of memory available.</para>
    <para>Rowset size is set by a call to <legacyBold>SQLSetStmtAttr </legacyBold>with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_ROW_ARRAY_SIZE. The application can change the rowset size, bind new rowset buffers (by calling <legacyBold>SQLBindCol</legacyBold> or specifying a binding offset) even after rows have been fetched, or both. The implications of changing the rowset size depend on the function:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> use the rowset size at the time of the call to determine how many rows to fetch. However, <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_NEXT increments the cursor based on the rowset of the previous fetch and then fetches a rowset based on the current rowset size.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLSetPos</legacyBold> uses the rowset size that is in effect as of the preceding call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, because <legacyBold>SQLSetPos</legacyBold> operates on a rowset that has already been set. <legacyBold>SQLSetPos</legacyBold> also will pick up the new rowset size if <legacyBold>SQLBulkOperations</legacyBold> has been called after the rowset size was changed.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLBulkOperations</legacyBold> uses the rowset size in effect at the time of the call, because it performs operations on a table independent of any fetched rowset.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>