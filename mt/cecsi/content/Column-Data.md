---
title: Column Data
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Column Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library creates a buffer in the cache for each data buffer bound to the result set with <legacyBold>SQLBindCol</legacyBold>. It uses the values in these buffers to construct a <legacyBold>WHERE</legacyBold> clause when it emulates a positioned update or delete statement. It updates these buffers from the rowset buffers when it fetches data from the data source and when it executes positioned update statements.</para>
  </introduction>
  <section>
    <content>
      <para>When the cursor library updates its cache from the rowset buffers, it transfers the data according to the C data type specified in <legacyBold>SQLBindCol</legacyBold>. For example, if the C data type of a rowset buffer is SQL_C_SLONG, the cursor library transfers four bytes of data; if it is SQL_C_CHAR and <legacyItalic>BufferLength</legacyItalic> is 10, the cursor library transfers 10 bytes of data. The cursor library does not perform any type checking or conversions on the data it transfers.</para>
      <alert class="note">
        <para>The cursor library does not update its cache for a column if *<legacyItalic>StrLen_or_IndPtr</legacyItalic> in the corresponding rowset buffer is SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC macro.</para>
      </alert>
      <para>When it updates a column, a data source blank-pads fixed-length character data and zero-pads fixed-length binary data as necessary. For example, a data source stores "Smith" in a CHAR(10) column as "Smith     ". The cursor library does not blank-pad or zero-pad data in the rowset buffers when it copies this data to its cache after executing a positioned update statement. Therefore, if an application requires that the values in the cursor library's cache are blank-padded or zero-padded, it must blank-pad or zero-pad the values in the rowset buffers before executing a positioned update statement.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>