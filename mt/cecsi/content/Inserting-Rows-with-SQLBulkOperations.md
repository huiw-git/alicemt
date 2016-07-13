---
title: Inserting Rows with SQLBulkOperations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Inserting Rows with SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Inserting data with <legacyBold>SQLBulkOperations</legacyBold> is similar to updating data with <legacyBold>SQLBulkOperations</legacyBold> because it uses data from the bound application buffers. </para>
    <para>So that each column in the new row has a value, all bound columns with a length/indicator value of SQL_COLUMN_IGNORE and all unbound columns must either accept NULL values or have a default.</para>
    <para>To insert rows with <legacyBold>SQLBulkOperations</legacyBold>, the application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Sets the SQL_ATTR_ROW_ARRAY_SIZE statement attribute to the number of rows to insert and places the new data values in the bound application buffers. For information on how to send long data with <legacyBold>SQLBulkOperations</legacyBold>, see <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer of each column as necessary. This is the byte length of the data or SQL_NTS for columns bound to string buffers, the byte length of the data for columns bound to binary buffers, and SQL_NULL_DATA for any columns to be set to NULL. The application sets the value in the length/indicator buffer of those columns that are to be set to their default (if one exists) or NULL (if one does not) to SQL_COLUMN_IGNORE.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLBulkOperations</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_ADD.</para>
      </listItem>
    </list>
    <para>After <legacyBold>SQLBulkOperations</legacyBold> returns, the current row is unchanged. If the bookmark column (column 0) is bound, <legacyBold>SQLBulkOperations</legacyBold> returns the bookmarks of the inserted rows in the rowset buffer bound to that column.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>