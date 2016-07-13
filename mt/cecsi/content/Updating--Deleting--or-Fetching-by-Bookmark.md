---
title: Updating, Deleting, or Fetching by Bookmark
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Updating, Deleting, or Fetching by Bookmark
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Bookmarks can be used to identify data to be updated in the result set, deleted from the result set, or fetched from the result set to the rowset buffers. These operations are performed by a call to <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Option</legacyItalic> argument of SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK, or SQL_FETCH_BY_BOOKMARK. The bookmarks used in these operations are stored in column 0 of the rowset buffers. When updating by bookmark, the data that result set columns are updated to is retrieved from the rowset buffers. For more information, see <legacyLink xlink:href="7645a704-341e-4267-adbe-061a9fda225b">Updating Data with SQLBulkOperations</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>