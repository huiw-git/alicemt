---
title: Updating Data with SQLSetPos
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Updating Data with SQLSetPos
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications can update or delete any row in the rowset with <legacyBold>SQLSetPos</legacyBold>. Calling <legacyBold>SQLSetPos</legacyBold> is a convenient alternative to constructing and executing an SQL statement. It lets an ODBC driver support positioned updates even when the data source does not support positioned SQL statements. It is part of the paradigm of achieving complete database access by means of function calls.</para>
    <para>         <legacyBold>SQLSetPos</legacyBold> operates on the current rowset and can be used only after a call to <legacyBold>SQLFetchScroll</legacyBold>. The application specifies the number of the row to update, delete, or insert, and the driver retrieves the new data for that row from the rowset buffers. <legacyBold>SQLSetPos</legacyBold> can also be used to designate a specified row as the current row, or to refresh a particular row in the rowset from the data source.</para>
    <para>Rowset size is set by a call to <legacyBold>SQLSetStmtAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> argument of SQL_ATTR_ROW_ARRAY_SIZE. <legacyBold>SQLSetPos</legacyBold> uses a new rowset size, however, only after a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. For example, if the rowset size is changed, <legacyBold>SQLSetPos</legacyBold> is called and then <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> is called, and the call to <legacyBold>SQLSetPos</legacyBold> uses the old rowset size while <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> uses the new rowset size.</para>
    <para>The first row in the rowset is row number 1. The <legacyItalic>RowNumber</legacyItalic> argument in <legacyBold>SQLSetPos</legacyBold> must identify a row in the rowset; that is, its value must be in the range between 1 and the number of rows that were most recently fetched (which may be less than the rowset size). If <legacyItalic>RowNumber</legacyItalic> is 0, the operation applies to every row in the rowset.</para>
    <para>Because most interaction with relational databases is done through SQL, <legacyBold>SQLSetPos</legacyBold> is not widely supported. However, a driver can easily emulate it by constructing and executing an <legacyBold>UPDATE</legacyBold> or <legacyBold>DELETE</legacyBold> statement.</para>
    <para>To determine what operations <legacyBold>SQLSetPos</legacyBold> supports, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 information option (depending on the type of the cursor).</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="d83a8c2a-5aa8-4f19-947c-79a817167ee1">Updating Rows in the Rowset with SQLSetPos</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3117a47d-e179-4f76-89d0-656582f1c9bb">Deleting Rows in the Rowset with SQLSetPos</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>