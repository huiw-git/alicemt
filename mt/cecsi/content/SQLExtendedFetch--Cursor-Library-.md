---
title: SQLExtendedFetch (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLExtendedFetch (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLExtendedFetch</legacyBold> function in the cursor library. For general information about <legacyBold>SQLExtendedFetch</legacyBold>, see <legacyLink xlink:href="940b5cf7-581c-4ede-8533-c67d5e9ef488">SQLExtendedFetch Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library implements <legacyBold>SQLExtendedFetch</legacyBold> by repeatedly calling <legacyBold>SQLFetch</legacyBold> in the driver.</para>
      <para>The cursor library supports calling <legacyBold>SQLExtendedFetch</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_BOOKMARK.</para>
      <para>When the cursor library is used, calls to <legacyBold>SQLExtendedFetch</legacyBold> cannot be mixed with calls to either <legacyBold>SQLFetchScroll</legacyBold> or <legacyBold>SQLFetch</legacyBold>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>