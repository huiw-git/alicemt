---
title: Deleting Rows by Bookmark with SQLBulkOperations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Deleting Rows by Bookmark with SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When deleting a row by bookmark, <legacyBold>SQLBulkOperations</legacyBold> makes the data source delete one or more selected rows of the table. The rows are identified by the bookmark in a bound bookmark column. </para>
    <para>To delete rows by bookmark with <legacyBold>SQLBulkOperations</legacyBold>, the application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Retrieves and caches the bookmarks of all rows to be deleted. If there is more than one bookmark and column-wise binding is used, the bookmarks are stored in an array; if there is more than one bookmark and row-wise binding is used, the bookmarks are stored in an array of row structures.</para>
      </listItem>
      <listItem>
        <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of bookmarks and binds the buffer containing the bookmark value, or the array of bookmarks, to column 0.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLBulkOperations</legacyBold> with <legacyItalic>Operation</legacyItalic> set to SQL_DELETE_BY_BOOKMARK.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>