---
title: "SQLNativeSql (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLNativeSql (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLNativeSql</legacyBold> function in the cursor library. For general information about <legacyBold>SQLNativeSql</legacyBold>, see <legacyLink xlink:href="b8efc247-27ab-4a00-92b6-1400785783fe">SQLNativeSql Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>If the driver supports this function, the cursor library calls <legacyBold>SQLNativeSql</legacyBold> in the driver and passes it the SQL statement. For positioned update, positioned delete, and <legacyBold>SELECT FOR UPDATE</legacyBold> statements, the cursor library modifies the statement before passing it to the driver.</para>
      <alert class="note">
        <para>The cursor library incorrectly returns SQLSTATE 34000 (Invalid cursor name) if the cursor name is invalid in a positioned update or delete statement that is passed in the <legacyItalic>InStatementText</legacyItalic> argument of <legacyBold>SQLNativeSql</legacyBold>. <legacyBold>SQLNativeSql</legacyBold> is not intended to return syntax errors, which are returned only upon statement preparation or execution.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>