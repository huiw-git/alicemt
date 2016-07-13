---
title: SQLSetPos (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetPos (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetPos</legacyBold> function in the cursor library. For general information about <legacyBold>SQLSetPos</legacyBold>, see <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>.</para>
    <para>The cursor library supports the SQL_POSITION operation only for the <legacyItalic>Operation</legacyItalic> argument in <legacyBold>SQLSetPos</legacyBold>. It supports the SQL_LOCK_NO_CHANGE value only for the <legacyItalic>LockType</legacyItalic> argument.</para>
    <para>If the driver does not support bulk operations, the cursor library returns SQLSTATE HYC00 (Driver not capable) when <legacyBold>SQLSetPos</legacyBold> is called with <legacyItalic>RowNumber</legacyItalic> equal to 0. This driver behavior is not recommended.</para>
    <para>The cursor library does not support the SQL_UPDATE and SQL_DELETE operations in a call to <legacyBold>SQLSetPos</legacyBold>. The cursor library implements a positioned update or delete SQL statement by creating a searched update or delete statement with a WHERE clause that enumerates the values stored in its cache for each bound column. For more information, see <legacyLink xlink:href="2975dd97-48e6-4d0a-a9c7-40759a7d94c8">Processing Positioned Update and Delete Statements</legacyLink>.</para>
    <para>If the driver does not support static cursors, an application working with the cursor library should call <legacyBold>SQLSetPos</legacyBold> only on a rowset fetched by <legacyBold>SQLExtendedFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, not by <legacyBold>SQLFetch</legacyBold>. The cursor library implements <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> by making repeated calls of <legacyBold>SQLFetch</legacyBold> (with a rowset size of 1) in the driver. The cursor library passes calls to <legacyBold>SQLFetch</legacyBold>, on the other hand, through to the driver. If <legacyBold>SQLSetPos</legacyBold> is called on a multirow rowset fetched by <legacyBold>SQLFetch</legacyBold> when the driver does not support static cursors, the call will fail because <legacyBold>SQLSetPos</legacyBold> does not work with forward-only cursors. This will occur even if an application has successfully called <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_STATIC, which the cursor library supports even if the driver does not support static cursors.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>