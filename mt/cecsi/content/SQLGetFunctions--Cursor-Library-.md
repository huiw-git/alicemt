---
title: "SQLGetFunctions (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetFunctions (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetFunctions</legacyBold> function in the cursor library. For general information about <legacyBold>SQLGetFunctions</legacyBold>, see <legacyLink xlink:href="0451d2f9-0f4f-46ba-b252-670956a52183">SQLGetFunctions Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>When you call <legacyBold>SQLGetFunctions</legacyBold>, the cursor library returns that it supports <legacyBold>SQLExtendedFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLSetPos</legacyBold>, and <legacyBold>SQLSetScrollOptions</legacyBold>, in addition to the functions supported by the driver.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>