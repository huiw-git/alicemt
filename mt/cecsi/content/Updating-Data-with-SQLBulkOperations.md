---
title: Updating Data with SQLBulkOperations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
translation.priority.ht: 
  - en-gb
---
# Updating Data with SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications can perform bulk update, delete, fetch, or insertion operations on the underlying table at the data source with a call to <legacyBold>SQLBulkOperations</legacyBold>. Calling <legacyBold>SQLBulkOperations</legacyBold> is a convenient alternative to constructing and executing an SQL statement. It lets an ODBC driver support positioned updates even when the data source does not support positioned SQL statements. It is part of the paradigm of achieving complete database access by means of function calls.</para>
    <para>         <legacyBold>SQLBulkOperations</legacyBold> operates on the current rowset and can be used only after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. The application specifies the rows to update, delete, or refresh by caching their bookmarks. The driver retrieves the new data for rows to be updated, or the new data to be inserted into the underlying table, from the rowset buffers.</para>
    <para>The rowset size to be used by <legacyBold>SQLBulkOperations</legacyBold> is set by a call to <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_ROW_ARRAY_SIZE. Unlike <legacyBold>SQLSetPos</legacyBold>, which uses a new rowset size only after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold> uses the new rowset size after the call to <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
    <para>Because most interaction with relational databases is done through SQL, <legacyBold>SQLBulkOperations</legacyBold> is not widely supported. However, a driver can easily emulate it by constructing and executing an <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, or <legacyBold>INSERT</legacyBold> statement.</para>
    <para>To determine what operations <legacyBold>SQLBulkOperation</legacyBold> supports, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 information option (depending on the type of the cursor).</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6">Updating Rows by Bookmark with SQLBulkOperations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="46139ec9-7095-481a-bf45-20200a2fdc03">Deleting Rows by Bookmark with SQLBulkOperations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ed585ea7-4d56-4df9-8dc3-53ca82382450">Inserting Rows with SQLBulkOperations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0efee2d6-ce94-411e-9976-97ba28b8da37">Fetching Rows with SQLBulkOperations</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>