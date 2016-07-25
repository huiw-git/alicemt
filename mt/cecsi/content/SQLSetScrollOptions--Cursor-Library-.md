---
title: "SQLSetScrollOptions (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetScrollOptions (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetScrollOptions</legacyBold> function in the cursor library. For general information about <legacyBold>SQLSetScrollOptions</legacyBold>, see <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library supports <legacyBold>SQLSetScrollOptions</legacyBold> only for backward compatibility; applications should use the SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, and SQL_ATTR_ROW_ARRAY_SIZE statement attributes instead.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>