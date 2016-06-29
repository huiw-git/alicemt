---
title: SQLCloseCursor_ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
translation.priority.ht: 
  - en-gb
---
# SQLCloseCursor_ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLCloseCursor</legacyBold> function in the cursor library. For general information about <legacyBold>SQLCloseCursor</legacyBold>, see <legacyLink xlink:href="05b0a054-e28d-4e16-b5b0-07418486b372">SQLCloseCursor Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library does not support calling <legacyBold>SQLCloseCursor</legacyBold> without an open cursor. Attempting this will return SQLSTATE 24000 (Invalid cursor state). Calling <legacyBold>SQLFreeStmt</legacyBold> with an <legacyItalic>Option</legacyItalic> of SQL_CLOSE when no cursor is open is supported by the cursor library.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>