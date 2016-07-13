---
title: Length of Column Data
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Length of Column Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library creates a buffer in the cache for each length/indicator buffer bound to the result set with <legacyBold>SQLBindCol</legacyBold>. It uses the values in these buffers to construct a <legacyBold>WHERE</legacyBold> clause when it emulates positioned update or delete statements. It updates these buffers from the rowset buffers when it fetches data from the data source and when it executes positioned update statements.</para>
  </introduction>
  <section>
    <content>
      <para>If the C type of a data buffer is SQL_C_CHAR or SQL_C_BINARY, and the length/indicator value is SQL_NTS, the string length of the data is put into the length/indicator buffer.</para>
      <alert class="note">
        <para>The cursor library does not update its cache for a column if *<legacyItalic>StrLen_or_IndPtr</legacyItalic> in the corresponding rowset buffer is SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC macro.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>