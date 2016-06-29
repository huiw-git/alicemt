---
title: SQLFreeStmt (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
translation.priority.ht: 
  - en-gb
---
# SQLFreeStmt (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLFreeStmt</legacyBold> function in the cursor library. For general information about <legacyBold>SQLFreeStmt</legacyBold>, see <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>If an application calls <legacyBold>SQLFreeStmt</legacyBold> with the SQL_UNBIND option after it calls <legacyBold>SQLExtendedFetch</legacyBold>, <legacyBold>SQLFetch</legacyBold>, or <legacyBold>SQLFetchScroll</legacyBold>, the cursor library returns an error. Before it can unbind result set columns, an application must call <legacyBold>SQLCloseCursor</legacyBold> or <legacyBold>SQLFreeStmt</legacyBold> with the SQL_CLOSE option.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>