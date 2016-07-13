---
title: SQLRowCount (Cursor Library)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLRowCount (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLRowCount</legacyBold> function in the cursor library. For general information about <legacyBold>SQLRowCount</legacyBold>, see <legacyLink xlink:href="61e00a8a-9b3b-45b9-b397-7fe818822416">SQLRowCount Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>When an application calls <legacyBold>SQLRowCount</legacyBold> with the statement associated with the cursor, the cursor library returns the number of rows of data it has retrieved from the driver.</para>
      <para>When an application calls <legacyBold>SQLRowCount</legacyBold> with the statement associated with a positioned update or delete statement, the cursor library returns the number of rows affected by the statement.</para>
      <para>When an application calls <legacyBold>SQLRowCount</legacyBold> after a <legacyBold>SELECT</legacyBold> statement, the cursor library returns –1.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>