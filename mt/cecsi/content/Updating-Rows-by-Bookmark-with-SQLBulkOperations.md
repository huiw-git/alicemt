---
title: "Updating Rows by Bookmark with SQLBulkOperations"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Updating Rows by Bookmark with SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When updating a row by bookmark, <legacyBold>SQLBulkOperations</legacyBold> makes the data source update one or more rows of the table. The rows are identified by the bookmark in a bound bookmark column. The row is updated using data in the application buffers for each bound column (except when the value in the length/indicator buffer for a column is SQL_COLUMN_IGNORE). Unbound columns will not be updated. </para>
    <para>To update rows by bookmark with <legacyBold>SQLBulkOperations</legacyBold>, the application:  </para>
    <list class="ordered">
      <listItem>
        <para>Retrieves and caches the bookmarks of all rows to be updated. If there is more than one bookmark and column-wise binding is used, the bookmarks are stored in an array; if there is more than one bookmark and row-wise binding is used, the bookmarks are stored in an array of row structures.</para>
      </listItem>
      <listItem>
        <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of bookmarks and binds the buffer containing the bookmark value, or the array of bookmarks, to column 0.</para>
      </listItem>
      <listItem>
        <para>Places the new data values in the rowset buffers. For information on how to send long data with <legacyBold>SQLBulkOperations</legacyBold>, see <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of each column as necessary. This is the byte length of the data or SQL_NTS for columns bound to string buffers, the byte length of the data for columns bound to binary buffers, and SQL_NULL_DATA for any columns to be set to NULL.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of those columns that are not to be updated to SQL_COLUMN_IGNORE. Although the application can skip this step and resend existing data, this is inefficient and risks sending values to the data source that were truncated when they were read.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLBulkOperations</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_UPDATE_BY_BOOKMARK.</para>
      </listItem>
    </list>
    <para>For every row that is sent to the data source as an update, the application buffers should have valid row data. If the application buffers were filled by fetching, if a row status array has been maintained, and if the status value for a row is SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW, invalid data could inadvertently be sent to the data source.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>