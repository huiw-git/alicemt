---
title: "SQLFetch (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFetch (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLFetch</legacyBold> function in the cursor library. For general information about <legacyBold>SQLFetch</legacyBold>, see <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>When the cursor library is used, calls to <legacyBold>SQLFetch</legacyBold> cannot be mixed with calls to either <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLExtendedFetch</legacyBold>.</para>
      <para>If <legacyBold>SQLFetch</legacyBold> is called with SQL_ATTR_ROW_ARRAY_SIZE set to a value greater than 1, the cursor library will pass the call to the driver. If the driver is an ODBC 2.<legacyItalic>x</legacyItalic> driver, the rowset size will be ignored and the call to <legacyBold>SQLFetch</legacyBold> will return a single row of data.</para>
      <para>If the cursor library is used with an ODBC 2.<legacyItalic>x</legacyItalic> driver, a bind offset (as defined by the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute) is not used when <legacyBold>SQLFetch</legacyBold> is called.</para>
      <para>When the cursor library is loaded, an application cannot call <legacyBold>SQLFetch</legacyBold> to fetch bookmark columns. The cursor library passes the call to <legacyBold>SQLFetch</legacyBold> through to the driver, but the function calls to enable bookmarks and bind the bookmark column are intercepted by the cursor library.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>