---
title: SQLBindParameter (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindParameter (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLBindParameter</legacyBold> function in the cursor library. For general information about <legacyBold>SQLBindParameter</legacyBold>, see <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>An application can call <legacyBold>SQLBindParameter</legacyBold> to rebind parameters, as long as the C data type, column size, and decimal digits of the bound column remain the same.</para>
      <para>The cursor library supports setting the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute to use bind offsets. (<legacyBold>SQLBindParameter</legacyBold> does not have to be called for this rebinding to occur.)</para>
      <para>The cursor library supports binding data-at-execution parameters.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>