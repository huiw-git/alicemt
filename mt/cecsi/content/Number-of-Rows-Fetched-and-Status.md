---
title: Number of Rows Fetched and Status
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Number of Rows Fetched and Status
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the SQL_ATTR_ROWS_FETCHED_PTR statement attribute has been set, it specifies a buffer that returns the number of rows fetched by the call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>, and error rows. (This number is a count of all rows that do not have the status SQL_ROW_NO_ROWS.) After a call to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>, the buffer contains the number of rows that were affected by a bulk operation performed by the function. If the SQL_ATTR_ROW_STATUS_PTR statement attribute has been set, <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> returns the <legacyItalic>row status array,</legacyItalic> which provides the status of each returned row. Both of the buffers pointed to by these fields are allocated by the application and populated by the driver. An application must make sure that these pointers remain valid until the cursor is closed.</para>
    <para>Entries in the row status array state whether each row was fetched successfully, whether it was updated, added, or deleted since it was last fetched, and whether an error occurred while fetching the row. If <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> encounters an error while retrieving one row of a multirow rowset, or if <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_FETCH_BY_BOOKMARK encounters an error while performing a bulk fetch, it sets the corresponding value in the row status array to SQL_ROW_ERROR, continues fetching rows, and returns SQL_SUCCESS_WITH_INFO. For more information about error handling and the row status array, see the <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch</legacyLink> and <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll</legacyLink> function descriptions.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>