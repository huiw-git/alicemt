---
title: SQLGetDescField and SQLGetDescRec (Cursor Library)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetDescField and SQLGetDescRec (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetDescField</legacyBold> and <legacyBold>SQLGetDescRec </legacyBold>functions in the cursor library. For general information about these functions, see <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink> and <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library executes <legacyBold>SQLGetDescRec</legacyBold> to return metadata for bookmark columns. The cursor library executes <legacyBold>SQLGetDescField</legacyBold> to return the same fields returned by <legacyBold>SQLGetDescRec</legacyBold>, which are SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, and SQL_DESC_NULLABLE. For consistency, <legacyBold>SQLGetDescField</legacyBold> also returns SQL_DESC_UNNAMED.</para>
      <para>The cursor library executes <legacyBold>SQLGetDescField</legacyBold> when it is called to return the value of the following fields that are set for binding bookmark columns: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR, and SQL_DESC_LENGTH.</para>
      <para>The cursor library executes <legacyBold>SQLGetDescField</legacyBold> when it is called to return the value of the SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE, or SQL_DESC_ROW_STATUS_PTR field. These fields can be returned for any row, not just the bookmark row.</para>
      <para>If an application calls <legacyBold>SQLGetDescField</legacyBold> to return the value of any field other than those mentioned previously, the cursor library passes the call to the driver.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>