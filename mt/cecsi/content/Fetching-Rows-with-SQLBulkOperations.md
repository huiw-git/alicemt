---
title: Fetching Rows with SQLBulkOperations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Fetching Rows with SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data can be refetched into a rowset using bookmarks by a call to <legacyBold>SQLBulkOperations. </legacyBold>The rows to be fetched are identified by the bookmarks in a bound bookmark column. Columns with a value of SQL_COLUMN_IGNORE are not fetched.</para>
    <para>To perform bulk fetches with <legacyBold>SQLBulkOperations</legacyBold>, the application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Retrieves and caches the bookmarks of all rows to be updated. If there is more than one bookmark and column-wise binding is used, the bookmarks are stored in an array; if there is more than one bookmark and row-wise binding is used, the bookmarks are stored in an array of row structures.</para>
      </listItem>
      <listItem>
        <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows to fetch and binds the buffer containing the bookmark value, or the array of bookmarks, to column 0.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of each column as necessary. This is the byte length of the data or SQL_NTS for columns bound to string buffers, the byte length of the data for columns bound to binary buffers, and SQL_NULL_DATA for any columns to be set to NULL. The application sets the value in the length/indicator buffer of those columns that are to be set to their default (if one exists) or NULL (if one does not) to SQL_COLUMN_IGNORE.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLBulkOperations</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_FETCH_BY_BOOKMARK.</para>
      </listItem>
    </list>
    <para>There is no need for the application to use the row operation array to prevent the operation to be performed on certain columns. The application selects the rows it wants to fetch by copying only the bookmarks for those rows into the bound bookmark array.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>